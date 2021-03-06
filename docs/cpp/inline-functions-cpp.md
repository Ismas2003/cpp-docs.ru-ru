---
title: Встраиваемые функции (C++)
ms.date: 10/09/2018
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
ms.openlocfilehash: 703c04873a733d068da025b595909ecc681ff147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374088"
---
# <a name="inline-functions-c"></a>Встраиваемые функции (C++)

Функция, определенная в теле объявления класса, является встроенной.

## <a name="example"></a>Пример

В показанном ниже объявлении класса конструктор `Account` является встраиваемой функцией. Функция участника `GetBalance` `Deposit`и `Withdraw` не указаны как **вонючие,** но могут быть реализованы в виде внеочередных функций.

```cpp
// Inline_Member_Functions.cpp
class Account
{
public:
    Account(double initial_balance) { balance = initial_balance; }
    double GetBalance();
    double Deposit( double Amount );
    double Withdraw( double Amount );
private:
    double balance;
};

inline double Account::GetBalance()
{
    return balance;
}

inline double Account::Deposit( double Amount )
{
    return ( balance += Amount );
}

inline double Account::Withdraw( double Amount )
{
    return ( balance -= Amount );
}
int main()
{
}
```

> [!NOTE]
> В декларации класса функции были **inline** объявлены без встраиваемого ключевого слова. **Включиватете** ключевое слово может быть указано в декларации класса; результат тот же.

Заданная встроенная функция-член должна быть объявлена одинаково в каждом блоке компиляции. Из-за этого ограничения встраиваемые функции работают так же, как если бы они были созданными экземплярами функций. Кроме того, должно существовать только одно определение встраиваемой функции.

Функция члена класса по умолчанию по умолчанию не связана с внешней связью, если только определение этой функции не содержит **спецификации.** Предыдущий пример показывает, что эти функции не должны быть четко объявлены с **помощью вневешку;** использование **внеочередных** в определении функции приводит к тому, что она является вненужной функцией. Однако повторное объявление функции в качестве **вонючего** после вызова к этой функции является незаконным.

## <a name="inline-__inline-and-__forceinline"></a>Вline, __inline \_и _forceinline

**Встроенные** и **__inline** спецификаторы инструктируют компилятор вставить копию тела функции в каждое место, где вызывается функция.

Такая вставка (она называется подстановкой или встраиванием) выполняется только в том случае, если проведенный компилятором анализ затрат и выгод показывает, что это может дать выигрыш. Подстановка снимает нагрузку на вызов функции, иногда ценой увеличения размера кода.

В **__forceinline** ключевое слово переопределяет анализ затрат/выгод и опирается на суждения программиста. Упражнение осторожность при **использовании __forceinline**. Неизбирательное использование **__forceinline** может привести к увеличению кода с лишь незначительными приростами к производительности или, в некоторых случаях, даже потерями производительности (из-за увеличения, например, более крупного исполнения).

Применение встраиваемых функций может ускорить выполнение программ, поскольку устраняет нагрузку на вызов функций. Для подставляемых функций выполняются оптимизации кода, которые недоступны для обычных функций.

Параметры и ключевые слова подстановки компилятор обрабатывает как рекомендации. Подстановка функции не гарантируется. Вы не можете заставить компилятор ввести определенную функцию, даже с **__forceinline** ключевого слова. При компиляции с **/clr**компилятор не будет встраивать функцию, если к функции применены атрибуты безопасности.

