---
title: Использование элемента управления "Сочетание клавиш"
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
ms.openlocfilehash: d9178fe989e476111a3da55861642e9aa6311872
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180535"
---
# <a name="using-a-hot-key-control"></a>Использование элемента управления "Сочетание клавиш"

Типичное применение элемента управления "Горячий" ключа соответствует шаблону ниже:

- Создается элемент управления. Если элемент управления, заданный в шаблон диалогового окна, создание выполняется автоматически, когда создается диалоговое окно. (Вы должны иметь [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) член в класс диалогового окна, соответствующее элементу управления "Горячий" ключа.) Кроме того, можно использовать [создать](../mfc/reference/chotkeyctrl-class.md#create) функцию-член для создания элемента управления как дочернего окна любого окна.

- Если вы хотите установить значение по умолчанию для элемента управления, вызовите [SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) функция-член. Если вы хотите запретить определенные состояния сдвига, вызвать [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). Для элементов управления в диалоговом окне — самое время сделать это, в диалоговом окне [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) функции.

- Пользователь взаимодействует с элементом управления, нажав сочетание клавиш "Горячий", при активном ключа элемент управления имеет фокус. Пользователь затем каким-либо образом указывает, что эта задача завершена, возможно, нажав кнопку в диалоговом окне.

- Когда приложение получает уведомление, что пользователь выбрал сочетания клавиш, его следует использовать функцию-член [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) для получения виртуального ключа- and -shift значений состояния из "Горячий" ключа элемента управления.

- Если известно, какой ключ выбранный пользователем, можно задать сочетания клавиш, с помощью одного из методов, описанных в [задание сочетания клавиш](../mfc/setting-a-hot-key.md).

- Если в диалоговом окне "Горячий" ключа элемент управления его и `CHotKeyCtrl` объект будет удален автоматически. Если нет, то необходимо убедиться, что оба элемента управления и `CHotKeyCtrl` объекта удаляются должным образом.

## <a name="see-also"></a>См. также

[Использование CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Элементы управления](../mfc/controls-mfc.md)
