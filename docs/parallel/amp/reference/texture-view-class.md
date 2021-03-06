---
title: Класс texture_view
ms.date: 11/04/2016
f1_keywords:
- texture_view
- AMP_GRAPHICS/texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_alpha
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_blue
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_green
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_red
- AMP_GRAPHICS/Concurrency::graphics::texture_view::get
- AMP_GRAPHICS/Concurrency::graphics::texture_view::sample
- AMP_GRAPHICS/Concurrency::graphics::texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::texture_view::value_type
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
ms.openlocfilehash: 6bf4b9666d746199cea92fa2bd52b691c67e4a5b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126356"
---
# <a name="texture_view-class"></a>Класс texture_view

Предоставляет доступ на чтение и запись для текстуры. `texture_view` можно использовать только для чтения текстур, тип значения которых — `int`, `unsigned int`или `float` с 32-битным бпсе по умолчанию. Для чтения других форматов текстуры используйте `texture_view<const value_type, _Rank>`.

## <a name="syntax"></a>Синтаксис

```cpp
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>Параметры

*value_type*<br/>
Тип элементов в агрегате текстуры.

*_Rank*<br/>
Ранг `texture_view`.

## <a name="members"></a>Члены

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Description|
|----------|-----------------|
|`value_type`|Тип элементов в агрегатах текстур.|
|`coordinates_type`|Тип координаты, используемой для указания шаг текселя в `texture_view`, то есть `short_vector` с тем же рангом, что и у связанной текстуры, имеющей тип значения `float`.|
|`gather_return_type`|Тип возвращаемого значения, используемый для операций сбора, то есть ранг 4 `short_vector`, который содержит четыре однородных цветовых компонента, полученных из четырех шаг текселя значений.|

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Description|
|----------|-----------------|
|[Конструктор texture_view](#ctor)|Перегружен. Конструирует экземпляр `texture_view`.|
|[Деструктор ~ texture_view](#ctor)|Уничтожает экземпляр `texture_view`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Description|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Перегружен. Выбирает текстуру с заданными координатами с помощью заданной конфигурации выборки и возвращает альфа-компоненты четырех образцов пикселей текстуры.|
|[gather_blue](#gather_blue)|Перегружен. Выбирает текстуру с заданными координатами с помощью заданной конфигурации выборки и возвращает синие (z) компоненты четырех образцов пикселей текстуры.|
|[gather_green](#gather_green)|Перегружен. Выбирает текстуру с заданными координатами с помощью заданной конфигурации выборки и возвращает зеленые (y) компоненты четырех образцов пикселей текстуры.|
|[gather_red](#gather_red)|Перегружен. Выбирает текстуру с заданными координатами с помощью заданной конфигурации выборки и возвращает красный (x) компоненты четырех образцов пикселей текстуры.|
|[get](#get)|Перегружен. Возвращает значение элемента по индексу.|
|[sample](#sample)|Перегружен. Выбирает текстуру с заданными координатами и уровнем детализации, используя указанную конфигурацию выборки.|
|[set](#set)|Задает значение элемента по индексу.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Description|
|----------|-----------------|
|[operator()](#operator_call)|Перегружен. Возвращает значение элемента по индексу.|
|[operator\[\]](#operator_at)|Перегружен. Возвращает значение элемента по индексу.|
|[оператор=](#operator_eq)|Перегружен. Оператор присвоения.|

### <a name="public-data-members"></a>Открытые члены данных

|Имя|Description|
|----------|-----------------|
|[value_type](#value_type)|Тип значения элементов `texture_view`.|

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`_Texture_base`

`texture_view`

## <a name="requirements"></a>Требования

**Заголовок:** amp_graphics. h

**Пространство имен:** Concurrency:: Graphics

## <a name="dtor"></a>~ texture_view

Уничтожает экземпляр `texture_view`.

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="ctor"></a>texture_view

Конструирует экземпляр `texture_view`.

```cpp
texture_view(// [1] constructor
    texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [2] constructor
    texture<value_type, _Rank>& _Src,
    unsigned int _Mipmap_level = 0) restrict(cpu);

