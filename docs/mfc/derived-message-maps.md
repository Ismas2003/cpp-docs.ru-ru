---
title: Производные схемы сообщений
ms.date: 11/19/2018
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: fcdff67c57e932e414a2b61b28cd0498ab997c60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173590"
---
# <a name="derived-message-maps"></a>Производные схемы сообщений

Во время сообщения, обработка, проверка сообщения принадлежащего классу карты не конец истории схемы сообщений. Что произойдет, если класс `CMyView` (производный от `CView`), не имеет соответствующей записи сообщения

Имейте в виду, что `CView`, базовый класс `CMyView`, в свою очередь наследуется из `CWnd`. Таким образом `CMyView` *—* `CView` и *—* `CWnd`. Каждый из этих классов имеет собственную схему сообщений. Рисунок, «просмотр иерархии» ниже показано иерархические отношения из классов, но имейте в виду, что `CMyView` объект представляет собой один объект, который имеет характеристики всех трех классов.

![Иерархия представления](../mfc/media/vc38621.gif "иерархия представления") <br/>
Просмотр иерархии

Таким образом, если сообщение не может быть сопоставлен в классе `CMyView`в схему сообщений, платформы, кроме того, выполняет сопоставление сообщений свой непосредственный базовый класс. `BEGIN_MESSAGE_MAP` Макрос в начале сообщений указывает два имени класса как аргументы:

[!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]

Первый аргумент имен класса, к которому принадлежит схеме сообщений. Второй аргумент обеспечивает подключение с помощью непосредственного базового класса — `CView` здесь, чтобы платформу можно найти схему сообщений, слишком.

Обработчики сообщений, предоставленный в базовом классе таким образом, наследуются от производного класса. Это очень похоже на обычный виртуальных функций-членов без необходимости вносить все функции-члены обработчика виртуальной.

Если обработчик не найден в любой из maps сообщение базового класса, выполняется обработка по умолчанию сообщения. Если сообщение команды, платформа перенаправляет его в следующий целевой объект команды. Если это стандартное сообщение Windows, сообщение передается процедуре окна соответствующее значение по умолчанию.

Для повышения скорости сопоставления схемы сообщений, платформа кэширует последние совпадения по вероятность того, что он будет получать то же сообщение снова. Следствием этого является процессы framework довольно эффективно необработанных сообщений. Схемы сообщений также пространство эффективнее, чем реализаций, использующих виртуальные функции.

## <a name="see-also"></a>См. также

[Выполнение платформой поиска по схемам сообщений](../mfc/how-the-framework-searches-message-maps.md)
