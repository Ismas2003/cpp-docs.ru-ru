---
title: Предупреждение компилятора (уровень 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 6d110aa70a470382e274546e95599804fa3bc7d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199879"
---
# <a name="compiler-warning-level-1-c4190"></a>Предупреждение компилятора (уровень 1) C4190

"идентификатор1" имеет указанную компоновку C, но возвращает определяемый пользователем тип "идентификатор2", который несовместим с C

Функция или указатель на функцию имеют ОПРЕДЕЛЯЕМый пользователем тип, который является классом, структурой, перечислением или объединением, в качестве возвращаемого типа и `extern` компоновки "C". Это допустимо, если:

- Все вызовы этой функции происходят из C++.

- Определение функции находится в C++.

## <a name="example"></a>Пример

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
