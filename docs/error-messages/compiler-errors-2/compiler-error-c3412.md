---
title: Ошибка компилятора C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: ad241b656464746333760cfcbc134c91e49bf44e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761420"
---
# <a name="compiler-error-c3412"></a>Ошибка компилятора C3412

"шаблон": не удается заспециализациь шаблона в текущей области

Шаблон не может быть специализированным в области видимости класса, только в области глобальных или пространств имен.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3412.

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

## <a name="example"></a>Пример

В следующем примере показано возможное решение.

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
