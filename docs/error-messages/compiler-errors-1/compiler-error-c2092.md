---
title: Ошибка компилятора C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: b530663cae2292ebeab1b871e495e9a45e4633cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754671"
---
# <a name="compiler-error-c2092"></a>Ошибка компилятора C2092

Тип элемента массива "имя массива" не может быть функцией

Массивы функций не допускаются. Используйте массив указателей на функции.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C2092:

```cpp
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

## <a name="example"></a>Пример

Возможное решение

```cpp
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```
