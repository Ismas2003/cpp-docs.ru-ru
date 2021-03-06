---
title: Класс match_results
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 31154a38f8bbcb879fd871f1eb1bf5a4b15af79b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371021"
---
# <a name="match_results-class"></a>Класс match_results

Содержит последовательность подстрок соответствия.

## <a name="syntax"></a>Синтаксис

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Параметры

*BidIt*\
Тип итератора для подстрок соответствия.

*Alloc*\
Тип распределителя для управления хранилищем.

## <a name="remarks"></a>Remarks

Шаблон класса описывает объект, который управляет неизменяемой `sub_match<BidIt>` последовательностью элементов типа, генерируемых регулярным поиском выражения. Каждый элемент указывает на часть последовательности, которая соответствует группе захвата, соответствующей этому элементу.

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[match_results](#match_results)|Создает объект.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[allocator_type](#allocator_type)|Тип распределителя для управления хранилищем.|
|[char_type](#char_type)|Тип элемента.|
|[const_iterator](#const_iterator)|Тип постоянного итератора для подстрок соответствия.|
|[const_reference](#const_reference)|Тип постоянной ссылки на элемент.|
|[difference_type](#difference_type)|Тип разницы итератора.|
|[Итератор](#iterator)|Тип итератора для подстрок соответствия.|
|[Ссылки](#reference)|Тип ссылки на элемент.|
|[size_type](#size_type)|Тип числа подстрок соответствия.|
|[string_type](#string_type)|Тип строки.|
|[Value_type](#value_type)|Тип подстроки соответствия.|

### <a name="member-functions"></a>Функции элементов

|Функция-член|Описание|
|-|-|
|[Начать](#begin)|Обозначает начало последовательности подстроки соответствия.|
|[Пустой](#empty)|Проверяет отсутствие подстрок соответствия.|
|[end](#end)|Обозначает конец последовательности частичного соответствия.|
|[Формат](#format)|Форматирует подстроки соответствия.|
|[get_allocator](#get_allocator)|Возвращает сохраненный распределитель.|
|[длина](#length)|Возвращает длину подстроки соответствия.|
|[max_size](#max_size)|Получает максимальное число подстрок соответствия.|
|[Позиции](#position)|Получает начальное смещение подгруппы.|
|[prefix](#prefix)|Получает последовательность перед первой подстрокой соответствия.|
|[Размер](#size)|Подсчитывает количество подстрок соответствия.|
|[Ул](#str)|Возвращает подстроку совпадения.|
|[suffix](#suffix)|Получает последовательность после последней подстроки соответствия.|
|[Своп](#swap)|Меняет местами два объекта match_results.|

### <a name="operators"></a>Операторы

|Оператор|Описание|
|-|-|
|[оператора](#op_eq)|Копирование объекта match_results.|
|[Оператор\[\]](#op_at)|Доступ к подчиненному объекту.|

## <a name="requirements"></a>Требования

**Заголовок:** \<regex>

**Пространство имен:** std

## <a name="example"></a>Пример

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="match_resultsallocator_type"></a><a name="allocator_type"></a>match_results::allocator_type

Тип распределителя для управления хранилищем.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Remarks

Typedef является синонимом шаблона аргумент *Alloc*.

## <a name="match_resultsbegin"></a><a name="begin"></a>match_results::начало

Обозначает начало последовательности подстроки соответствия.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает итератор произвольного доступа, указывающий на первый элемент последовательности (или на место сразу за концом пустой последовательности).

## <a name="match_resultschar_type"></a><a name="char_type"></a>match_results::char_type

Тип элемента.

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Remarks

Определение типа является синонимом типа `iterator_traits<BidIt>::value_type`, который является типом элемента искомой последовательности символов.

## <a name="match_resultsconst_iterator"></a><a name="const_iterator"></a>match_results::const_iterator

Тип постоянного итератора для подстрок соответствия.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Remarks

Определение типа описывает объект, который можно использовать в качестве постоянного итератора с произвольным доступом для управляемой последовательности.

## <a name="match_resultsconst_reference"></a><a name="const_reference"></a>match_results::const_reference

Тип постоянной ссылки на элемент.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Remarks

Определение типа описывает объект, который можно использовать в качестве постоянной ссылки на элемент управляемой последовательности.

## <a name="match_resultsdifference_type"></a><a name="difference_type"></a>match_results::difference

Тип разницы итератора.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Remarks

Определение типа является синонимом типа `iterator_traits<BidIt>::difference_type`; оно описывает объект, который может представлять разницу между любыми двумя итераторами, указывающими на элементы управляемой последовательности.

## <a name="match_resultsempty"></a><a name="empty"></a>match_results::пустой

Проверяет отсутствие подстрок соответствия.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает значение true, только если не удалось найти регулярное выражение.

## <a name="match_resultsend"></a><a name="end"></a>match_results::end

Обозначает конец последовательности частичного соответствия.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает итератор, указывающий на место сразу за концом последовательности.

## <a name="match_resultsformat"></a><a name="format"></a>match_results:формат

Форматирует подстроки соответствия.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Параметры

*OutIt*\
Тип итератора вывода.

*из*\
Поток вывода для записи.

*Fmt*\
Строка форматирования.

*Флаги*\
Флаги формата.

### <a name="remarks"></a>Remarks

Каждая функция участника генерирует отформатированный текст под контролем формата *fmt*. Функция первого члена записывает отформатированный текст *out* к последовательности, определенной его аргументом, и *возвращается.* Функция второго члена возвращает объект строки, держащий копию отформатируемого текста.

Чтобы создать форматированный текст, литеральный текст в строке формата, как правило, копируется в целевую последовательность. Каждая escape-последовательность в строке формата заменяется текстом, который она представляет. Сведениями о копировании и замене управляют флаги формата, передаваемые функции.

## <a name="match_resultsget_allocator"></a><a name="get_allocator"></a>match_results::get_allocator

Возвращает сохраненный распределитель.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает копию объекта распределителя, используемого `*this` для распределения его объектов `sub_match`.

## <a name="match_resultsiterator"></a><a name="iterator"></a>match_results::iterator

Тип итератора для подстрок соответствия.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Remarks

Этот тип описывает объект, который можно использовать в качестве итератора с произвольным доступом для управляемой последовательности.

## <a name="match_resultslength"></a><a name="length"></a>match_results::длина

Возвращает длину подстроки соответствия.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Параметры

*Sub*\
Индекс подстроки соответствия.

### <a name="remarks"></a>Remarks

Функция-член возвращает значение `(*this)[sub].length()`.

## <a name="match_resultsmatch_results"></a><a name="match_results"></a>match_results::match_results

Создает объект.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Параметры

*Alloc*\
Объект распределителя для сохранения.

*Правильно*\
Копируемый объект match_results.

### <a name="remarks"></a>Remarks

Первый конструктор создает объект `match_results`, который не содержит подстрок совпадения. Второй конструктор строит `match_results` объект, который является копией *права.*

## <a name="match_resultsmax_size"></a><a name="max_size"></a>match_results::max_size

Получает максимальное число подстрок соответствия.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает длину самой длинной последовательности, которой объект может управлять.

## <a name="match_resultsoperator"></a><a name="op_eq"></a>match_results:оператор

Копирование объекта match_results.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Параметры

*Правильно*\
Копируемый объект match_results.

### <a name="remarks"></a>Remarks

Оператор-член заменяет последовательность, управляемую `*this` копией последовательности, контролируемой *правом.*

## <a name="match_resultsoperator"></a><a name="op_at"></a>match_results:оператор

Доступ к подчиненному объекту.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Параметры

*N*\
Индекс подстроки совпадения.

### <a name="remarks"></a>Remarks

Функция члена возвращает ссылку на элемент *n* контролируемой последовательности `sub_match` или `size() <= n` ссылку на пустой объект, если группа захвата *n* не была частью совпадения.

## <a name="match_resultsposition"></a><a name="position"></a>match_results::pоси

Получает начальное смещение подгруппы.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Параметры

*Sub*\
Индекс подстроки совпадения.

### <a name="remarks"></a>Remarks

Функция-член возвращает `std::distance(prefix().first, (*this)[sub].first)`, то есть расстояние от первого символа в целевой последовательности до первого символа в подстроке соответствия, указанной элементом `n` управляемой последовательности.

## <a name="match_resultsprefix"></a><a name="prefix"></a>match_results::prefix

Получает последовательность перед первой подстрокой соответствия.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает ссылку на объект типа `sub_match<BidIt>` , указывающий на последовательность символов, которая начинается с начала целевой последовательности и заканчивается в `(*this)[0].first`, то есть он указывает на текст, который предшествует сопоставленной части последовательности.

## <a name="match_resultsreference"></a><a name="reference"></a>match_results::ссылка

Тип ссылки на элемент.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Remarks

Тип является синонимом для типа `const_reference`.

## <a name="match_resultssize"></a><a name="size"></a>match_results:размер

Подсчитывает количество подстрок соответствия.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает число, которое на единицу больше, чем количество групп записи в регулярном выражении, использовавшемся для поиска, или значение 0, если поиск не выполнялся.

## <a name="match_resultssize_type"></a><a name="size_type"></a>match_results::size_type

Тип числа подстрок соответствия.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Remarks

Тип является синонимом для типа `Alloc::size_type`.

## <a name="match_resultsstr"></a><a name="str"></a>match_results::str

Возвращает подстроку совпадения.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Параметры

*Sub*\
Индекс подстроки совпадения.

### <a name="remarks"></a>Remarks

Функция-член возвращает значение `string_type((*this)[sub])`.

## <a name="match_resultsstring_type"></a><a name="string_type"></a>match_results:::string_type

Тип строки.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Remarks

Тип является синонимом для типа `basic_string<char_type>`.

## <a name="match_resultssuffix"></a><a name="suffix"></a>match_results::суффикс

Получает последовательность после последней подстроки соответствия.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Remarks

Функция-член возвращает ссылку на объект типа `sub_match<BidIt>` , указывающий на последовательность символов, которая начинается с `(*this)[size() - 1].second` и заканчивается в конце целевой последовательности, то есть он указывает на текст, который следует за сопоставленной частью последовательности.

## <a name="match_resultsswap"></a><a name="swap"></a>match_results::swap

Меняет местами два объекта match_results.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Параметры

*Правильно*\
Объект match_results для замены.

### <a name="remarks"></a>Remarks

Функция члена меняет содержимое `*this` и *справа* в постоянное время и не бросает исключений.

## <a name="match_resultsvalue_type"></a><a name="value_type"></a>match_results::value_type

Тип подстроки соответствия.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Remarks

Определение типа является синонимом для типа `sub_match<BidIt>`.

## <a name="see-also"></a>См. также раздел

[\<regex>](../standard-library/regex.md)
