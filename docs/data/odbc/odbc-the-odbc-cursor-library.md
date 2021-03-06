---
title: ODBC. Библиотека курсоров ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- cursor library [ODBC]
- snapshots, support in ODBC
- timestamps, ODBC timestamp columns
- ODBC cursor library [ODBC]
- static cursors
- ODBC drivers, Level 1
- ODBC drivers, cursor support
- positioned updates
- cursors, ODBC cursor library
- Level 1 ODBC drivers
- cursor library [ODBC], snapshots
- ODBC, timestamp
- positioning cursors
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
ms.openlocfilehash: 13640dd2a8593057bef708a45dfc8471ba212563
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367177"
---
# <a name="odbc-the-odbc-cursor-library"></a>ODBC. Библиотека курсоров ODBC

Эта тема описывает библиотеку ODBC Cursor и объясняет, как ее использовать. Дополнительные сведения см. в разделе:

- [Библиотека Курсора и 1-й уровень водителей ODBC](#_core_the_cursor_library_and_level_1_odbc_drivers)

- [Позиционированные обновления и столбцы timestamp](#_core_positioned_updates_and_timestamp_columns)

- [Использование библиотеки Курсора](#_core_using_the_cursor_library)

Библиотека ODBC Cursor — это библиотека динамических ссылок (DLL), которая находится между менеджером драйверов ODBC и водителем. С точки зрения ODBC, водитель поддерживает курсор, чтобы отслеживать свое положение в рекорде. Курсор отмечает позицию в наборе рекордов, к которому вы уже прокрутили - текущую запись.

## <a name="cursor-library-and-level-1-odbc-drivers"></a><a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a>Библиотека Курсора и 1-й уровень водителей ODBC

Библиотека ODBC Cursor предоставляет водителям 1-го уровня следующие новые возможности:

- Вперед и назад прокрутки. Драйверам уровня 2 не нужна библиотека курсора, поскольку они уже прокрутки.

- Поддержка моментальных снимков. Библиотека курсора управляет буфером, содержащим записи снимка. Этот буфер отражает удаления и изменения программы в записи, но не дополнения, удаления или изменения других пользователей. Таким образом, снимок является только ток, как буфер библиотеки курсора. Буфер также не отражает ваши собственные дополнения, пока вы не позвоните. `Requery` Dynasets не используют библиотеку курсоров.

Библиотека курсора дает снимки (статические курсоры), даже если они обычно не поддерживаются вашим водителем. Если драйвер уже поддерживает статические курсоры, вам не нужно загружать библиотеку курсора, чтобы получить поддержку моментального снимка. Если вы используете библиотеку курсоров, вы можете использовать только снимки и только вперед записи. Если ваш драйвер поддерживает dynasets (KEYSET_DRIVEN курсоры) и вы хотите использовать их, вы не должны использовать библиотеку курсора. Если вы хотите использовать как снимки, так и динасеты, вы должны основывать их на двух разных `CDatabase` объектах (два разных соединения), если драйвер не поддерживает оба.

## <a name="positioned-updates-and-timestamp-columns"></a><a name="_core_positioned_updates_and_timestamp_columns"></a>Позиционированные обновления и столбцы timestamp

> [!NOTE]
> Источники данных ODBC доступны через классы MFC ODBC, как описано в этой теме, или через классы MFC Data Access Object (DAO).

> [!NOTE]
> Если ваш драйвер `SQLSetPos`ODBC поддерживает, который MFC использует, если таков, эта тема не относится к вам.

Большинство драйверов уровня 1 не поддерживают позиционные обновления. Такие драйверы полагаются на библиотеку курсоров для эмуляции возможностей драйверов уровня 2 в этом отношении. Библиотека курсора эмулирует позиционную поддержку обновления, выполняя поиск обновления на неизменных полях.

В некоторых случаях набор записей может содержать столбец метки времени в качестве одного из этих неизменных полей. Две проблемы возникают при использовании записей MFC со таблицами, содержащими столбцы меток времени.

Первый выпуск касается обновляемых моментальных снимков в таблицах с столбцов метки времени. Если таблица, к которой привязан моментальный снимок, `Requery` содержит `Edit` столбец метки времени, следует позвонить после звонка и: `Update` В противном случае вы не сможете снова отсеить одну и ту же запись. При `Edit` вызове, `Update`а затем запись записывается в источник данных и столбец метки времени обновляется. Если вы не `Requery`вызываете, значение метки времени для записи в моментальном снимке больше не совпадает с соответствующей метки времени на источнике данных. При повторном обновлении записи источник данных может запретить обновление из-за несоответствия.

Второй вопрос касается ограничений [cTime](../../atl-mfc-shared/reference/ctime-class.md) класса `RFX_Date` при использовании с функцией передачи информации о времени и дате в таблицу или из нее. Обработка `CTime` объекта накладывает некоторые накладные расходы в виде дополнительной промежуточной обработки во время передачи данных. Диапазон дат `CTime` объектов также может быть слишком ограниченным для некоторых приложений. Новая версия функции `RFX_Date` принимает TIMESTAMP_STRUCT *TIMESTAMP_STRUCT* параметр ODBC вместо `CTime` объекта. Для получения дополнительной `RFX_Date` информации, *MFC Reference* [см.](../../mfc/reference/mfc-macros-and-globals.md)

## <a name="using-the-cursor-library"></a><a name="_core_using_the_cursor_library"></a>Использование библиотеки Курсора

При подключении к источнику данных, позвонив в [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) или [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) - можно указать, следует ли использовать библиотеку курсора для источника данных. Если вы будете создавать снимки на этом `CDatabase::useCursorLib` источнике `dwOptions` данных, укажите опцию в параметре `OpenEx` или укажите TRUE для параметра *bUseCursorLib* (значение `Open` по умолчанию является правдой). Если ваш драйвер ODBC поддерживает dynasets и вы хотите открыть динасеты на источнике данных, не используйте библиотеку курсоров (он маскирует некоторые функции драйвера, необходимые для динасетов). В этом случае не `CDatabase::useCursorLib` `OpenEx` укажите и не укажите FALSE для `Open`параметра *bUseCursorLib* в .

## <a name="see-also"></a>См. также раздел

[Основы ODBC](../../data/odbc/odbc-basics.md)
