---
title: Класс basic_ios
ms.date: 11/04/2016
f1_keywords:
- ios/std::basic_ios
- ios/std::basic_ios::char_type
- ios/std::basic_ios::int_type
- ios/std::basic_ios::off_type
- ios/std::basic_ios::pos_type
- ios/std::basic_ios::traits_type
- ios/std::basic_ios::bad
- ios/std::basic_ios::clear
- ios/std::basic_ios::copyfmt
- ios/std::basic_ios::eof
- ios/std::basic_ios::exceptions
- ios/std::basic_ios::fail
- ios/std::basic_ios::fill
- ios/std::basic_ios::good
- ios/std::basic_ios::imbue
- ios/std::basic_ios::init
- ios/std::basic_ios::move
- ios/std::basic_ios::narrow
- ios/std::basic_ios::rdbuf
- ios/std::basic_ios::rdstate
- ios/std::basic_ios::set_rdbuf
- ios/std::basic_ios::setstate
- ios/std::basic_ios::swap
- ios/std::basic_ios::tie
- ios/std::basic_ios::widen
- ios/std::basic_ios::explicit operator bool
helpviewer_keywords:
- std::basic_ios [C++]
- std::basic_ios [C++], char_type
- std::basic_ios [C++], int_type
- std::basic_ios [C++], off_type
- std::basic_ios [C++], pos_type
- std::basic_ios [C++], traits_type
- std::basic_ios [C++], bad
- std::basic_ios [C++], clear
- std::basic_ios [C++], copyfmt
- std::basic_ios [C++], eof
- std::basic_ios [C++], exceptions
- std::basic_ios [C++], fail
- std::basic_ios [C++], fill
- std::basic_ios [C++], good
- std::basic_ios [C++], imbue
- std::basic_ios [C++], init
- std::basic_ios [C++], move
- std::basic_ios [C++], narrow
- std::basic_ios [C++], rdbuf
- std::basic_ios [C++], rdstate
- std::basic_ios [C++], set_rdbuf
- std::basic_ios [C++], setstate
- std::basic_ios [C++], swap
- std::basic_ios [C++], tie
- std::basic_ios [C++], widen
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
ms.openlocfilehash: c8f883dd4f946c03aaa22dffcf5a3164a539d041
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364924"
---
# <a name="basic_ios-class"></a>Класс basic_ios

Шаблон класса описывает функции хранения и члена, общие как для потоков ввода (шаблона класса [basic_istream),](../standard-library/basic-istream-class.md)так и потоков вывода (шаблона класса [basic_ostream),](../standard-library/basic-ostream-class.md)которые зависят от параметров шаблона. (Класс [ios_base](../standard-library/ios-base-class.md) описывает то, что является общим и не зависит от параметров шаблона.) Объект класса **basic_ios\<класса Elem, class Traits>** помогает `Elem`управлять потоком с элементами `Traits`типа, черты характера которых определяются классом.

## <a name="syntax"></a>Синтаксис

```cpp

template <class Elem, class Traits>
class basic_ios : public ios_base
```

### <a name="parameters"></a>Параметры

*Elem*\
Тип.

*Черты*\
Переменная типа `char_traits`.

## <a name="remarks"></a>Remarks

Объект класса **basic_ios\<class Elem, class Traits>** хранит следующее.

- Привязка к объекту типа [basic_istream](../standard-library/basic-istream-class.md)**\<Elem, Traits>. **

- Указатель буфера потока к объекту типа [basic_streambuf](../standard-library/basic-streambuf-class.md)**\<Elem, Traits >. **

- [Сведения о форматировании](../standard-library/ios-base-class.md).

- [Сведения о состоянии потока](../standard-library/ios-base-class.md) в базовом объекте типа [ios_base](../standard-library/ios-base-class.md).

