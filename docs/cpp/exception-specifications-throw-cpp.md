---
title: Спецификации исключений (throw, не Except) (C++)
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 6f8f9466b867603738919c6210055d02d3c579ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180047"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Спецификации исключений (throw, не Except) (C++)

Спецификации исключений — это C++ функция языка, которая указывает намерение программиста о типах исключений, которые могут распространяться функцией. Можно указать, что функция может или не может выйти за исключением, используя *спецификацию исключения*. Компилятор может использовать эти сведения для оптимизации вызовов функции, а также для завершения программы, если непредвиденное исключение приводит к экранированию функции.

До C++ 17 существовали два типа спецификаций исключений. В C++ 11 была введена *только спецификация* . Он указывает, является ли набор возможных исключений, которые могут вызывать функцию, пустым. *Спецификация динамических исключений*или спецификация `throw(optional_type_list)` устарела в c++ 11 и удалена в c++ 17, за исключением `throw()`, который является псевдонимом для `noexcept(true)`. Эта спецификация исключений была разработана для предоставления сводных сведений о том, какие исключения могут быть вызваны из функции, но на практике обнаружены проблемы. Одна из динамических исключений, которая была бы довольно полезной, была неусловной `throw()` спецификации. Например, объявление функции:

```cpp
void MyFunction(int i) throw();
```

сообщает компилятору, что функция не создает исключений. Однако в **/std: режим c++ 14** это может привести к неопределенному поведению, если функция создает исключение. Поэтому рекомендуется использовать оператор " [except](../cpp/noexcept-cpp.md) " вместо того, который приведен выше.

```cpp
void MyFunction(int i) noexcept;
```

В следующей таблице перечислены реализации спецификаций C++ исключений Майкрософт.

|Спецификация исключений|Значение|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|Функция не вызывает исключений. В [/std: режим c++ 14](../build/reference/std-specify-language-standard-version.md) (по умолчанию), `noexcept` и `noexcept(true)` эквивалентны. При возникновении исключения из функции, объявленной `noexcept` или `noexcept(true)`, вызывается [std:: Terminate](../standard-library/exception-functions.md#terminate) . При возникновении исключения из функции, объявленной как `throw()` в режиме **/std: c++ 14** , результат является неопределенным поведением. Никакая конкретная функция не вызывается. Это расхождение по стандарту C++ 14, которое требует, чтобы компилятор вызывал [std:: непредвиденный](../standard-library/exception-functions.md#unexpected).  <br/> **Visual Studio 2017 версии 15,5 и более поздних**версий: в **/std: режим c++ 17** , `noexcept`, `noexcept(true)`и `throw()` являются эквивалентными. В **/std: режим c++ 17** `throw()` является псевдонимом для `noexcept(true)`. В режиме **/std: c++ 17** при возникновении исключения из функции, объявленной с любой из этих спецификаций, [std:: Terminate](../standard-library/exception-functions.md#terminate) вызывается согласно требованиям стандарта c++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Нет спецификации|Функция может вызывать исключение любого типа.|
|`throw(type)`| (**C++ 14 и более ранние версии**) Функция может вызвать исключение типа `type`. Компилятор принимает синтаксис, но интерпретирует его как `noexcept(false)`. В **/std: режим c++ 17** . компилятор выдает предупреждение C5040.|

Если в приложении используется обработка исключений, в стеке вызовов должна быть функция, которая обрабатывает созданные исключения до выхода из внешней области функции, помеченной `noexcept`, `noexcept(true)`или `throw()`. Если какая-либо из функций, вызываемых между исключением и обработчиком исключения, задается как `noexcept`, `noexcept(true)` (или `throw()` в режиме **/std: c++ 17** ), программа завершается, когда исключение распространяется функцией, кроме.

Поведение функции зависит от следующих факторов:

- Установлен [режим компиляции стандартного языка](../build/reference/std-specify-language-standard-version.md) .
- В какой среде выполняется компиляция функции — в C или C++.

- Используемый параметр компилятора [/EH](../build/reference/eh-exception-handling-model.md) .

- Задана ли явно спецификация исключений.

Явные спецификации исключений не разрешено использовать для функций C. Предполагается, что функция C не создает исключения в **/EHsc**и может вызывать структурированные исключения в порядке **/EHs**, **/EHa**или **/ехак**.

В следующей таблице приведены сведения о том C++ , может ли функция вызываться в различных параметрах обработки исключений компилятора.

|Компонент|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|Функция C++ без спецификации исключений|Да|Да|Да|Да|
|C++функция с `noexcept`, `noexcept(true)`или спецификацией исключения `throw()`|нет|нет|Да|Да|
|C++функция с `noexcept(false)`, `throw(...)`или спецификацией исключения `throw(type)`|Да|Да|Да|Да|

## <a name="example"></a>Пример

```cpp
// exception_specification.cpp
// compile with: /EHs
#include <stdio.h>

void handler() {
   printf_s("in handler\n");
}

void f1(void) throw(int) {
   printf_s("About to throw 1\n");
   if (1)
      throw 1;
}

void f5(void) throw() {
   try {
      f1();
   }
   catch(...) {
      handler();
    }
}

// invalid, doesn't handle the int exception thrown from f1()
// void f3(void) throw() {
//   f1();
// }

void __declspec(nothrow) f2(void) {
   try {
      f1();
   }
   catch(int) {
      handler();
    }
}

// only valid if compiled without /EHc
// /EHc means assume extern "C" functions don't throw exceptions
extern "C" void f4(void);
void f4(void) {
   f1();
}

int main() {
   f2();

   try {
      f4();
   }
   catch(...) {
      printf_s("Caught exception from f4\n");
   }
   f5();
}
```

```Output
About to throw 1
in handler
About to throw 1
Caught exception from f4
About to throw 1
in handler
```

## <a name="see-also"></a>См. также раздел

[Операторы try, throw и catch (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[Современные C++ рекомендации по исключениям и обработке ошибок](errors-and-exception-handling-modern-cpp.md)
