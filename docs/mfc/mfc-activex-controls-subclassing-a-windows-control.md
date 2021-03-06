---
title: Элементы управления ActiveX в MFC. Создание подкласса элемента управления Windows
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: ccebbad22be92b84fa2fd84434f788484d332cce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375999"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Элементы управления ActiveX в MFC. Создание подкласса элемента управления Windows

В этой статье описывается процесс подкласса общего элемента управления Windows для создания элемента управления ActiveX. Подклассирование существующего элемента управления Windows — это быстрый способ разработки управления ActiveX. Новый элемент управления будет иметь возможности подклассовой управления Windows, такие как живопись и реагирование на клики мыши. MFC ActiveX управления образцом [BUTTON](../overview/visual-cpp-samples.md) является примером подкласса управления Windows.

>[!IMPORTANT]
> ActiveX является устаревшей технологией, которая не должна использоваться для новых разработок. Для получения дополнительной информации о современных технологиях, которые заменяли ActiveX, [см.](activex-controls.md)

Чтобы подклассифицировать управление Windows, выполните следующие задачи:

- [Переопределить функции членов IsSubclassedControl и PreCreateWindow COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Изменение функции члена OnDraw](#_core_modifying_the_ondraw_member_function)

- [Обработка любых сообщений управления ActiveX (OCM), отраженных в элементе управления](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Большая часть этой работы выполняется для вас мастером управления ActiveX, если вы выбираете элемент управления, который будет подклассен, используя список выпадающих окон **Класса Select Parent** на странице **«Настройки управления».**

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Переопределение IsSubclassedControl и PreCreateWindow

Чтобы `PreCreateWindow` переопределить `IsSubclassedControl`и добавить следующие строки кода в **защищенный** раздел декларации класса управления:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

В файле реализации элемента управления (. CPP), добавить следующие строки кода для реализации двух переопределенных функций:

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Обратите внимание, что в этом примере `PreCreateWindow`указано управление кнопками Windows. Однако любые стандартные элементы управления Windows могут быть подклассифицированы. Для получения дополнительной информации о стандартных элементах управления Windows, [см.](../mfc/controls-mfc.md)

При подгруппе управления Windows можно указать определенный стиль окна (WS_) или расширенные флаги стиля окна (WS_EX_), которые будут использоваться при создании окна элемента управления. Значения этих параметров можно установить `PreCreateWindow` в функции `cs.style` члена, `cs.dwExStyle` изменив поля и поля структуры. Изменения в эти поля должны быть сделаны с помощью **или** операции, чтобы сохранить флаги по умолчанию, которые устанавливаются по классу. `COleControl` Например, если элемент управления подклассирует элемент button и требует, чтобы элемент управления отображался `CSampleCtrl::PreCreateWindow`в виде флажка, вставьте следующую строку кода в реализацию, прежде чем заявление о возврате:

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Эта операция добавляет флаг BS_CHECKBOX стиле, оставляя флаг стиля `COleControl` по умолчанию (WS_CHILD) класса нетронутым.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Изменение функции участника OnDraw

Если вы хотите, чтобы подклассный элемент управления сохранял `OnDraw` тот же внешний вид, что `DoSuperclassPaint` и соответствующий элемент управления Windows, функция элемента управления должна содержать только вызов функции участника, как в следующем примере:

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

Функция `DoSuperclassPaint` члена, реализованная, `COleControl`использует процедуру управления Windows для рисования элемента управления в указанном контексте устройства, в пределах прямоугольника. Это делает элемент управления видимым, даже если он не активен.

> [!NOTE]
> Функция `DoSuperclassPaint` участника будет работать только с теми типами управления, которые позволяют передавать контекст устройства в качестве *wParam* WM_PAINT сообщения. Это включает в себя некоторые из стандартных элементов управления Windows, таких как SCROLLBAR и BUTTON, и все общие элементы управления. Для элементов управления, которые не поддерживают это поведение, вам придется предоставить свой собственный код, чтобы правильно отобразить неактивный элемент управления.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Обработка отраженных сообщений окон

Элементы управления Windows обычно отправляют определенные оконные сообщения в родительское окно. Некоторые из этих сообщений, например WM_COMMAND, предоставляют уведомление о действии пользователя. Другие, такие как WM_CTLCOLOR, используются для получения информации из родительского окна. Контроль ActiveX обычно общается с родительским окном другими средствами. Уведомления передаются путем событий стрельбы (отправка уведомлений о событиях), а информация о контейнере управления получается путем доступа к окружающим свойствам контейнера. Поскольку эти методы связи существуют, контейнеры управления ActiveX не должны обрабатывать любые оконные сообщения, отправленные элементом управления.

Чтобы предотвратить получение контейнера оконных сообщений, отправленных `COleControl` подклассифицированным управлением Windows, создается дополнительное окно, чтобы служить в качестве родительского элемента управления. Это дополнительное окно, называемое "отражателем", создается только для управления ActiveX, который подклассирует управление Windows и имеет тот же размер и положение, что и окно управления. Окно отражателя перехватывает определенные оконные сообщения и отправляет их обратно в управление. Элемент управления в процедуре окна может обрабатывать эти отраженные сообщения, принимая меры, подходящие для управления ActiveX (например, запуск события). Смотрите [идентимативные идентизаты отраженных оконных сообщений](../mfc/reflected-window-message-ids.md) для списка перехваченных сообщений windows и их соответствующих отраженных сообщений.

Контейнер управления ActiveX может быть разработан для выполнения отражения сообщений самостоятельно, устраняя необходимость `COleControl` создания окна отражателя и уменьшая накладные расходы на время выполнения для подклассового управления Windows. `COleControl`определяет, поддерживает ли контейнер эту возможность, проверяя на наличие окружающего свойства MessageReflect со значением **TRUE.**

Для обработки отраженного сообщения окна добавьте запись на карту диспетчерской службы и реализуйте функцию обработчика. Поскольку отраженные сообщения не являются частью стандартного набора сообщений, определяемого Windows, Class View не поддерживает добавление таких обработчиков сообщений. Тем не менее, это не трудно добавить обработчик вручную.

Чтобы добавить обработчик сообщений для отраженного сообщения окна вручную сделайте следующее:

- В классе управления . H файл, объявить функцию обработчика. Функция должна иметь тип возврата **LRESULT** и два параметра, с типами **WPARAM** и **LPARAM**, соответственно. Пример:

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- В классе управления . Файл CPP, добавьте ON_MESSAGE запись на карту сообщений. Параметры этой записи должны быть идентификатором сообщения и названием функции обработчика. Пример:

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Также в . Файл CPP, `OnOcmCommand` реализуйте функцию участника для обработки отраженного сообщения. Параметры *wParam* и *lParam* такие же, как и параметры исходного сообщения окна.

Для примера обработки отраженных сообщений обратитесь к образцу управления MFC ActiveX [BUTTON.](../overview/visual-cpp-samples.md) Он демонстрирует `OnOcmCommand` обработчика, который обнаруживает BN_CLICKED кодом уведомлений и отвечает путем запуска (отправки) `Click` события.

## <a name="see-also"></a>См. также раздел

[Элементы ActiveX библиотеки MFC](../mfc/mfc-activex-controls.md)
