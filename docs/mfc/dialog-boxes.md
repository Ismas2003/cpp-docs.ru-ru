---
title: Диалоговые окна
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: 18b4c4d1386716a0a3282b88d6fdf5a701abce08
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685793"
---
# <a name="dialog-boxes"></a>Диалоговые окна

Приложения для Windows часто взаимодействуют с пользователем с помощью диалоговых окон. Класс [CDialog](../mfc/reference/cdialog-class.md) предоставляет интерфейс для управления диалоговыми окнами, редактор визуальных C++ диалоговых окон упрощает конструирование диалоговых окон и создание ресурсов диалоговых окон, а также мастера кода упрощают процесс инициализации и проверки элементы управления в диалоговом окне и сбор значений, вводимых пользователем.

Диалоговые окна содержат элементы управления, включая:

- Общие элементы управления Windows, такие как поля ввода, кнопки, списки, поля со списком, элементы управления "дерево", элементы управления списками и индикаторы хода выполнения.

- Элементы управления ActiveX.

- Рисуемые владельцем элементы управления: элементы управления, которые вы несете для рисования в диалоговом окне.

Большинство диалоговых окон являются модальными, что требует от пользователя закрыть диалоговое окно перед использованием любой другой части программы. Но можно создать немодальные диалоговые окна, которые позволяют пользователям работать с другими окнами, пока диалоговое окно открыто. MFC поддерживает оба вида диалогового окна с классом `CDialog`. Элементы управления упорядочиваются и управляются с помощью ресурса шаблона диалогового окна, созданного в [редакторе диалоговых окон](../windows/dialog-editor.md).

[Страницы свойств](../mfc/property-sheets-mfc.md), также известные как диалоговые окна вкладок, являются диалоговыми окнами, содержащими «страницы» различных элементов управления диалоговых окон. На каждой странице в верхней части находится папка с файлами "Tab". При щелчке на вкладке Эта страница переводится в начало диалогового окна.

## <a name="what-do-you-want-to-know-more-about"></a>Что вы хотите узнать подробнее

- [Пример. Отображение диалогового окна через команду меню](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [Компоненты диалоговых окон в платформе](../mfc/dialog-box-components-in-the-framework.md)

- [Модальные и немодальные диалоговые окна](../mfc/modal-and-modeless-dialog-boxes.md)

- [Вкладки свойств и страницы свойств](../mfc/property-sheets-and-property-pages-mfc.md) в диалоговом окне

- [Создание ресурса диалогового окна](../mfc/creating-the-dialog-resource.md)

- [Создание класса диалогового окна с помощью мастеров кода](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [Работа с диалоговыми окнами в MFC](../mfc/life-cycle-of-a-dialog-box.md)

- [Обмен данными диалоговых окон (DDX) и проверка (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [Строго типизированный доступ к элементам управления в диалоговом окне](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [Сопоставление сообщений Windows с классом](../mfc/mapping-windows-messages-to-your-class.md)

- [Часто переопределяемые функции-члены](../mfc/commonly-overridden-member-functions.md)

- [Часто добавляемые функции-члены](../mfc/commonly-added-member-functions.md)

- [Классы общих диалоговых окон](../mfc/common-dialog-classes.md)

- [Диалоговые окна в OLE](../mfc/dialog-boxes-in-ole.md)

- Создание приложения, Пользовательский интерфейс которого является диалоговым окном. см. примеры программ [CMNCTRL1](../overview/visual-cpp-samples.md) или [CMNCTRL2](../overview/visual-cpp-samples.md) . Этот параметр также предоставляется мастером приложений.

- [Примеры](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>См. также

[Элементы пользовательского интерфейса](../mfc/user-interface-elements-mfc.md)
