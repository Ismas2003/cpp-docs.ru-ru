---
title: Структура pair
ms.date: 11/04/2016
f1_keywords:
- utility/std::pair
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
ms.openlocfilehash: f372ae036ff4843532efa18c3d518820b5f06111
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244419"
---
# <a name="pair-structure"></a>Структура pair

Структура, позволяющая обрабатывать два объекта как один объект.

## <a name="syntax"></a>Синтаксис

```cpp
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    pair(const pair&) = default;
    pair(pair&&) = default;
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);

    template <class... Args1, class... Args2>
    pair(piecewise_construct_t, tuple<Args1...> first_args, tuple<Args2...> second_args);

    pair& operator=(const pair& p);
    template<class U1, class U2> pair& operator=(const pair<U1, U2>& p);
    pair& operator=(pair&& p) noexcept(see below );
    template<class U1, class U2> pair& operator=(pair<U1, U2>&& p);

    void swap(pair& p) noexcept(see below );
};

template<class T1, class T2>
    pair(T1, T2) -> pair<T1, T2>;
```

### <a name="parameters"></a>Параметры

*val1*\
Значение, которое инициализирует первый элемент `pair`.

*Val2*\
Значение, которое инициализирует второй элемент `pair`.

*Правильно*\
Пара, значения которой будут использоваться для инициализации элементов другой пары.

## <a name="return-value"></a>Возвращаемое значение

Первый конструктор (по умолчанию) инициализирует первый элемент пары как значение по умолчанию типа `T1` и второй элемент по умолчанию типа `T2`.

Второй конструктор инициализирует первый элемент пары как *Val1* и второй для *Val2.*

Третий конструктор (шаблон) инициализирует первый элемент пары как `Right`. **first**, а второй — как `Right`. **second**.

Четвертый конструктор инициализирует первый элемент пары как *Val1* и второй для *Val2* с помощью [декларатор ссылки Rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="remarks"></a>Примечания

Структура шаблона хранит пары объектов типа `T1` и `T2`, соответственно. Тип `first_type` совпадает со значением параметра-шаблона `T1` и тип `second_type` совпадает со значением параметра-шаблона `T2`. `T1` и `T2` должны предоставлять только конструктор по умолчанию, конструктор с одним аргументом и деструктор. Все члены типа `pair` являются открытыми, так как тип объявлен как `struct`, а не как **класс**. Два наиболее распространенных способа применения пары — в качестве возвращаемых типов для функций, возвращающих два значения, и в качестве элементов для классов ассоциативных контейнеров [map](../standard-library/map-class.md) и [multimap](../standard-library/multimap-class.md), у которых есть ключ и тип значения, связанные с каждым элементом. Последнее удовлетворяет требованиям для парного ассоциативного контейнера и имеет тип значения в формате `pair`< **const**`key_type`, `mapped_type`>.

## <a name="example"></a>Пример

```cpp
// utility_pair.cpp
// compile with: /EHsc
#include <utility>
#include <map>
#include <iomanip>
#include <iostream>

int main( )
{
   using namespace std;

   // Using the constructor to declare and initialize a pair
   pair <int, double> p1 ( 10, 1.1e-2 );

   // Compare using the helper function to declare and initialize a pair
   pair <int, double> p2;
   p2 = make_pair ( 10, 2.22e-1 );

   // Making a copy of a pair
   pair <int, double> p3 ( p1 );

   cout.precision ( 3 );
   cout << "The pair p1 is: ( " << p1.first << ", "
        << p1.second << " )." << endl;
   cout << "The pair p2 is: ( " << p2.first << ", "
        << p2.second << " )." << endl;
   cout << "The pair p3 is: ( " << p3.first << ", "
        << p3.second << " )." << endl;

   // Using a pair for a map element
   map <int, int> m1;
   map <int, int>::iterator m1_Iter;

   typedef pair <int, int> Map_Int_Pair;

   m1.insert ( Map_Int_Pair ( 1, 10 ) );
   m1.insert ( Map_Int_Pair ( 2, 20 ) );
   m1.insert ( Map_Int_Pair ( 3, 30 ) );

   cout << "The element pairs of the map m1 are:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " ( " << m1_Iter -> first << ", "
           << m1_Iter -> second << " )";
   cout   << "." << endl;

   // Using pair as a return type for a function
   pair< map<int,int>::iterator, bool > pr1, pr2;
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );

   if( pr1.second == true )
   {
      cout << "The element (4,40) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }

   if( pr2.second == true )
   {
      cout << "The element (1,10) was inserted successfully in m1."
           << endl;
   }
   else
   {
      cout << "The element with a key value of\n"
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first
           << " is already in m1,\n so the insertion failed." << endl;
   }
}
```

```Output
The pair p1 is: ( 10, 0.011 ).
The pair p2 is: ( 10, 0.222 ).
The pair p3 is: ( 10, 0.011 ).
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).
The element (4,40) was inserted successfully in m1.
The element with a key value of
( (pr2.first) -> first ) = 1 is already in m1,
so the insertion failed.
```
