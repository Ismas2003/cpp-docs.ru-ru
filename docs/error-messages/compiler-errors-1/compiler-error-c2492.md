---
title: Ошибка компилятора C2492
ms.date: 11/04/2016
f1_keywords:
- C2492
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
ms.openlocfilehash: fd52b434f86bdc93124c6005bbf7fadad3cb56b2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757063"
---
# <a name="compiler-error-c2492"></a>Ошибка компилятора C2492

"*переменная*": данные с длительностью хранилища потоков могут не иметь интерфейс DLL

Переменная объявляется с помощью атрибута [Thread](../../cpp/thread.md) и интерфейса DLL. Адрес переменной `thread` неизвестен до времени выполнения, поэтому он не может быть связан с импортом или экспортом DLL.

Следующий пример приводит к возникновению ошибки C2492:

```cpp
// C2492.cpp
// compile with: /c
class C {
public:
   char   ch;
};

__declspec(dllexport) __declspec(thread) C c_1;   // C2492
__declspec(thread) C c_1;   // OK
```
