---
title: Предупреждение компилятора (уровень 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: 0788824dd4180476d81d9682f99fb95883b8c4f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198345"
---
# <a name="compiler-warning-level-4-c4559"></a>Предупреждение компилятора (уровень 4) C4559

> "*функция*": переопределение; Функция прибылей __declspec (*Модификатор*)

## <a name="remarks"></a>Remarks

Функция была переопределена или объявлена повторно, а второе определение или объявление добавило модификатор **__declspec** (*Модификатор*). Это предупреждение носит информационный характер. Чтобы устранить это предупреждение, удалите одно из определений.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```