- Символ заполнения в объекте типа `char_type`.

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[basic_ios](#basic_ios)|Создает класс `basic_ios`.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[char_type](#char_type)|Синоним параметра шаблона `Elem`.|
|[int_type](#int_type)|Синоним для `Traits::int_type`.|
|[off_type](#off_type)|Синоним для `Traits::off_type`.|
|[pos_type](#pos_type)|Синоним для `Traits::pos_type`.|
|[traits_type](#traits_type)|Синоним параметра шаблона `Traits`.|

### <a name="member-functions"></a>Функции элементов

|Функция-член|Описание|
|-|-|
|[Плохо](#bad)|Сообщает о потере целостности буфера потока.|
|[Ясно](#clear)|Очищает все флаги ошибок.|
|[copyfmt](#copyfmt)|Копирует флаги из одного потока в другой.|
|[Eof](#eof)|Указывает, достигнут ли конец потока.|
|[Исключения](#exceptions)|Указывает, какие исключения будут создаваться потоком.|
|[Не](#fail)|Сообщает об ошибке при извлечении допустимого поля из потока.|
|[Заполнить](#fill)|Задает или возвращает символ, который будет использоваться, если ширина текста не совпадает с шириной потока.|
|[Хорошо](#good)|Указывает, что поток находится в хорошем состоянии.|
|[imbue](#imbue)|Изменяет языковой стандарт.|
|[Init](#init)|Вызывается конструкторами `basic_ios`.|
|[Переместить](#move)|Перемещает все значения, кроме указателя на буфер потока, из параметра в текущий объект.|
|[narrow](#narrow)|Находит эквивалентный char для данного `char_type`.|
|[rdbuf](#rdbuf)|Направляет поток в указанный буфер.|
|[rdstate](#rdstate)|Считывает состояние битов для флагов.|
|[set_rdbuf](#set_rdbuf)|Назначает буфер потока буфером чтения для этого объекта потока.|
|[setstate](#setstate)|Устанавливает дополнительные флаги.|
|[Своп](#swap)|Меняет местами значения в этом объекте `basic_ios` и значения другого объекта `basic_ios`. Указатели на буферы потока не меняются местами.|
|[tie](#tie)|Гарантирует, что один поток обрабатывается до другого потока.|
|[widen](#widen)|Находит эквивалент `char_type` для указанного char.|

### <a name="operators"></a>Операторы

|Оператор|Описание|
|-|-|
|[explicit operator bool](#op_bool)|Позволяет использовать `basic_ios` объект в качестве **була**. Автоматическое преобразование типов отключено для предотвращения распространенных непредвиденных побочных эффектов.|
|[operator void *](#op_void_star)|Указывает, находится ли поток по-прежнему в хорошем состоянии.|
|[Оператор!](#op_not)|Указывает, не находится ли поток в плохом состоянии.|

## <a name="requirements"></a>Требования

**Заголовок:** \<ios>

**Пространство имен:** std

## <a name="basic_iosbad"></a><a name="bad"></a>basic_ios::плохой

Сообщает о потере целостности буфера потока.

```cpp
bool bad() const;
```

### <a name="return-value"></a>Возвращаемое значение

**верно,** если `rdstate & badbit` является ненулевым; в противном случае **ложные**.

Дополнительные сведения по `badbit` см. в разделе [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Пример

```cpp
// basic_ios_bad.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.bad( );
    cout << boolalpha;
    cout << b << endl;

    b = cout.good( );
    cout << b << endl;
}
```

## <a name="basic_iosbasic_ios"></a><a name="basic_ios"></a>basic_ios::basic_ios

Конструирует класс basic_ios.

```cpp
explicit basic_ios(basic_streambuf<Elem,  Traits>* sb);
basic_ios();
```

### <a name="parameters"></a>Параметры

*Sb*\
Стандартный буфер для хранения элементов ввода или вывода.

### <a name="remarks"></a>Remarks

Первый конструктор инициализирует свой объект-член путем вызова [init](#init)(_ *Sb*). Второй (защищенный) конструктор оставляет свои объекты-члены не инициализированными. Более поздний `init` вызов должен инициализировать объект, прежде чем он может быть безопасно уничтожен.

## <a name="basic_ioschar_type"></a><a name="char_type"></a>basic_ios:char_type

Синоним параметра шаблона `Elem`.

```cpp
typedef Elem char_type;
```

## <a name="basic_iosclear"></a><a name="clear"></a>basic_ios::ясно

Очищает все флаги ошибок.

```cpp
void clear(iostate state = goodbit, bool reraise = false);
void clear(io_state state);
```

### <a name="parameters"></a>Параметры

*Государства*\
(Необязательно) Флаги, которые вы хотите установить после очистки всех флагов. По умолчанию равен `goodbit`.

*перерей*\
(Необязательно) Уточняется, следует ли повторно поднимать исключение. По умолчанию **к ложным** (не будет ререйзировать исключение).

### <a name="remarks"></a>Remarks

Флаги, `goodbit` `failbit` `eofbit`и `badbit`. Проверяет наличие этих флагов с помощью [good](#good), [bad](#bad), [eof](#eof) и [fail](#fail)

Функция-член заменяет сохраненную информацию о состоянии потока на следующее:

`state` &#124; `(`[rdbuf](#rdbuf) != 0 **goodbit** : **badbit**)

Если `state` **&** [исключения](#exceptions) неявляются, он затем бросает объект [сбоя](../standard-library/ios-base-class.md#failure)класса.

### <a name="example"></a>Пример

См [rdstate](#rdstate) и [getline](../standard-library/string-functions.md#getline) для примеров с помощью `clear`.

## <a name="basic_ioscopyfmt"></a><a name="copyfmt"></a>basic_ios::copyfmt

Копирует флаги из одного потока в другой.

```cpp
basic_ios<Elem, Traits>& copyfmt(
const basic_ios<Elem, Traits>& right);
```

### <a name="parameters"></a>Параметры

*Правильно*\
Поток, флаги которого требуется скопировать.

### <a name="return-value"></a>Возвращаемое значение

Объект **this** для потока, в который копируются флаги.

### <a name="remarks"></a>Remarks

Функция участника сообщает о **событии обратного вызова, стирая\_** событие. Затем он копирует ** \*** из *право в* этом заполнить символ, галстук указатель, и информация о форматировании. Перед изменением маски исключения он сообщает `copyfmt_event`о событии обратного вызова. Если после завершения копирования **state & **[exceptions](#exceptions) не равно нулю, функция эффективно вызывает [clear](#clear) с аргументом [rdstate](#rdstate). Он ** \*** возвращает это .

### <a name="example"></a>Пример

```cpp
// basic_ios_copyfmt.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream x( "test.txt" );
    int i = 10;

    x << showpos;
    cout << i << endl;
    cout.copyfmt( x );
    cout << i << endl;
}
```

## <a name="basic_ioseof"></a><a name="eof"></a>basic_ios::eof

Указывает, достигнут ли конец потока.

```cpp
bool eof() const;
```

### <a name="return-value"></a>Возвращаемое значение

**верно,** если конец потока был достигнут, **ложнов** в противном случае.

### <a name="remarks"></a>Remarks

Функция члена возвращается **верно,** если [rdstate](#rdstate) `& eofbit` является ненулевой. Дополнительные сведения по `eofbit` см. в разделе [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Пример

```cpp
// basic_ios_eof.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

int main( int argc, char* argv[] )
{
    fstream   fs;
    int n = 1;
    fs.open( "basic_ios_eof.txt" );   // an empty file
    cout << boolalpha
    cout << fs.eof() << endl;
    fs >> n;   // Read the char in the file
    cout << fs.eof() << endl;
}
```

## <a name="basic_iosexceptions"></a><a name="exceptions"></a>basic_ios::исключения

Указывает, какие исключения будут создаваться потоком.

```cpp
iostate exceptions() const;
void exceptions(iostate Newexcept);
void exceptions(io_state Newexcept);
```

### <a name="parameters"></a>Параметры

*Ньюзаисключение*\
Флаги, которые должны вызывать исключение.

### <a name="return-value"></a>Возвращаемое значение

Флаги, указанные в настоящий момент для создания исключения для потока.

### <a name="remarks"></a>Remarks

Первая функция-член возвращает сохраненную маску исключения. Вторая функция-член сохраняет *_Except* в маске исключения и возвращает предыдущее хранившееся там значение. Обратите внимание, что сохранение новой маски исключения может вызвать исключение так же, как вызов [clear](#clear)( [rdstate](#rdstate) ).

### <a name="example"></a>Пример

```cpp
// basic_ios_exceptions.cpp
// compile with: /EHsc /GR
#include <iostream>

int main( )
{
    using namespace std;

    cout << cout.exceptions( ) << endl;
    cout.exceptions( ios::eofbit );
    cout << cout.exceptions( ) << endl;
    try
    {
        cout.clear( ios::eofbit );   // Force eofbit on
    }
    catch ( exception &e )
    {
        cout.clear( );
        cout << "Caught the exception." << endl;
        cout << "Exception class: " << typeid(e).name()  << endl;
        cout << "Exception description: " << e.what() << endl;
    }
}
```

```Output
0
1
Caught the exception.
Exception class: class std::ios_base::failure
Exception description: ios_base::eofbit set
```

## <a name="basic_iosfail"></a><a name="fail"></a>basic_ios:::fail

Сообщает об ошибке при извлечении допустимого поля из потока.

```cpp
bool fail() const;
```

### <a name="return-value"></a>Возвращаемое значение

**верно,** если [rdstate](#rdstate) `& (badbit|failbit)` является ненулевой, в противном случае **ложным**.

Дополнительные сведения по `failbit` см. в разделе [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Пример

```cpp
// basic_ios_fail.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
    using namespace std;
    bool b = cout.fail( );
    cout << boolalpha;
    cout << b << endl;
}
```

## <a name="basic_iosfill"></a><a name="fill"></a>basic_ios::заполнение

Задает или возвращает символ, который будет использоваться, если ширина текста не совпадает с шириной потока.

```cpp
char_type fill() const;
char_type fill(char_type Char);
```

### <a name="parameters"></a>Параметры

*Char*\
Символ, который нужно использовать в качестве символа заливки.

### <a name="return-value"></a>Возвращаемое значение

Текущий символ заливки.

### <a name="remarks"></a>Remarks

Первая функция-член возвращает сохраненный символ заливки. Функция второго члена хранит *символ заполнения* и возвращает его прежнее сохраненное значение.

### <a name="example"></a>Пример

```cpp
// basic_ios_fill.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( )
{
    using namespace std;

    cout << setw( 5 ) << 'a' << endl;
    cout.fill( 'x' );
    cout << setw( 5 ) << 'a' << endl;
    cout << cout.fill( ) << endl;
}
```

```Output
a
xxxxa
x
```

## <a name="basic_iosgood"></a><a name="good"></a>basic_ios::хорошо

Указывает, что поток находится в хорошем состоянии.

```cpp
bool good() const;
```

### <a name="return-value"></a>Возвращаемое значение

**верно,** если [rdstate](#rdstate) `== goodbit` (не государственные флаги установлены), в противном случае, **ложные**.

Дополнительные сведения по `goodbit` см. в разделе [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

### <a name="example"></a>Пример

Пример использования `good` разделе [basic_ios::bad](#bad).

## <a name="basic_iosimbue"></a><a name="imbue"></a>basic_ios::imbue

Изменяет языковой стандарт.

```cpp
locale imbue(const locale& Loc);
```

### <a name="parameters"></a>Параметры

*Loc*\
Строка языкового стандарта.

### <a name="return-value"></a>Возвращаемое значение

Предыдущий языковой стандарт.

### <a name="remarks"></a>Remarks

Если [rdbuf](#rdbuf) не является пустым указателем, функция-член вызывает

`rdbuf`-> [pubimbue](../standard-library/basic-streambuf-class.md#pubimbue)(_ *Loc*)

В любом случае возвращается [ios_base::imbue](../standard-library/ios-base-class.md#imbue)(_ *Loc*).

### <a name="example"></a>Пример

```cpp
// basic_ios_imbue.cpp
// compile with: /EHsc
#include <iostream>
#include <locale>

int main( )
{
    using namespace std;

    cout.imbue( locale( "french_france" ) );
    double x = 1234567.123456;
    cout << x << endl;
}
```

## <a name="basic_iosinit"></a><a name="init"></a>basic_ios::init

Вызывается конструкторами basic_ios.

```cpp
void init(basic_streambuf<Elem,Traits>* _Sb, bool _Isstd = false);
```

### <a name="parameters"></a>Параметры

*_Sb*\
Стандартный буфер для хранения элементов ввода или вывода.

*_Isstd*\
Указывает, является ли этот поток стандартным.

### <a name="remarks"></a>Remarks

Функция-член сохраняет значения во всех объектах-членах, так что:

- [rdbuf](#rdbuf) возвращает *_Sb*;

- [tie](#tie) возвращает пустой указатель;

- [rdstate](#rdstate) возвращает [goodbit,](../standard-library/ios-base-class.md#iostate) если *_Sb* незеро; в противном случае, он возвращает [Badbit](../standard-library/ios-base-class.md#iostate).

- [исключения](#exceptions) возвращается `goodbit`.

- [flags](../standard-library/ios-base-class.md#flags) возвращает [skipws](../standard-library/ios-base-class.md#fmtflags) &#124; [dec](../standard-library/ios-base-class.md#fmtflags);

- [width](../standard-library/ios-base-class.md#width) возвращает 0;

- [precision](../standard-library/ios-base-class.md#precision) возвращает 6;

- [fill](#fill) возвращает символ пробела;

- [getloc](../standard-library/ios-base-class.md#getloc) возвращает `locale::classic`;

- [iword](../standard-library/ios-base-class.md#iword) возвращает ноль, и [pword](../standard-library/ios-base-class.md#pword) возвращает пустой указатель для всех значений аргумента.

## <a name="basic_iosint_type"></a><a name="int_type"></a>basic_ios::int_type

Синоним для `traits_type::int_type`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_iosmove"></a><a name="move"></a>basic_ios::Move

Перемещает все значения, кроме указателя на буфер потока, из параметра в текущий объект.

```cpp
void move(basic_ios&& right);
```

### <a name="parameters"></a>Параметры

*Правильно*\
Объект `ios_base`, из которого будут перемещаться значения.

### <a name="remarks"></a>Remarks

Защищенная функция члена перемещает все *right* значения, `*this` хранящиеся в праве на, кроме `stream buffer pointer`сохраненных, который не изменяется в *праве* и устанавливается на нулевую указатель в `*this`. Сохраненное `tie pointer` настроено на нулевую указатель в *правой.*

## <a name="basic_iosnarrow"></a><a name="narrow"></a>basic_ios::узкий

Находит эквивалентный char для данного `char_type`.

```cpp
char narrow(char_type Char, char Default = '\0') const;
```

### <a name="parameters"></a>Параметры

*Char*\
**Символ** для преобразования.

*По умолчанию*\
**Символ,** который вы хотите вернуть, если эквивалент не найден.

### <a name="return-value"></a>Возвращаемое значение

Эквивалентный **символ** данного `char_type`.

### <a name="remarks"></a>Remarks

Функция участника [возвращается](../standard-library/basic-filebuf-class.md#open)\<\<use_facet ctype E> > [(getloc](../standard-library/ios-base-class.md#getloc)( ) ). `narrow`( `Char`, `Default`).

### <a name="example"></a>Пример

```cpp
// basic_ios_narrow.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    wchar_t *x = L"test";
    char y[10];
    cout << x[0] << endl;
    wcout << x << endl;
    y[0] = wcout.narrow( x[0] );
    cout << y[0] << endl;
}
```

## <a name="basic_iosoff_type"></a><a name="off_type"></a>basic_ios::off_type

Синоним для `traits_type::off_type`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_iosoperator-void-"></a><a name="op_void_star"></a>basic_ios::оператор недействительным

Указывает, находится ли поток по-прежнему в хорошем состоянии.

```cpp
operator void *() const;
```

### <a name="return-value"></a>Возвращаемое значение

Оператор возвращает пустой указатель только в том случае, если [fail](#fail).

### <a name="example"></a>Пример

```cpp
// basic_ios_opgood.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << (bool)(&cout != 0) << endl;   // Stream is still good
}
```

```Output
1
```

## <a name="basic_iosoperator"></a><a name="op_not"></a>basic_ios::оператор!

Указывает, не находится ли поток в плохом состоянии.

```cpp
bool operator!() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает [fail](#fail).

### <a name="example"></a>Пример

```cpp
// basic_ios_opbad.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << !cout << endl;   // Stream is not bad
}
```

```Output
0
```

## <a name="basic_iosoperator-bool"></a><a name="op_bool"></a>basic_ios::оператор бул

Позволяет использовать `basic_ios` объект в качестве **була**. Автоматическое преобразование типов отключено для предотвращения распространенных непредвиденных побочных эффектов.

```cpp
explicit operator bool() const;
```

### <a name="remarks"></a>Remarks

Оператор возвращает значение кабриолет `fail()`на **ложное** только в том случае, если. Тип возврата кабриолет только для `void *` **bool,** не к или другому известному типу scalar.

## <a name="basic_iospos_type"></a><a name="pos_type"></a>basic_ios::pос-тип

Синоним для `traits_type::pos_type`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_iosrdbuf"></a><a name="rdbuf"></a>basic_ios::rdbuf

Направляет поток в указанный буфер.

```cpp
basic_streambuf<Elem, Traits> *rdbuf() const;
basic_streambuf<Elem, Traits> *rdbuf(
basic_streambuf<Elem, Traits>* _Sb);
```

### <a name="parameters"></a>Параметры

*_Sb*\
Поток.

### <a name="remarks"></a>Remarks

Первая функция-член возвращает сохраненный указатель буфера потока.

Функция второго члена хранит *_Sb* в указатель буфера сохраненного потока и возвращает ранее сохраненное значение.

### <a name="example"></a>Пример

```cpp
// basic_ios_rdbuf.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
    using namespace std;
    ofstream file( "rdbuf.txt" );
    streambuf *x = cout.rdbuf( file.rdbuf( ) );
    cout << "test" << endl;   // Goes to file
    cout.rdbuf(x);
    cout << "test2" << endl;
}
```

```Output
test2
```

## <a name="basic_iosrdstate"></a><a name="rdstate"></a>basic_ios:rdstate

Считывает состояние битов для флагов.

```cpp
iostate rdstate() const;
```

### <a name="return-value"></a>Возвращаемое значение

Сведения о состоянии сохраненного потока.

### <a name="example"></a>Пример

```cpp
// basic_ios_rdstate.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>
using namespace std;

void TestFlags( ios& x )
{
    cout << ( x.rdstate( ) & ios::badbit ) << endl;
    cout << ( x.rdstate( ) & ios::failbit ) << endl;
    cout << ( x.rdstate( ) & ios::eofbit ) << endl;
    cout << endl;
}

int main( )
{
    fstream x( "c:\test.txt", ios::out );
    x.clear( );
    TestFlags( x );
    x.clear( ios::badbit | ios::failbit | ios::eofbit );
    TestFlags( x );
}
```

```Output
0
0
0

4
2
1
```

## <a name="basic_iossetstate"></a><a name="setstate"></a>basic_ios::setstate

Устанавливает дополнительные флаги.

```cpp
void setstate(iostate _State);
```

### <a name="parameters"></a>Параметры

*_state*\
Дополнительные флаги для установки.

### <a name="remarks"></a>Remarks

Эта функция-член эффективно вызывает [clear](#clear)(_ *State* &#124; [rdstate](#rdstate)).

### <a name="example"></a>Пример

```cpp
// basic_ios_setstate.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
using namespace std;

int main( )
{
    bool b = cout.bad( );
    cout << b << endl;   // Good
    cout.clear( ios::badbit );
    b = cout.bad( );
    // cout.clear( );
    cout << b << endl;   // Is bad, good
    b = cout.fail( );
    cout << b << endl;   // Not failed
    cout.setstate( ios::failbit );
    b = cout.fail( );
    cout.clear( );
    cout << b << endl;   // Is failed, good
    return 0;
}
```

```Output
0
1
```

## <a name="basic_iosset_rdbuf"></a><a name="set_rdbuf"></a>basic_ios::set_rdbuf

Назначает буфер потока буфером чтения для этого объекта потока.

```cpp
void set_rdbuf(
basic_streambuf<Elem, Tr>* strbuf)
```

### <a name="parameters"></a>Параметры

*strbuf*\
Буфер потока, который должен стать буфером чтения.

### <a name="remarks"></a>Remarks

Защищенная функция члена хранит *strbuf* в `stream buffer pointer`. Он не `clear`вызывает .

## <a name="basic_iostie"></a><a name="tie"></a>basic_ios::tie

Гарантирует, что один поток обрабатывается до другого потока.

```cpp
basic_ostream<Elem, Traits> *tie() const;
basic_ostream<Elem, Traits> *tie(
basic_ostream<Elem, Traits>* str);
```

### <a name="parameters"></a>Параметры

*Ул*\
Поток.

### <a name="return-value"></a>Возвращаемое значение

Первая функция-член возвращает сохраненный указатель tie. Функция второго члена хранит *стряп* в указателе галстука и возвращает свое предыдущее сохраненное значение.

### <a name="remarks"></a>Remarks

`tie` вызывает синхронизацию двух потоков, так что операции в одном потоке операций происходят после завершения операций в другом потоке.

### <a name="example"></a>Пример

В этом примере путем связывания cin с cout гарантируется, что строка "Enter a number:" будет появляться на консоли перед самим номером, извлекаемым из cin. Это исключает возможность того, что строка "Enter a number:" будет оставаться в буфере при считывании номера, и таким образом мы гарантируем, что пользователь фактически получает некоторый запрос, на который нужно отреагировать. По умолчанию cin и cout связаны.

```cpp
#include <ios>
#include <iostream>

int main( )
{
    using namespace std;
    int i;
    cin.tie( &cout );
    cout << "Enter a number:";
    cin >> i;
}
```

## <a name="basic_iostraits_type"></a><a name="traits_type"></a>basic_ios::traits_type

Синоним параметра шаблона `Traits`.

```cpp
typedef Traits traits_type;
```

## <a name="basic_ioswiden"></a><a name="widen"></a>basic_ios::расширение

Находит эквивалент `char_type` данного **символа**.

```cpp
char_type widen(char Char) const;
```

### <a name="parameters"></a>Параметры

*Char*\
Символ для преобразования.

### <a name="return-value"></a>Возвращаемое значение

Находит эквивалент `char_type` данного **символа**.

### <a name="remarks"></a>Remarks

Функция участника [возвращается use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **E**> > [(getloc).](../standard-library/ios-base-class.md#getloc) `widen`( `Char`).

### <a name="example"></a>Пример

```cpp
// basic_ios_widen.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <wchar.h>

int main( )
{
    using namespace std;
    char *z = "Hello";
    wchar_t y[2] = {0,0};
    cout << z[0] << endl;
    y[0] = wcout.widen( z[0] );
    wcout << &y[0] << endl;
}
```

## <a name="basic_iosswap"></a><a name="swap"></a>basic_ios::swap

Меняет местами значения в этом объекте `basic_ios` и значения другого объекта `basic_ios`. Однако указатели на буферы потока не меняются местами.

```cpp
void swap(basic_ios&& right);
```

### <a name="parameters"></a>Параметры

*Правильно*\
Объект `basic_ios`, используемый для обмена значений.

### <a name="remarks"></a>Remarks

Защищенная функция члена обменивает все значения, `*this` хранящиеся в `stream buffer pointer` *праве,* кроме сохраненных .

## <a name="see-also"></a>См. также раздел

[Безопасность резьбы в стандартной библиотеке СЗ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[программирование йострима](../standard-library/iostream-programming.md)\
[iostreams Конвенций](../standard-library/iostreams-conventions.md)
