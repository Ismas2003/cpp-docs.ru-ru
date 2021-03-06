---
title: Предупреждение компилятора (уровень 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 31deba2f421b461ba56d13810b5064b353a0e602
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175679"
---
# <a name="compiler-warning-level-1-c4297"></a>Предупреждение компилятора (уровень 1) C4297

function: ожидается, что функция не будет выдавать исключения, но она это делает

Объявление функции содержит (возможно, неявное) спецификатор `noexcept`, пустой `throw` спецификатор исключения или атрибут [__declspec (throw)](../../cpp/nothrow-cpp.md) , а определение содержит один или несколько операторов [throw](../../cpp/try-throw-and-catch-statements-cpp.md) . Чтобы устранить ошибку C4297, не пытайтесь вызвать исключения в функциях, которые объявлены как `__declspec(nothrow)`, `noexcept(true)` или `throw()`. Кроме того, можно удалить спецификацию `noexcept`, `throw()` или `__declspec(nothrow)`.

По умолчанию компилятор создает неявные описатели `noexcept(true)` для определяемых пользователем деструкторов и функций deallocator, а также созданных компилятором специальных функций-членов. Это соответствует стандарту ISO C++ 11. Чтобы предотвратить создание неявных описателей, кроме, и вернуть компилятор к нестандартному поведению Visual Studio 2013, используйте параметр **/Zc: implicitNoexcept-** Compiler. Дополнительные сведения см. в разделе [/Zc: implicitNoexcept (неявные описатели исключений)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Дополнительные сведения о спецификациях исключений см. в разделе [спецификации исключений (throw)](../../cpp/exception-specifications-throw-cpp.md). См. также раздел [/EH (модель обработки исключений)](../../build/reference/eh-exception-handling-model.md) для получения сведений о том, как изменить поведение обработки исключений во время компиляции.

Это предупреждение также создается для функций __declspec ([dllexport](../../cpp/dllexport-dllimport.md)), помеченных как extern "C", даже если C++ они являются функциями.

Следующий пример приводит к возникновению ошибки C4297.

```cpp
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```