**Включущее** ключевое слово доступно только в СЗ. Ключевые слова **__inline** и **__forceinline** доступны как в C, так и в C. Для совместимости с предыдущими версиями **_inline** и **_forceinline** являются синонимами для **__inline,** и **__forceinline** если не указан вариант компилятора [/ расширение языка Свыкосновенных. \(](../build/reference/za-ze-disable-language-extensions.md)

**Включиватемое** ключевое слово говорит компилятору, что внее расширение предпочтительнее. Однако компилятор может создать отдельный экземпляр функции и вместо подстановки кода создать стандартную компоновку вызова. Существует две ситуации, в которых это может происходить.

- Рекурсивные функции.

- Функции, на которые создаются ссылки посредством указателя в любом месте блока трансляции.

Эти причины могут помешать подчеркиванию, *как и другие,* по усмотрению компилятора; вы не должны зависеть от **встроенного** спецификации, чтобы вызвать функцию, которая будет подстроена.

Как при использовании обычных функций, для встраиваемых функций нет заданного порядка вычисления аргументов. Фактически он может отличаться от порядка, в котором аргументы вычисляются при передаче с использованием обычного протокола вызова функций.

Опция оптимизации компилятора [/Ob](../build/reference/ob-inline-function-expansion.md) помогает определить, действительно ли происходит расширение внее функции.

[/LTCG](../build/reference/ltcg-link-time-code-generation.md) выполняет кросс-модуль, подчеркивая независимо от того, было ли это запрошено в исходном коде.

### <a name="example-1"></a>Пример 1

```cpp
// inline_keyword1.cpp
// compile with: /c
inline int max( int a , int b ) {
   if( a > b )
      return a;
   return b;
}
```

Функции члена класса могут быть объявлены вставки либо с помощью **встраиваемого** ключевого слова, либо путем размещения определения функции в определении класса.

### <a name="example-2"></a>Пример 2

```cpp
// inline_keyword2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;

class MyClass {
public:
   void print() { cout << i << ' '; }   // Implicitly inline
private:
   int i;
};
```

**Microsoft Специфический**

**Ключевое** __inline эквивалентно **внеочередным.**

Даже при **__forceinline**компилятор не может вставить код в любой из обстоятельств. Компилятор не выполняет подстановку, если:

- Функция или вызывающий ее объект скомпилированы с параметром /Ob0 (параметр по умолчанию для отладочной сборки).

- В функции и вызывающем объекте используются разные типы (в одном — обработка исключений C++, а в другом — структурированная).

- Функция имеет переменное число аргументов.

- В функции используется встроенный код ассемблера (кроме случаев компиляции с параметром /Og, /Ox, /O1 или /O2).

- Функция является рекурсивной и не сопровождается **#pragma inline_recursion(на)**. С помощью этой директивы выполняется подстановка рекурсивных функций с глубиной по умолчанию, 16 вызовам. Чтобы уменьшить глубину, используйте [inline_depth](../preprocessor/inline-depth.md) прагму.

- Функция является виртуальной, и для нее используется виртуальный вызов. Прямые вызовы виртуальных функций могут подставляться.

- Программа принимает адрес функции, и вызов совершается через указатель на функцию. Прямые вызовы функций, чей адрес был принят, могут подставляться.

- Функция также отмечена [донайным](../cpp/naked-cpp.md) модификатором [__declspec.](../cpp/declspec.md)

Если компилятор не может вставить функцию, заявленную **с __forceinline,** он генерирует предупреждение уровня 1, за исключением случаев, когда:

- Функция компилируется с помощью /Od или /Ob0. В этих случаях не ожидается никаких признаков.

- Функция определяется внешне, в включенной библиотеке или другой единице перевода, или является виртуальной целью вызова или непрямой целью вызова. Компилятор не может определить неподнитенный код, который он не может найти в текущем блоке перевода.

Рекурсивные функции могут быть заменены внеочередными на глубину, указанную [inline_depth](../preprocessor/inline-depth.md) прагму, максимум до 16 вызовов. Начиная с этой глубины рекурсивные функции обрабатываются как вызовы на экземпляр функции.  Глубина, до которой эвристический поиск для подстановки функций проверяет рекурсивные функции, не может превышать 16 вызовов. [В inline_recursion](../preprocessor/inline-recursion.md) прагма контролирует расширение функции, которая в настоящее время находится в стадии расширения. Для получения соответствующей информации просмотрите опцию компилятора [Inline-Function](../build/reference/ob-inline-function-expansion.md) (/Ob).

**END Microsoft Специфический**

Для получения дополнительной информации об использовании **внештатного** специателя см.:

- [Подставляемые функции-члены класса](../cpp/inline-functions-cpp.md)

- [Определение функций Inline C е с dllexport и dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Когда использовать встраиваемые функции

Встроенные функции лучше использовать для небольших функций, например функций доступа к закрытым элементам данных. Основное назначение таких одно- и двухстрочных функций метода доступа — возвращение сведений о состоянии объектов; короткие функции чувствительны к рабочей нагрузке вызовов функций. Более длинные функции тратят пропорционально меньше времени на выполнение последовательности вызова и возврата. Встраивание дает им меньше преимуществ.

Класс `Point` может быть определен следующим образом:

```cpp
// when_to_use_inline_functions.cpp
class Point
{
public:
    // Define "accessor" functions as
    //  reference types.
    unsigned& x();
    unsigned& y();
private:
    unsigned _x;
    unsigned _y;
};

inline unsigned& Point::x()
{
    return _x;
}
inline unsigned& Point::y()
{
    return _y;
}
int main()
{
}
```

Предполагая, что манипуляция координатами является относительно распространенной операцией `y` у клиента такого класса, указывая две функции accessor (и`x` в предыдущем примере), как **вставка** обычно сохраняет накладные расходы на:

- вызовы функций (включая передачу параметров и размещение адреса объекта в стеке);

- сохранение кадра стека вызывающего объекта;

- настройку нового кадра стека;

- передачу возвращаемого значения;

- восстановление старого кадра стека;

- Возвращает

## <a name="inline-functions-vs-macros"></a>Функции вне очередных и макросов

Хотя встраиваемые функции похожи на макросы (поскольку код функции разворачивается в точке вызова во время компиляции), встраиваемые функции анализируются компилятором, тогда как макросы разворачиваются препроцессором. В результате, имеется несколько важных различий.

- Встраиваемые функции выполняют все протоколы безопасности типов, обязательные для обычных функций.

- Функции inline указаны с использованием того же синтаксиса, что и любая другая функция, за исключением того, что они включают в себя **включаемые** ключевые слова в декларации функций.

- Выражения, передаваемые во встраиваемые функции в качестве аргументов, вычисляются один раз. В некоторых случаях выражения, передаваемые в макросы в качестве аргументов, можно вычислить несколько раз.

В следующем примере показан макрос, преобразующий строчные буквы в прописные.

```cpp
// inline_functions_macro.c
#include <stdio.h>
#include <conio.h>

#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))

int main() {
   char ch;
   printf_s("Enter a character: ");
   ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
//  Sample Input:  xyz
// Sample Output:  Z
```

Цель выражения `toupper(getc(stdin))` состоит в том, что символ должен`stdin`быть прочитан с консольного устройства () и, при необходимости, преобразован в верхний регистр.

В результате реализации макроса `getc` выполняется один раз для определения того, больше или равен "a" символ, и один раз для определения того, меньше он или равен "z". Если символ находится в этом диапазоне, `getc` выполняется еще раз для преобразования символа в прописную букву. Это означает, что программа ожидает два или три символа, когда в идеальном случае она должна ожидать только один.

Подставляемые функции позволяют устранить описанную выше проблему.

```cpp
// inline_functions_inline.cpp
#include <stdio.h>
#include <conio.h>

inline char toupper( char a ) {
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );
}

int main() {
   printf_s("Enter a character: ");
   char ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
```

```Output
Sample Input: a
Sample Output: A
```

## <a name="see-also"></a>См. также раздел

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)
