---
title: Предупреждение компилятора (уровень 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 2424d076be0914a68c3227566cb851b7ab64cc0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175042"
---
# <a name="compiler-warning-level-1-c4807"></a>Предупреждение компилятора (уровень 1) C4807

"операция": небезопасное смешение типа "тип" и битового поля со знаком типа "тип"

Это предупреждение возникает при сравнении однобитового поля со знаком с переменной `bool` . Так как однобитовое поле со знаком может содержать только значения –1 или 0, его небезопасно сравнивать с `bool`. Сочетание `bool` и однобитовых полей без знака не вызывает предупреждений, так как эти поля идентичны `bool` и могут содержать только 0 или 1.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению предупреждения C4807:

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
