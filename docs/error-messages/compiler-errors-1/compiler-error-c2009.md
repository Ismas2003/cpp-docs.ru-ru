---
title: Ошибка компилятора C2009
ms.date: 11/04/2016
f1_keywords:
- C2009
helpviewer_keywords:
- C2009
ms.assetid: fe9d94ed-20a5-4d83-b9c4-60ee69d2f30a
ms.openlocfilehash: 434ae830e78c8fb5fe4e56438a557afb027d264f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752448"
---
# <a name="compiler-error-c2009"></a>Ошибка компилятора C2009

повторное использование формального параметра макроса "идентификатор"

Список формальных параметров в определении макроса использует идентификатор более одного раза. Идентификаторы в списке параметров макроса должны быть уникальными.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C2009:

```cpp
// C2009.cpp
#include <stdio.h>

#define macro1(a,a) (a*a)   // C2009

int main()
{
    printf_s("%d\n", macro1(2));
}
```

## <a name="example"></a>Пример

Возможное решение

```cpp
// C2009b.cpp
#include <stdio.h>

#define macro2(a)   (a*a)
#define macro3(a,b) (a*b)

int main()
{
    printf_s("%d\n", macro2(2));
    printf_s("%d\n", macro3(2,4));
}
```
