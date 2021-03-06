---
title: Наследование (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: 214900f8f36de0fa90ffcd6ca75f3a4e6e2c0777
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178264"
---
# <a name="inheritance--c"></a>Наследование (C++)

В этом разделе рассматривается использование производных классов для создания расширяемых программ.

## <a name="overview"></a>Обзор

Новые классы могут быть производными от существующих классов с помощью механизма наследования (см. сведения, начиная с [одиночного наследования](../cpp/single-inheritance.md)). Классы, используемые для наследования, называются "базовыми классами" определенного производного класса. Производный класс объявляется с помощью следующего синтаксиса:

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

После тега (имени) класса следует двоеточие и список базовых спецификаций.  Названные таким образом базовые классы, вероятно, были объявлены ранее.  Базовые спецификации могут содержать описатель доступа, который является одним из ключевых слов: **открытый**, **защищенный** или **частный**.  Эти описатели доступа отображаются перед именем базового класса и применяются только к базовому классу.  Эти описатели контролируют разрешение производного класса на использование членов базового класса.  Сведения о доступе к членам базового класса см. в разделе [Управление доступом](../cpp/member-access-control-cpp.md) к членам.  Если описатель доступа опущен, доступ к этой базе будет считаться **закрытым**.  Базовые спецификации могут содержать ключевое слово **Virtual** , указывающее на виртуальное наследование.  Это ключевое слово может отображаться до или после описателя доступа, если таковые имеются.  Если используется виртуальное наследование, базовый класс называется виртуальным базовым классом.

Можно определить несколько базовых классов, разделив их запятыми.  Если указан один базовый класс, то модель наследования является [одиночным наследованием](../cpp/single-inheritance.md). Если указано более одного базового класса, то модель наследования называется [множественным наследованием](../cpp/multiple-base-classes.md).

В этой статье содержатся следующие разделы:

- [Одиночное наследование](../cpp/single-inheritance.md)

- [Несколько базовых классов](../cpp/multiple-base-classes.md)

- [Виртуальные функции](../cpp/virtual-functions.md)

- [Явные переопределения](../cpp/explicit-overrides-cpp.md)

- [Абстрактные классы](../cpp/abstract-classes-cpp.md)

- [Сводка правил области действия](../cpp/summary-of-scope-rules.md)

В этом разделе описаны ключевые слова [__super](../cpp/super.md) и [__interface](../cpp/interface.md) .

## <a name="see-also"></a>См. также раздел

[Справочник по языку C++](../cpp/cpp-language-reference.md)