texture_view(// [3] constructor
    const texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [4] constructor
    const texture<value_type, _Rank>& _Src,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);

texture_view(// [5] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [6] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [7] copy constructor
    const texture_view<const value_type, _Rank>& _Other,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);
```

### <a name="parameters"></a>Параметры

*_Src*<br/>
[1, 2] Конструктор `texture`, для которого создается `texture_view` с возможностью записи.

[3, 4] Конструктор `texture`, для которого создается `texture_view`, не поддерживающий запись.

*_Other*<br/>
[5] конструктор копий исходный `texture_view`, доступный для записи.

[6, 7] Конструктор копий исходный `texture_view`, не поддерживающий запись.

*_Mipmap_level*<br/>
Конкретный уровень mipmap на исходном `texture`, к которому привязывается `texture_view` для этой записи. Значение по умолчанию — 0, которое представляет уровень MIP верхнего уровня (самый подробный).

*_Most_detailed_mip*<br/>
Уровень MIP верхнего уровня (самый подробный) для представления относительно указанного объекта `texture_view`.

*_Mip_levels*<br/>
Число уровней mipmap, доступных через `texture_view`.

## <a name="gather_red"></a>gather_red

Выбирает текстуру с заданными координатами с помощью заданной конфигурации выборки и возвращает красный (x) компоненты четырех образцов пикселей текстуры.

```cpp
const gather_return_type gather_red(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_red(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Address_mode*<br/>
Режим адреса, используемый для выборки `texture_view`. Режим адреса одинаков для всех измерений.

*_Sampler*<br/>
Конфигурация образца, используемая для выборки `texture_view`.

*_Coord*<br/>
Координаты, из которых следует брать пример. Значения координат в дробной части используются для интерполяции между примерами пикселей текстуры.

### <a name="return-value"></a>Возвращаемое значение

Короткий вектор ранга, содержащий красный (x) компонент 4 выборочно шаг текселя значений.

## <a name="gather_green"></a>gather_green

Выбирает текстуру с заданными координатами с помощью заданной конфигурации выборки и возвращает зеленые (y) компоненты четырех образцов пикселей текстуры.

```cpp
const gather_return_type gather_green(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_green(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Address_mode*<br/>
Режим адреса, используемый для выборки `texture_view`. Режим адреса одинаков для всех измерений.

*_Sampler*<br/>
Конфигурация образца, используемая для выборки `texture_view`.

*_Coord*<br/>
Координаты, из которых следует брать пример. Значения координат в дробной части используются для интерполяции между примерами пикселей текстуры.

### <a name="return-value"></a>Возвращаемое значение

Короткий вектор ранга, содержащий зеленый компонент (y) из 4 образцов значений шаг текселя.

## <a name="gather_blue"></a>gather_blue

Выбирает текстуру с заданными координатами с помощью заданной конфигурации выборки и возвращает синие (z) компоненты четырех образцов пикселей текстуры.

```cpp
const gather_return_type gather_blue(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_blue(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Address_mode*<br/>
Режим адреса, используемый для выборки `texture_view`. Режим адреса одинаков для всех измерений.

*_Sampler*<br/>
Конфигурация образца, используемая для выборки `texture_view`.

*_Coord*<br/>
Координаты, из которых следует брать пример. Значения координат в дробной части используются для интерполяции между примерами пикселей текстуры.

### <a name="return-value"></a>Возвращаемое значение

Короткий вектор ранга, содержащий красный (x) компонент 4 выборочно шаг текселя значений.

## <a name="gather_alpha"></a>gather_alpha

Выбирает текстуру с заданными координатами с помощью заданной конфигурации выборки и возвращает альфа-компоненты четырех образцов пикселей текстуры.

```cpp
const gather_return_type gather_alpha(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_alpha(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Address_mode*<br/>
Режим адреса, используемый для выборки `texture_view`. Режим адреса одинаков для всех измерений.

*_Sampler*<br/>
Конфигурация образца, используемая для выборки `texture_view`.

*_Coord*<br/>
Координаты, из которых следует брать пример. Значения координат в дробной части используются для интерполяции между примерами пикселей текстуры.

### <a name="return-value"></a>Возвращаемое значение

Короткий вектор ранга, содержащий альфа-компонент (w) из 4 образцов значений шаг текселя.

## <a name="get"></a>Получить

Возвращает значение элемента по указанному индексу.

```cpp
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Index*<br/>
Индекс элемента, который необходимо получить, возможно, многомерный.

*_Mip_level*<br/>
Уровень mipmap, с которого должно быть получено значение. Значение по умолчанию 0 представляет наиболее подробный уровень mipmap.

### <a name="return-value"></a>Возвращаемое значение

Значение элемента.

## <a name="operator_eq"></a>Оператор =

Назначает представление той же текстуры, что и заданный `texture_view`, в данный экземпляр `texture_view`.

```cpp
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Параметры

*_Other*<br/>
[1, 2] Конструктор копирования `texture_view` объект, доступный для записи.

[3] конструктор копий объект `texture_view`, не поддерживающий запись.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на этот экземпляр `texture_view`.

## <a name="operator_at"></a>operator []

Возвращает значение элемента по индексу.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Index*<br/>
Индекс, возможно, многомерный.

*_I0*<br/>
Одномерный индекс.

### <a name="return-value"></a>Возвращаемое значение

Значение элемента, индексируемое `_Index`.

## <a name="operator_call"></a>оператор ()

Возвращает значение элемента по индексу.

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,   int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);

value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

value_type operator() (
    int _I0) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Index*<br/>
Индекс, возможно, многомерный.

*_I0*<br/>
Наиболее важный компонент индекса.

*_I1*<br/>
Компонент индекса "новый", наиболее важный для использования.

*_I2*<br/>
Наименее важный компонент индекса.

### <a name="return-value"></a>Возвращаемое значение

Значение элемента, индексируемое `_Index`.

## <a name="sample"></a>Следующий

Выбирает текстуру с заданными координатами и уровнем детализации, используя указанную конфигурацию выборки.

```cpp
value_type sample(
    const sampler& _Sampler,
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);

template<
    filter_mode _Filter_mode = filter_linear,
    address_mode _Address_mode = address_clamp
>
value_type sample(
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Filter_mode*<br/>
Режим фильтрации, используемый для выборки texture_view. Режим фильтра одинаков для фильтров минимизации, максимизации и mipmap.

*_Address_mode*<br/>
Режим адреса, используемый для выборки texture_view. Режим адреса одинаков для всех измерений.

*_Sampler*<br/>
Конфигурация образца, используемая для выборки texture_view.

*_Coord*<br/>
Координаты, из которых следует брать пример. Значения координат в дробной части используются для интерполяции между значениями шаг текселя.

*_Level_of_detail*<br/>
Значение указывает уровень mipmap для выборки. Дробные значения используются для интерполяции между двумя уровнями mipmap. Уровень детализации по умолчанию — 0, который представляет наиболее подробный уровень MIP.

### <a name="return-value"></a>Возвращаемое значение

Пример значения с интерполяцией.

## <a name="set"></a>параметр

Устанавливает значение элемента по указанному индексу в указанное значение.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Параметры

*_Index*<br/>
Индекс элемента, который необходимо задать, возможно многомерный.

*value*<br/>
Значение, которое необходимо присвоить элементу.

## <a name="value_type"></a>value_type

Тип значения элементов texture_view.

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>См. также раздел

[Пространство имен Concurrency::graphics](concurrency-graphics-namespace.md)
