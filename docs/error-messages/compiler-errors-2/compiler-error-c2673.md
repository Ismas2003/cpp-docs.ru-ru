---
title: Ошибка компилятора C2673
ms.date: 11/04/2016
f1_keywords:
- C2673
helpviewer_keywords:
- C2673
ms.assetid: 780230c0-619b-4a78-b01d-ff5886306741
ms.openlocfilehash: 5ade00d0b912a44c0916e5ce5aa7f23b2cc91cf8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757167"
---
# <a name="compiler-error-c2673"></a>Ошибка компилятора C2673

"функция": глобальные функции не имеют указателей "this"

Глобальная функция попыталась получить доступ к `this`.

Следующий пример приводит к возникновению ошибки C2673:

```cpp
// C2673.cpp
int main() {
   this = 0;   // C2673
}
```
