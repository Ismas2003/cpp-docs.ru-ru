---
title: Постоянные выражения C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: d4d9803c7f80caba3c33d011e4df433491b9b591
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170583"
---
# <a name="c-constant-expressions"></a>Постоянные выражения C++

*Константа* — это значение, которое не изменяется. В C++ имеется два ключевых слова, позволяющих указать, что объект не должен изменяться, и для осуществления этого намерения.

В C++ требуются константные выражения, то есть выражения, результатом вычисления которых является константа, для объявления следующих элементов.

- Границы массива.

- Селекторы в операторах case.

- Спецификация длины битового поля.

- Инициализаторы перечисления.

Ниже перечислены единственные допустимые операнды в константных выражениях.

- Литералы

- Константы перечисления.

- Значения, объявленные как константы, которые инициализированы с константными выражениями.

- выражения **sizeof**

Нецелочисленные константы должны преобразовываться (явно или неявно) в целочисленные типы, чтобы быть допустимыми в константном выражении. Поэтому следующий код допустим.

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Явные преобразования в целочисленные типы допустимы в константных выражениях; все остальные типы и производные типы являются недопустимыми, за исключением случаев использования в качестве операндов оператору **sizeof** .

Запятую-оператор и операторы присваивания невозможно использовать в константных выражениях.

## <a name="see-also"></a>См. также раздел

[Типы выражений](../cpp/types-of-expressions.md)
