---
title: Ошибка компилятора C3458
ms.date: 11/04/2016
f1_keywords:
- C3458
helpviewer_keywords:
- C3458
ms.assetid: 940202fd-8dcc-4042-9c96-3f9e9127d2f1
ms.openlocfilehash: 98f3dc8ec880a2d134da4cc1438841744b8d9a94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756660"
---
# <a name="compiler-error-c3458"></a>Ошибка компилятора C3458

"атрибут1": атрибут "атрибут2" уже задан для "конструкции"

Для одной и той же конструкции заданы два атрибута, которые являются взаимоисключающими.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3458:

```cpp
// C3458.cpp
// compile with: /clr /c
[System::Reflection::DefaultMember("Chars")]
public ref class MyString {
public:
   [System::Runtime::CompilerServices::IndexerName("Chars")]   // C3458
   property char default[int] {
      char get(int index);
      void set(int index, char c);
   }
};
```
