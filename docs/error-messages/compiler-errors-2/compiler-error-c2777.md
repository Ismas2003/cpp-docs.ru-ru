---
title: Ошибка компилятора C2777
ms.date: 11/04/2016
f1_keywords:
- C2777
helpviewer_keywords:
- C2777
ms.assetid: 5fe158c0-2a65-488a-aca2-61d4a8b32d43
ms.openlocfilehash: 67132f0acbee3614d8032685ae454386d97b8fb1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740017"
---
# <a name="compiler-error-c2777"></a>Ошибка компилятора C2777

для каждого свойства можно указать только один метод "помещает"

Модификатор [Свойства](../../cpp/property-cpp.md) declspec имеет более одного свойства `put`.

Следующий пример приводит к возникновению ошибки C2777:

```cpp
// C2777.cpp
struct A {
   __declspec(property(put=PutProp,put=PutPropToo))   // C2777
   // try the following line instead
   // __declspec(property(put=PutProp))
      int prop;
   int PutProp(void);
   int PutPropToo(void);
};
```
