---
title: Предупреждение компилятора (уровень 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 7b6e273de196f6708b92774ce5b436dc810ad3a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161443"
---
# <a name="compiler-warning-level-4-c4205"></a>Предупреждение компилятора (уровень 4) C4205

использовано нестандартное расширение: объявление статической функции в области видимости функции

При использовании расширений Майкрософт (/Ze) **статические** функции могут быть объявлены внутри другой функции. Функции предоставляется глобальная область.

## <a name="example"></a>Пример

```c
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

Такие инициализации недопустимы в режиме совместимости ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).
