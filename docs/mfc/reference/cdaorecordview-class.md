---
title: Класс CDaoRecordView
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: b8c411dbd29316219759351f1f1633b6e57b92e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377146"
---
# <a name="cdaorecordview-class"></a>Класс CDaoRecordView

Представление, которое отображает записи базы данных в элементах управления.

## <a name="syntax"></a>Синтаксис

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>Участники

### <a name="protected-constructors"></a>Защищенные конструкторы

|Имя|Описание|
|----------|-----------------|
|[CDaoRecordView::CDaoRecordView](#cdaorecordview)|Формирует объект `CDaoRecordView`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[CDaoRecordView::IsOnFirstRecord](#isonfirstrecord)|Возвращает ненулевой, если текущая запись является первой записью в связанном наборе записей.|
|[CDaoRecordView::IsOnLastRecord](#isonlastrecord)|Возвращает ненулевой, если текущая запись является последней записью в связанном наборе записей.|
|[CDaoRecordView::OnGetRecordset](#ongetrecordset)|Возвращает указатель объекту класса, полученному `CDaoRecordset`из. ClassWizard переопределяет эту функцию для вас и создает рекорд, если это необходимо.|
|[CDaoRecordView::OnMove](#onmove)|Если текущая запись изменилась, обновит ее в источник еданных, а затем переходит к указанной записи (следующей, предыдущей, первой или последней).|

## <a name="remarks"></a>Remarks

Представление представляет собой представление формы, `CDaoRecordset` непосредственно связанное с объектом. Представление создается из ресурса шаблона диалогов и `CDaoRecordset` отображает поля объекта в элементах управления шаблона диалога. Объект `CDaoRecordView` использует обмен диалоговые данные (DDX) и обмен поля записи DAO (DFX) для автоматизации движения данных между элементами управления по форме и полям рекорда. `CDaoRecordView`также поставляет реализацию по умолчанию для перехода к первой, следующей, предыдущей или последней записи и интерфейсу для обновления записи, наименее рассматриваемой в настоящее время.

> [!NOTE]
> Классы баз данных DAO отличаются от классов баз данных MFC на основе open Database Connectivity (ODBC). Все названия классов баз данных DAO имеют префикс "CDao". Вы все еще можете получить доступ к источникам данных ODBC с классами DAO; классы DAO обычно предлагают превосходные возможности, поскольку они используют движок базы данных Microsoft Jet.

Наиболее распространенным способом создания представления записи является «Мастер приложения». Волшебник приложения создает как класс представления записи, так и связанный с ним класс записей как часть вашего приложения для стартера скелета.

Если вам просто нужна одна форма, подход Мастера приложений проще. ClassWizard позволяет вам принять решение использовать представление записи позже в процессе разработки. Если вы не создаете класс представления записи с помощью Мастера приложения, его можно создать позже с помощью ClassWizard. Использование ClassWizard для создания представления записи и записи отдельно, а затем подключить их является наиболее гибким подходом, поскольку он дает вам больше контроля в названии класса recordset и его . H/. Файлы CPP. Этот подход также позволяет иметь несколько представлений записей на одном и том же классе записей.

Чтобы облегчить переход конечных пользователей от записи к записи в представлении записи, Мастер приложения создает ресурсы меню (и, по желанию, панели инструментов) для перехода к первой, следующей, предыдущей или последней записи. Если вы создаете класс представления записи с ClassWizard, вам нужно создать эти ресурсы самостоятельно с редакторами меню и биткарты.

Для получения информации о реализации по `IsOnFirstRecord` умолчанию для перехода от записи к записи, `IsOnLastRecord` см. и и статьи [С помощью представления записи](../../data/using-a-record-view-mfc-data-access.md), который относится к обоим `CRecordView` и `CDaoRecordView`.

`CDaoRecordView`отслеживает положение пользователя в записи, чтобы представление записи можно обновляло пользовательский интерфейс. Когда пользователь перемещается на один конец набора записей, представление записи отводит объекты пользовательского интерфейса - такие как элементы меню или кнопки панели инструментов - для дальнейшего движения в том же направлении.

Для получения дополнительной информации об объявлении и использовании классов представления записей и [Record Views](../../data/record-views-mfc-data-access.md)записей см. Для получения дополнительной информации о том, как работают представления записей и как их использовать, смотрите статью [«Использование представления записи».](../../data/using-a-record-view-mfc-data-access.md) Все статьи, упомянутые `CRecordView` `CDaoRecordView`выше, относятся к обоим и .

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>Требования

**Заголовок:** afxdao.h

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a>CDaoRecordView::CDaoRecordView

При создании объекта типа, полученного `CDaoRecordView`из, вызов любой формы конструктора для инициализации объекта представления и идентификации ресурса диалога, на котором основано представление.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>Параметры

*lpszTemplateName*<br/>
Содержит строку с нулевым завершением, которая является названием ресурса шаблона диалога.

*nIDTemplate*<br/>
Содержит идентификационный номер ресурса шаблона диалогов.

### <a name="remarks"></a>Remarks

Можно либо определить ресурс по имени (пройти строку в качестве аргумента к конструктору), либо по его идентификатору (пройти неподписанный целый ряд в качестве аргумента). Рекомендуется использовать идентификатор ресурса.

> [!NOTE]
> Ваш производный класс должен поставлять свой собственный конструктор. В конструкторе вашего производного `CDaoRecordView::CDaoRecordView` класса позвоните в конструктор с именем ресурса или идентификатором в качестве аргумента.

`CDaoRecordView::OnInitialUpdate`звонки, `CWnd::UpdateData`которые `CWnd::DoDataExchange`звонят . Этот первоначальный `DoDataExchange` вызов `CDaoRecordView` для подключения элементов управления (косвенно) к `CDaoRecordset` членам данных на местах, созданным ClassWizard. Эти участники данных не могут использоваться до тех пор, пока вы не позвоните в функцию базового класса. `CFormView::OnInitialUpdate`

> [!NOTE]
> Если вы используете ClassWizard, мастер определяет `CDaoRecordView::IDD` значение **enum** в декларации класса и использует его в списке инициализации элемента для конструктора.

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a>CDaoRecordView::IsOnFirstRecord

Вызовите эту функцию участника, чтобы определить, является ли текущая запись первой записью в объекте записи, связанном с этим представлением записи.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>Возвращаемое значение

Nonzero, если текущий рекорд является первым рекордом в рекордном уровне; в противном случае 0.

### <a name="remarks"></a>Remarks

Эта функция полезна для написания собственных реализаций обработчиков обновлений команд по умолчанию, написанных ClassWizard.

Если пользователь переходит к первой записи, фреймворк отстраняет любые объекты пользовательского интерфейса (например, элементы меню или кнопки панели инструментов) для перехода к первой или предыдущей записи.

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a>CDaoRecordView::IsOnLastRecord

Вызовите эту функцию участника, чтобы определить, является ли текущая запись последней записью в объекте записи, связанном с этим представлением записи.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>Возвращаемое значение

Nonzero, если текущий рекорд является последним рекордом в рекорде; в противном случае 0.

### <a name="remarks"></a>Remarks

Эта функция полезна для написания собственных реализаций обработчиков обновлений команд по умолчанию, которые пишет ClassWizard для поддержки пользовательского интерфейса для перехода от записи к записи.

> [!CAUTION]
> Результат этой функции является надежным, за исключением того, что представление не может быть в состоянии обнаружить конец записи до тех пор, пока пользователь не переместится мимо него. Возможно, пользователю придется выйти за пределы последней записи, прежде чем представление записи может сказать, что он должен отключить любые объекты пользовательского интерфейса для перехода к следующей или последней записи. Если пользователь проходит мимо последней записи, а затем возвращается к последней записи (или до нее), представление записи может отслеживать положение пользователя в наборе записей и правильно отскакивать объекты пользовательского интерфейса.

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a>CDaoRecordView::OnGetRecordset

Возвращает указатель на `CDaoRecordset`объект, полученный из полученных в виде записи.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на `CDaoRecordset`объект, полученный в результате получения; в противном случае null указатель.

### <a name="remarks"></a>Remarks

Вы должны переопределить эту функцию участника, чтобы построить или получить объект, установленный записью, и вернуть указатель к нему. Если вы объявляете свой класс представления записи с ClassWizard, мастер записывает переопределение по умолчанию для вас. Реализация ClassWizard по умолчанию возвращает указатель записи, хранящийся в представлении записи, если он существует. Если нет, он конструирует объект записи типа, указанного в ClassWizard, и вызывает его `Open` функцию члена, чтобы открыть таблицу или запустить запрос, а затем возвращает указатель объекту.

Для получения дополнительной информации [Record Views: Using a Record View](../../data/using-a-record-view-mfc-data-access.md)и примеров см.

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a>CDaoRecordView::OnMove

Вызовите эту функцию участника, чтобы переместиться к другой записи в наборе записей и отобразить ее поля в элементах управления представления записи.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>Параметры

*nIDMoveCommand*<br/>
Одно из следующих стандартных значений идентификатора команды:

- ID_RECORD_FIRST Перейти к первой записи в рекорде.

- ID_RECORD_LAST Переместить к последнему рекорду в рекорде.

- ID_RECORD_NEXT Перейти к следующему рекорду в рекорде.

- ID_RECORD_PREV Перейти к предыдущему рекорду в рекорде.

### <a name="return-value"></a>Возвращаемое значение

Nonzero, если ход был успешным; в противном случае 0, если запрос на перемещение был отклонен.

### <a name="remarks"></a>Remarks

Реализация по умолчанию вызывает соответствующую `CDaoRecordset` функцию участника Движения объекта, связанную с представлением записи.

По умолчанию `OnMove` обновляется текущая запись источника данных, если пользователь изменил ее в представлении записи.

Волшебник приложения создает ресурс меню с элементами меню First Record, Last Record, Next Record и Previous Record. При выборе опции Initial Toolbar Мастер приложения также создает панель инструментов с кнопками, соответствующими этим командам.

Если вы пройдите мимо последней записи в рекордном сете, представление записи продолжает отображать последнюю запись. При перемещении назад мимо первой записи представление записи продолжает отображать первую запись.

> [!CAUTION]
> Вызов `OnMove` бросает исключение, если в наборе записей нет записей. Позвоните соответствующей функции `OnUpdateRecordFirst`обработчика обновления пользовательского интерфейса - , `OnUpdateRecordLast` `OnUpdateRecordNext`, или `OnUpdateRecordPrev` - до соответствующей операции перемещения, чтобы определить, есть ли записи.

## <a name="see-also"></a>См. также раздел

[Класс CFormView](../../mfc/reference/cformview-class.md)<br/>
[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset класс](../../mfc/reference/cdaorecordset-class.md)<br/>
[Класс CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)<br/>
[Класс CДао-КуириДеф](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase Класс](../../mfc/reference/cdaodatabase-class.md)<br/>
[Класс CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Класс CFormView](../../mfc/reference/cformview-class.md)
