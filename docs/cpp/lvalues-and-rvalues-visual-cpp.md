---
title: 'Категории значений: значения lvalue и rvalue (C++)'
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 23625ddf44d16a4dc408b87f27b9cdfba7a9cbd4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077239"
---
# <a name="lvalues-and-rvalues-c"></a>Значения Lvalue и Rvalue (C++)

Каждое C++ выражение имеет тип и принадлежит к *категории значений*. Категории значений являются основанием для правил, которым должны следовать компиляторы при создании, копировании и перемещении временных объектов во время оценки выражений.

Стандарт C++ 17 определяет категории значений выражений следующим образом:

- *Глвалуе* — это выражение, вычисление которого определяет идентификатор объекта, битового поля или функции.
- *Prvalue* — это выражение, вычисление которого Инициализирует объект или битовое поле или выполняет вычисление значения операнда оператора, как указано в контексте, в котором он отображается.
- *XValue* — это глвалуе, который обозначает объект или битовое поле, ресурсы которого можно использовать повторно (обычно потому, что он находится ближе к концу своего времени существования). Пример. определенные типы выражений, включающие ссылки rvalue (8.3.2), выдают ксвалуес, например, вызов функции, тип возвращаемого значения которого является ссылкой rvalue или приведен к ссылочному типу rvalue.
- *Lvalue* — это глвалуе, который не является xValue.
- *Rvalue* — это prvalue или xValue.

На следующей схеме показаны связи между категориями.

![C++категории значений выражений](media/value_categories.png "C++категории значений выражений")

Lvalue имеет адрес, к которому программа может получить доступ. Примерами выражений lvalue являются имена переменных, включая **константные** переменные, элементы массива, вызовы функций, возвращающие ссылки на lvalue, битовые поля, объединения и члены классов.

Выражение prvalue не имеет адреса, доступного вашей программой. Примерами выражений prvalue являются литералы, вызовы функций, возвращающие тип, не являющийся ссылочным, и временные объекты, созданные во время евалутиона выражения, но доступные только компилятору.

Выражение xValue имеет адрес, который больше не доступен для вашей программы, но может использоваться для инициализации ссылки rvalue, которая предоставляет доступ к выражению. К примерам относятся вызовы функций, возвращающие ссылку rvalue, а также индексы массива, члена и указателя на элементы, где массив или объект является ссылкой rvalue.

## <a name="example"></a>Пример

В следующем примере показано несколько правильных и неправильных способов использования значений lvalue и rvalues.

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;

    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> В примерах этого раздела показано правильное и неправильное использование при неперегруженных операторах. Перегрузив операторы, можно преобразовать выражение, такое как `j * 4`, в значение lvalue.

Термины *lvalue* и *rvalue* часто используются при ссылке на ссылки на объекты. Дополнительные сведения о ссылках см. в разделе [декларатор ссылки lvalue: &](../cpp/lvalue-reference-declarator-amp.md) и [декларатор ссылки Rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>См. также:

[Основные понятия](../cpp/basic-concepts-cpp.md)<br/>
[Декларатор ссылки Lvalue: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Декларатор ссылки Rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md)
