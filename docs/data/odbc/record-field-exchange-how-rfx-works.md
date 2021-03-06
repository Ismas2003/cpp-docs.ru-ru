---
title: 'Обмен данными с полями записей: Принцип работы RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 903acf4f55fb2708f4998a2babf3f143c895429b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367176"
---
# <a name="record-field-exchange-how-rfx-works"></a>Обмен данными с полями записей: Принцип работы RFX

Эта тема объясняет процесс RFX. Это передовая тема покрытия:

- [RFX и рекорд](#_core_rfx_and_the_recordset)

- [Процесс RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
> Этот раздел относится к классам, производным от `CRecordset`, в которых пакетное получение строк не реализовано. Если вы используете пакетное получение строк, реализуется пакетный обмен полями записей (Bulk RFX). Bulk RFX аналогичен RFX. Чтобы понять различия, [см.](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX и рекорд

Элементы полевых данных объекта записи, вместе взятые, представляют собой буфер редактида, вмещаещий выбранные столбцы одной записи. Когда набор записей впервые открыт и собирается прочитать первую запись, RFX связывает (ассоциирует) каждый выбранный столбец с адресом соответствующего члена данных поля. Когда запись обновляет запись, RFX вызывает функции ODBC API, чтобы отправить драйверу заявление S'L **UPDATE** или **INSERT.** RFX использует свои знания о членах полевых данных для определения столбцов для записи.

На определенных этапах фреймворк резервное копирование буфера отодвилость, чтобы при необходимости восстановить его содержимое. RFX резервирует буфер редактирования перед добавлением новой записи и перед редактированием существующей записи. Он восстанавливает буфер отобрачения в некоторых `AddNew`случаях, например, после следующего `Update` вызова. Буфер изменения не восстанавливается, если вы откажетесь от недавно измененного `Update`буфера изменения, например, перейдя на другую запись перед вызовом.

Помимо обмена данными между источником данных и членами полевых данных, RFX управляет параметрами связывания. При открытии набора данных любые параметры, связанные с порядком "?" в `CRecordset::Open` отчете S'L, который конструируется. Для получения дополнительной информации [см.](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

Переопределение класса записей `DoFieldExchange` выполняет всю работу, перемещая данные в обоих направлениях. Как и обмен диалоговыми данными (DDX), RFX нуждается в информации о членах данных вашего класса. Мастер предоставляет необходимую информацию, написав для `DoFieldExchange` вас конкретную реализацию, основанную на именах членов данных и типах данных, указанных в мастере.

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Процесс обмена полевыми полями

В этом разделе описывается последовательность событий RFX по мере открытия объекта записи и добавления, обновления и удаления записей. Таблица [Последовательность операций RFX Во время открытия Recordset](#_core_sequence_of_rfx_operations_during_recordset_open) и [таблица Последовательность операций RFX Во время прокрутки](#_core_sequence_of_rfx_operations_during_scrolling) в этой теме показывают процесс, как RFX обрабатывает `Move` команду в наборе записей и как RFX управляет обновлением. Во время этих процессов [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) вызывается для выполнения различных операций. Член `m_nOperation` данных объекта [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) определяет, какая операция запрашивается. Вы можете найти полезным для чтения [Recordset: Как записи Выберите записи (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) и [Recordset: Как записи обновления записей (ODBC),](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) прежде чем читать этот материал.

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX: Первоначальная связывание столбцов и параметров

Следующие действия RFX возникают в указанном порядке при вызове функции [открытого](../../mfc/reference/crecordset-class.md#open) члена объекта записи:

- Если в наборе данных параметров `DoFieldExchange` есть параметры, то фреймворк требует привязать параметры к заполнителям параметров в строке оператора записи в s-L. Для каждого заполнителя, найденного в выписке **SELECT,** используется зависимое от типа данных представление о значении параметра. Это происходит после того, как заявление S'L подготовлено, но до того, как оно будет выполнено. Для получения информации о `::SQLPrepare` подготовке оператора, см. *Programmer's Reference*

- Платформа вызывает `DoFieldExchange` второй раз, чтобы связать значения выбранных столбцов с соответствующими членами данных в наборе записей. Это устанавливает объект записи в качестве буфера для отправления, содержащего столбцы первой записи.

- Запись выполняет выписку S'L, а источник данных выбирает первую запись. Столбцы записи загружаются в полевые данные записи.

В следующей таблице показана последовательность операций RFX при открытии набора записей.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Последовательность операций RFX во время открытого уровня recordset

|Операция|Операция DoFieldExchange|Операция базы данных/СЗЛ|
|--------------------|-------------------------------|-----------------------------|
|1. Открытый рекорд.|||
||2. Создайте выписку по S'L.||
|||3. Отправить S'L.|
||4. Связать членов параметров параметров.||
||5. Привязание полевых данных к столбиям.||
|||6. ODBC выполняет ход и заполняет данные.|
||7. Исправьте данные для СЗ.||

Записи используют подготовленное выполнение ODBC, чтобы обеспечить быструю защелку с той же выпиской S'L. Более подробную информацию о подготовленном исполнении можно узнать *в* библиотеке MSDN.

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: Прокрутка

При прокрутке из одной записи в другую фреймворк требует `DoFieldExchange` заменить значения, ранее хранимые в полях, значениями для новой записи.

В следующей таблице показана последовательность операций RFX, когда пользователь переходит от записи к записи.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Последовательность операций RFX во время прокрутки

|Операция|Операция DoFieldExchange|Операция базы данных/СЗЛ|
|--------------------|-------------------------------|-----------------------------|
|1. `MoveNext` Вызов или одна из других функций Move.|||
|||2. ODBC делает ход и заполняет данные.|
||3. Исправьте данные для СЗ.||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Добавление новых записей и редактирование существующих записей

Если вы добавляете новую запись, то запись работает как буфер для отодействия для создания содержимого новой записи. Как и в вопросе добавления записей, редактирование записей предполагает изменение значений полевых данных регистраторов. С точки зрения RFX, последовательность заключается в следующем:

1. Вызов функции [AddNew](../../mfc/reference/crecordset-class.md#addnew) или [Edit-функции](../../mfc/reference/crecordset-class.md#edit) записи записи приводит к тому, что RFX хранит текущий буфер отсеивания, чтобы он мог быть восстановлен позже.

1. `AddNew`или `Edit` готовит поля в буфере отсеивок, чтобы RFX мог обнаружить измененные члены данных поля.

   Поскольку новая запись не имеет предыдущих значений для сравнения новых, `AddNew` значение каждого члена данных поля устанавливается PSEUDO_NULL значением. Позже, при `Update`вызове, RFX сравнивает значение каждого участника данных с значением PSEUDO_NULL. Если есть разница, член данных установлен. (PSEUDO_NULL не то же самое, что столбец записи с истинным значением Null, ни один из них не то же самое, что и C'NULL.)

   В `Update` отличие `AddNew`от `Update` вызова `Edit` для, вызов для сравнения обновленных значений с ранее сохраненными значениями, а не с использованием PSEUDO_NULL. Разница в `AddNew` том, что не имеет ранее хранимых значений для сравнения.

1. Вы непосредственно устанавливаете значения членов полевых данных, значения которых вы хотите отсеивать или которые вы хотите заполнить для новой записи. Это может `SetFieldNull`включать вызов .

1. Ваш призыв [к обновлению](../../mfc/reference/crecordset-class.md#update) проверок для измененных членов полевых данных, описанный в шаге 2 (см. [таблицу Последовательность операций RFX во время прокрутки).](#_core_sequence_of_rfx_operations_during_scrolling) Если ни одна `Update` из них не изменилась, возвращает 0. Если некоторые участники полевых данных изменились, `Update` подготовьте и выполняйте заявление S'L **INSERT,** содержащее значения для всех обновленных полей в записи.

1. `AddNew`Для, `Update` заключает путем восстанавливать ранее сохраненные значения записи, которая была текущей до `AddNew` вызова. Для `Edit`, новые, отредактированные значения остаются на месте.

В следующей таблице показана последовательность операций RFX при добавлении новой записи или отображаются существующие записи.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Последовательность операций RFX во время Добавления И Отсрочение

|Операция|Операция DoFieldExchange|Операция базы данных/СЗЛ|
|--------------------|-------------------------------|-----------------------------|
|1. `AddNew` Звоните или `Edit`.|||
||2. Резервное копирование буфера отсеиваемого средства.||
||3. `AddNew`Для , отметьте полевых членов данных как "чистые" и Null.||
|4. Назначать значения для записи полевых данных.|||
|5. `Update`Звоните .|||
||6. Проверьте наличие измененных полей.||
||7. Создайте заявление `AddNew` s'L `Edit` **INSERT** для или **ОБНОВЛЕНИЕ** заявление для .||
|||8. Отправить S'L.|
||9. `AddNew`Для, восстановить буфер отодвилость к его резервного содержимого. Для, `Edit`удалить резервную часть.||

### <a name="rfx-deleting-existing-records"></a>RFX: Удаляние существующих записей

При удалении записи RFX устанавливает все поля в КАЧЕСТВЕ напоминания об удалении записи и ее удалении. Вам не нужна другая информация о последовательности RFX.

## <a name="see-also"></a>См. также раздел

[Рекордная полевая биржа (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Потребление MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Макросы, глобальные функции и глобальные переменные](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Класс CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
