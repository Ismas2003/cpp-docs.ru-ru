---
title: Сообщения AFX
ms.date: 11/04/2016
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: b4ed86c11d3c5b5f1ce38e3146533109f3a6b00d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363600"
---
# <a name="afx-messages"></a>Сообщения AFX

Эти сообщения используются в МФЦ.

## <a name="messages"></a>Сообщения

В следующей таблице перечислены сообщения, используемые в библиотеке MFC:

||||||
|-|-|-|-|-|
|Сообщение|Описание|(в) *wParam*|*lParam* (Все параметры являются «в» если не указано иное.)|Возвращаемое значение|
|AFX_WM_ACCGETOBJECT|Не используется.|Не используется.|Не применяется|Не применяется|
|AFX_WM_ACCGETSTATE|Используется для поддержки доступности. Отправить это `CMFCPopupMenu` сообщение `CMFCRibbonPanelMenu` или получить состояние текущего элемента.|Индекс элемента, который может быть кнопкой меню или сепаратором.|Не используется.|Состояние элемента. Это -1, если индекс недействителен, 0, если кнопка меню не имеет специальных атрибутов. В противном случае это сочетание следующих флагов:<br /><br /> TBBS_DISABLED - элемент отключен<br /><br /> TBBS_CHECKED - элемент проверяется<br /><br /> TBBS_BUTTON - элемент является стандартной кнопкой<br /><br /> TBBS_PRESSED — нажатие кнопки<br /><br /> TBBS_INDETERMINATE - неопределенное состояние<br /><br /> TBBS_SEPARATOR - вместо кнопки меню, этот элемент формирует разделение между другими пунктами меню|
|AFX_WM_CHANGE_ACTIVE_TAB|Платформа отправляет это сообщение на изменяемый элемент управления панелью управления. Обработайте это сообщение `CMFCTabCtrl` для получения уведомлений от объектов, когда пользователь изменяет активную вкладку.|Индекс вкладки.|Не используется.|Ненулевой.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Платформа отправляет это сообщение родительскому `CMFCShellListCtrl` типу, когда пользователь изменил текущую папку.|Не используется.|Не используется.|Не используется.|
|AFX_WM_CHANGEVISUALMANAGER|Платформа отправляет это сообщение во все окна кадра, когда пользователь изменяет текущий визуальный менеджер. В ответ на это сообщение окно кадра пересчитывает область и по мере необходимости настраивает другие параметры. Вы можете обработать сообщение AFX_WM_CHANGEVISUALMANAGER в приложении, если вам необходимо уведомлять об этом событии. Вы должны вызвать обработчик базового класса ()`OnChangeVisualManager`для обеспечения внутренней обработки этого события.|Не используется.|Не используется.|Не используется.|
|AFX_WM_CHANGING_ACTIVE_TAB|Отправлено родительскому `CMFCTabCtrl` объекту.  Обработайте это сообщение, если `CMFCTabCtrl` вы хотите получать уведомления от объектов, когда пользователь сбрасывает вкладку.|Индекс активируемой вкладки.|Не используется.|Ненулевой.|
|AFX_WM_CHECKEMPTYMINIFRAME|Только для внутреннего использования.|Не применяется|Не применяется|Не применяется|
|AFX_WM_CREATETOOLBAR|Отправлено `CMFCToolBarsListPropertyPage` с момента, когда пользователь создает новую панель инструментов во время процесса настройки. Вы можете обработать это сообщение, чтобы мгновенно настроить пользовательский объект CMFCToolBar. Если вы обрабатываете это сообщение и создаете свою собственную панель инструментов, опустите вызов обработчику по умолчанию.|Не используется.|Указатель на строку, содержащую название панели инструментов.|Указатель на недавно созданную панель инструментов. NULL указывает, что создание панели инструментов было отменено.|
|AFX_WM_CUSTOMIZEHELP|Отправлено в окно основной кадр `CMFCToolbarCustomize Dialog` из листа свойств настройки, когда пользователь нажимает кнопку **справки** или клавишу F1.|Определяет активную страницу листа свойств настройки.|Указатель на объект `CMFCToolbarCustomize Dialog`.|Ноль.|
|AFX_WM_CUSTOMIZETOOLBAR|Отправляет `CMFCToolbarCustomize Dialog` это сообщение, чтобы уведомить родительский кадр о том, что пользователь создает новую панель инструментов.|TRUE, когда началась настройка, FALSE, когда настройка закончена.|Не используется.|Ноль.|
|AFX_WM_DELETETOOLBAR|Отправлено в окно основной кадр, когда пользователь собирается удалить панель инструментов в режиме настройки.<br /><br /> Обработайте это сообщение, чтобы принять дополнительные действия, когда пользователь удаляет панель инструментов в режиме настройки. Вы также должны вызвать`OnToolbarDelete`обработчик по умолчанию (), который удаляет панель инструментов. Обработчик по умолчанию возвращает значение, которое указывает, возможно ли удалить панель инструментов.|Не используется.|Указатель на `CMFCToolBar` объект, который будет удален.|Nonzero, если панель инструментов не может быть удалена; в противном случае 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`отправляет это сообщение в основное окно кадра для получения цветов документа.|Не используется.|(в, вне) Указатель на `CList<COLORREF, COLORREF>` объект.|Ноль.|
|AFX_WM_GETDRAGBOUNDS|Только для внутреннего использования.|Не применяется|Не применяется|Не применяется|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Отправлено в окно основной кадр, когда пользователь выделяет элемент списка лент.|Индекс выделенного элемента|Указатель на`CMFCBaseRibbonElement`|Не используется.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Отправлено родительскому `CMFCShellListCtrl` `CMFCShellTreeCtrl` элементу или управлению, когда пользователь заканчивает выполнение команды оболочки.|Идентификатор команды, выполненный пользователем|Не используется.|Если приложение обрабатывает это сообщение, оно должно вернуть ноль.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Платформа отправляет это сообщение родителям ленты перед отображением всплывающее меню. Вы можете обработать это сообщение и изменить всплывающее меню в любое время.|Не используется.|Указатель на`CMFCBaseRibbonElement`|Не используется.|
|AFX_WM_ON_CANCELTABMOVE|Только для внутреннего использования.|Не применяется|Не применяется||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Фрейм отправляет это сообщение в основной кадр, когда пользователь меняет активную категорию Управления лентой.|Не используется.|Указатель на `CMFCRibbonBar` категорию которых изменился.|Не используется.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Платформа отправляет это сообщение, чтобы `CMFCDesktopAlertWnd` уведомить владельца о том, что окно вот-вот будет закрыто.|Не используется.|Указатель на `CMFCDesktopAlertWnd` возражение.|Не используется.|
|AFX_WM_ON_DRAGCOMPLETE|Только для внутреннего использования.|Не применяется|Не применяется|Не применяется|
|AFX_WM_ON_GET_TAB_TOOLTIP|Отправка в окно основной кадра, когда окно вкладки собирается отображать набор инструментов для вкладки, если включены пользовательские наборы инструментов.|Не используется.|Указатель на `CMFCTabToolTipInfo` структуру.|Не используется.|
|AFX_WM_ON_HSCROLL|Отправлено в изменяемый контрольный элемент. Обработайте это сообщение `CMFCTabCtrl` для получения уведомлений от объектов, когда событие прокрутки происходит в горизонтальном горизонтальном прокрутке вкладки.|Слово с низким заказом определяет значение панели прокрутки, которое указывает запрос на прокрутку пользователя.  Дополнительные сведения см. в приведенной ниже таблице.|Не используется.|Ненулевой.|
|AFX_WM_ON_MOVE_TAB|Отправлено родительскому окну вкладок, когда пользователь перетаскивает вкладку в новое положение.|Индекс вкладки с нулевым уровнем в исходном положении.|(ваут) Индекс вкладки на нулевой основе в новом положении.|Ноль.|
|AFX_WM_ON_MOVETABCOMPLETE|Только для внутреннего использования.|Не применяется|Не применяется|Не применяется|
|AFX_WM_ON_MOVETOTABGROUP|Отправка в окно основной кадра, когда пользователь перемещает окно ребенка MDI из одной группы вкладок в другую.|Ручка в окне`CMFCTabCtrl`вкладок (), из которого удалено детское окно MDI.|(ваут) Ручка в окно`CMFCTabCtrl`вкладок (), в которое было вставлено детское окно MDI.|Не обрабатывается.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Отправлено родителям, `CDockablePane` когда пользователь нажимает кнопку **«Закрыть»** на заголовок панели управления.|Не используется.|Указатель на док-станционное стекло, на котором пользователь нажал кнопку **"Закрыть".**|TRUE, если панель не может быть закрыта; в противном случае FALSE.|
|AFX_WM_ON_RENAME_TAB|Отправлено родительскому окну вкладок после того, как пользователь переименовал отстеченную вкладку.|Индекс с нулевым уровнем переименованной вкладки.|(ваут) Указатель на строку, содержащую новое имя вкладки.|Nonzero, если приложение обрабатывает это сообщение; фреймворк будет `CMFCBaseTabCtrl::SetTabLabel`подавлять вызов .  Если ноль возвращается, то `CMFCBaseTabCtrl::SetTabLabel` вызывается фреймворцом.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Отправлено в родительский кадр, когда пользователь начинает настройку. Обработайте это сообщение, если вы хотите отобразить свой собственный диалоговый ящик настройки.|Не используется.|Указатель на ребератор управления, которые будут настроены.|Nonzero, если приложение обрабатывает это сообщение и отображает свое собственное поле диалога настройки. Если приложение возвращается с нулем, в фреймворке будет отображаться встроенная коробка диалога настройки.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Только для внутреннего использования.|Не применяется|Не применяется|Не применяется|
|AFX_WM_POSTSETPREVIEWFRAME|Отправлено для уведомления основной кадра о том, что пользователь изменил режим предварительного просмотра печати|TRUE указывает на то, что режим предварительного просмотра печати установлен. FALSE указывает на то, что режим предварительного просмотра печати выключен.|Не используется.|Не используется.|
|AFX_WM_PROPERTY_CHANGED|Отправлено владельцу управления сеткой`CMFCPropertyGridCtrl`свойств () при изменении значения выбранного свойства.|Идентификатор управления списком свойств.|Указатель на свойство`CMFCPropertyGridProperty`(), которое изменилось.|Не используется.|
|AFX_WM_RESETCONTEXTMENU|Отправлено в окно основной кадра, когда пользователь сбрасывает меню контекста во время настройки.|Идентификатор ресурса меню контекста.|Указатель на текущее меню `CMFCPopupMenu`контекста, .|Не используется.|
|AFX_WM_RESETKEYBOARD|Фрейм отправляет это сообщение в окно основного кадра, когда пользователь сбрасывает все ускорители клавиатуры во время настройки.|Не используется.|Не используется.|Не используется.|
|AFX_WM_RESETMENU|Платформа отправляет это сообщение владельцу меню (окно кадра), когда пользователь сбрасывает меню кадра приложения во время настройки|Идентификатор ресурса меню.|Не используется.|Не используется.|
|AFX_WM_RESETPROMPT|Платформа отправляет это сообщение, когда пользователь сбрасывает панель инструментов из панели инструментов, настраивает диалоговое окно. Обработчик по умолчанию отображает окно сообщений, в котором задается вопрос о том, хочет ли пользователь сбросить панель инструментов.|Не используется.|Не используется.|Не используется.|
|AFX_WM_RESETTOOLBAR|Объект `CMFCToolBar` отправляет это сообщение, когда панель инструментов восстанавливается в исходное состояние, т.е. загружается из ресурсов. Обработайте это сообщение, чтобы восстановить кнопки `CMFCToolbarButton`панели инструментов, классы которых являются производными от . Для получения дополнительной информации см. `CMFCToolbarComboBoxButton`.|Идентификатор ресурса панели инструментов, состояние которой было восстановлено.|Не используется.|Ноль.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`объект отправляет это сообщение своему владельцу, когда пользователь нажимает кнопку обычного меню. Обработайте это сообщение `CMFCToolbarMenuButton` каждый раз, когда вы используете для отображения всплывающее меню, когда пользователь нажимает кнопку.|Идентификатор команды кнопки, отправляющий сообщение.|Координаты экрана курсора. Слово низкого порядка определяет X-координацию. Слово высокого порядка определяет y-координацию.|Не используется.|
|AFX_WM_TOOLBARMENU|Отправляется в окно основной кадр, когда пользователь выпускает нужную кнопку мыши, в то время как указатель мыши находится в клиентской или неклиентской области панели.|Не используется.|Координаты экрана указателя мыши. Слово низкого порядка определяет X-координацию. Слово высокого порядка определяет y-координацию.|Ноль, если приложение обрабатывает это сообщение; в противном случае, ненулевой.|
|AFX_WM_UPDATETOOLTIPS|Отправка всем владельцам наборов инструментов, чтобы указать, что их элементы управления должны быть воссозданы.|Тип управления, который должен обрабатывать это сообщение. Позже в этой теме можно ознакомиться в таблице этой темы.|Не используется.|Не используется.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`отправляет это сообщение в родительский кадр, когда пользователь нажимает кнопку **справки** или входит в режим справки, нажав кнопку подписи **справки** или клавишу F1.|Не используется.|Указатель на экземпляр `CMFCWindowsManagerDialog`.|Не используется.|

В следующей таблице показаны значения для низкого слова параметра *lParam* метода AFX_WM_HSCROLL:

|||
|-|-|
|Значение|Значение|
|SB_ENDSCROLL|Пользователь завершает свиток.|
|SB_LEFT|Пользователь прокручивает влево.|
|SB_RIGHT|Пользователь прокручивает в правом нижнем.|
|SB_LINELEFT|Пользователь прокручивает, оставленные одной единицей.|
|SB_LINERIGHT|Пользователь прокручивает вправо на одну единицу.|
|SB_PAGELEFT|Пользователь прокручивает оставленные шириной окна.|
|SB_PAGERIGHT|Пользователь прокручивает вправо по ширине окна.|
|SB_THUMBPOSITION|Пользователь перетащил окно прокрутки (большой палец) и выпустил кнопку мыши. Слово высокого порядка указывает на положение окна прокрутки в конце операции перетаскивания.|
|SB_THUMBTRACK|Пользователь перетаскивает полосу прокрутки. Сообщение AFX_WM_ON_HSCROLL отправляется повторно с этим значением до тех пор, пока пользователь не выпустит кнопку мыши. Слово высокого порядка указывает на положение, в которое перетащилась коробка прокрутки.|

> [!NOTE]
> Слово высокого порядка параметра *lParam* определяет текущее положение окна прокрутки, если слово низкого порядка является SB_THUMBPOSITION или SB_THUMBTRACK; в противном случае это слово не используется.

В следующей таблице перечислены значения флага для параметра *lParam* AFX_WM_UPDATETOOLTIPS сообщения:

|||
|-|-|
|Флаг|Значение|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xffff|

## <a name="see-also"></a>См. также раздел

[Макросы и глобальные объекты](../../mfc/reference/mfc-macros-and-globals.md)
