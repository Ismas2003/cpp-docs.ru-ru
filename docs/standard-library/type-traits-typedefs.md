---
title: Определения типов &lt;type_traits&gt;
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::false_type
- xtr1common/std::false_type
- type_traits/std::true_type
- xtr1common/std::true_type
ms.assetid: 8ac040ca-ed2d-4570-adc9-cb5626530053
ms.openlocfilehash: 784bcfa5325e74180d3981a98cda530d839ab9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367980"
---
# <a name="lttype_traitsgt-typedefs"></a>Определения типов &lt;type_traits&gt;

|||
|-|-|
|[false_type](#false_type)|[true_type](#true_type)|

## <a name="false_type-typedef"></a><a name="false_type"></a>false_type Типдеф

Содержит целочисленную константу со значением false.

```cpp
typedef integral_constant<bool, false> false_type;
```

### <a name="remarks"></a>Remarks

Тип является синонимом для специализации шаблона `integral_constant`.

### <a name="example"></a>Пример

```cpp
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="true_type-typedef"></a><a name="true_type"></a>true_type Типдеф

Содержит целочисленную константу со значением true.

```cpp
typedef integral_constant<bool, true> true_type;
```

### <a name="remarks"></a>Remarks

Тип является синонимом для специализации шаблона `integral_constant`.

### <a name="example"></a>Пример

```cpp
// std__type_traits__true_type.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main() {
    std::cout << "false_type == " << std::boolalpha
        << std::false_type::value << std::endl;
    std::cout << "true_type == " << std::boolalpha
        << std::true_type::value << std::endl;

    return (0);
}
```

```Output
false_type == false
true_type == true
```

## <a name="see-also"></a>См. также раздел

[<type_traits>](../standard-library/type-traits.md)
