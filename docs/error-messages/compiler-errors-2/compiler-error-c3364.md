---
title: Ошибка компилятора C3364
ms.date: 11/04/2016
f1_keywords:
- C3364
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
ms.openlocfilehash: eae1e7ddbc34d36b55d7afa424c137db00ef047d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757349"
---
# <a name="compiler-error-c3364"></a>Ошибка компилятора C3364

"Delegate": конструктор делегата: аргумент должен быть указателем на функцию члена управляемого класса или глобальной функции

Второй параметр конструктора делегата принимает либо адрес функции-члена, либо адрес статической функции-члена любого класса. Оба они считаются простыми адресами.

Следующий пример приводит к возникновению ошибки C3364:

```cpp
// C3364_2.cpp
// compile with: /clr

delegate int D( int, int );

ref class C {
public:
   int mf( int, int ) {
      return 1;
   }
};

int main() {
   C^ pC = gcnew C;
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364

   // try the following line instead
   // System::Delegate^ pD = gcnew D(pC, &C::mf);
}
```
