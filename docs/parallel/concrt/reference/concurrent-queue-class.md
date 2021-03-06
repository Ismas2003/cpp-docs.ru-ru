---
title: Класс concurrent_queue
ms.date: 11/04/2016
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: 4e913af40b2218da5699da2659ec2e9189e32994
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143206"
---
# <a name="concurrent_queue-class"></a>Класс concurrent_queue

Класс `concurrent_queue` представляет собой класс контейнера последовательности, обеспечивающий доступ к элементам в порядке поступления. Он позволяет использовать ограниченный набор параллельно-безопасных операций, таких как `push` и `try_pop`. В данном случае, безопасность с параллелизмом означает, что указатели или итераторы всегда действительны. Не гарантируется инициализация элементов или определенный порядок обхода.

## <a name="syntax"></a>Синтаксис

```cpp
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

### <a name="parameters"></a>Параметры

*T*<br/>
Тип данных элементов, которые должны храниться в очереди.

*_Ax*<br/>
Тип, представляющий сохраненный объект распределителя, который инкапсулирует сведения о выделении и освобождении памяти для этой параллельной очереди. Этот аргумент является необязательным, и значением по умолчанию является `allocator<T>`.

## <a name="members"></a>Члены

### <a name="public-typedefs"></a>Общедоступные определения типов

|Имя|Description|
|----------|-----------------|
|`allocator_type`|Тип, представляющий класс распределителя для параллельной очереди.|
|`const_iterator`|Тип, представляющий не потокобезопасный `const` итератор по элементам в параллельной очереди.|
|`const_reference`|Тип, предоставляющий ссылку на элемент `const`, хранящийся в параллельной очереди для чтения и выполнения операций `const`.|
|`difference_type`|Тип, предоставляющий расстояние со знаком между двумя элементами в параллельной очереди.|
|`iterator`|Тип, представляющий не потокобезопасный итератор по элементам в параллельной очереди.|
|`reference`|Тип, предоставляющий ссылку на элемент, хранящийся в параллельной очереди.|
|`size_type`|Тип, подсчитывающий количество элементов в параллельной очереди.|
|`value_type`|Тип, представляющий тип данных, хранящихся в параллельной очереди.|

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Description|
|----------|-----------------|
|[concurrent_queue](#ctor)|Перегружен. Конструирует параллельную очередь.|
|[Деструктор ~ concurrent_queue](#dtor)|Уничтожает параллельную очередь.|

### <a name="public-methods"></a>Открытые методы

|Имя|Description|
|----------|-----------------|
|[пусто](#clear)|Очищает параллельную очередь, уничтожая все текущие элементы, поставленные в очередь. Этот метод не является типобезопасным в режиме параллелизма.|
|[empty](#empty)|Проверяет, пуста ли параллельная очередь в момент вызова этого метода. Этот метод является типобезопасным в режиме параллелизма.|
|[get_allocator](#get_allocator)|Возвращает копию распределителя, используемую для создания параллельной очереди. Этот метод является типобезопасным в режиме параллелизма.|
|[push](#push)|Перегружен. Ставит в очередь элемент в конце параллельной очереди. Этот метод является типобезопасным в режиме параллелизма.|
|[try_pop](#try_pop)|Удаляет элемент из очереди, если он доступен. Этот метод является типобезопасным в режиме параллелизма.|
|[unsafe_begin](#unsafe_begin)|Перегружен. Возвращает итератор типа `iterator` или `const_iterator` в начало параллельной очереди. Этот метод не является типобезопасным в режиме параллелизма.|
|[unsafe_end](#unsafe_end)|Перегружен. Возвращает итератор типа `iterator` или `const_iterator` в конец параллельной очереди. Этот метод не является типобезопасным в режиме параллелизма.|
|[unsafe_size](#unsafe_size)|Возвращает количество элементов в очереди. Этот метод не является типобезопасным в режиме параллелизма.|

## <a name="remarks"></a>Remarks

Дополнительные сведения см. в разделе [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`concurrent_queue`

## <a name="requirements"></a>Требования

**Заголовок:** concurrent_queue. h

**Пространство имен:** concurrency

## <a name="clear"></a>открытым

Очищает параллельную очередь, уничтожая все текущие элементы, поставленные в очередь. Этот метод не является типобезопасным в режиме параллелизма.

```cpp
void clear();
```

## <a name="ctor"></a>concurrent_queue

Конструирует параллельную очередь.

```cpp
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>Параметры

*_InputIterator*<br/>
Тип итератора ввода, который задает диапазон значений.

*_Al*<br/>
Класс распределителя для использования с данным объектом.

*_OtherQ*<br/>
Исходный объект `concurrent_queue` для копирования или перемещения элементов.

*_Begin*<br/>
Положение первого элемента в диапазоне копируемых элементов.

*_End*<br/>
Положение первого элемента за пределами диапазона копируемых элементов.

### <a name="remarks"></a>Remarks

Все конструкторы хранят объект распределителя `_Al` и инициализируют очередь.

Первый конструктор указывает пустую исходную очередь и явно указывает тип распределителя для использования.

Второй конструктор указывает копию параллельной очереди `_OtherQ`.

Третий конструктор задает перемещение параллельной очереди `_OtherQ`.

Четвертый конструктор указывает значения, предоставляемые диапазоном итератора [`_Begin`, `_End`).

## <a name="dtor"></a>~ concurrent_queue

Уничтожает параллельную очередь.

```cpp
~concurrent_queue();
```

## <a name="empty"></a>указано

Проверяет, пуста ли параллельная очередь в момент вызова этого метода. Этот метод является типобезопасным в режиме параллелизма.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Возвращаемое значение

**значение true** , если параллельная очередь была пуста в момент, когда мы искали, и **false** в противном случае.

### <a name="remarks"></a>Remarks

Хотя этот метод является типобезопасным по отношению к вызовам методов `push`, `try_pop`и `empty`, возвращаемое значение может быть неправильным на момент проверки вызывающим потоком.

## <a name="get_allocator"></a>get_allocator

Возвращает копию распределителя, используемую для создания параллельной очереди. Этот метод является типобезопасным в режиме параллелизма.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Возвращаемое значение

Копия распределителя, используемая для создания параллельной очереди.

## <a name="push"></a>распространение

Ставит в очередь элемент в конце параллельной очереди. Этот метод является типобезопасным в режиме параллелизма.

```cpp
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>Параметры

*_Src*<br/>
Элемент, добавляемый в очередь.

### <a name="remarks"></a>Remarks

`push` является типобезопасным по отношению к вызовам методов `push`, `try_pop`и `empty`.

## <a name="try_pop"></a>try_pop

Удаляет элемент из очереди, если он доступен. Этот метод является типобезопасным в режиме параллелизма.

```cpp
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>Параметры

*_Dest*<br/>
Ссылка на расположение для хранения элемента, находящихся в очереди.

### <a name="return-value"></a>Возвращаемое значение

**значение true** , если элемент был успешно удален из очереди; в противном случае — **значение false** .

### <a name="remarks"></a>Remarks

Если элемент был успешно удален из очереди, параметр `_Dest` получает значение из очереди, исходное значение, удерживаемое в очереди, уничтожается, а эта функция возвращает **значение true**. Если элемент для вывода из очереди отсутствует, эта функция возвращает `false` без блокировки, а содержимое параметра `_Dest` не определено.

`try_pop` является типобезопасным по отношению к вызовам методов `push`, `try_pop`и `empty`.

## <a name="unsafe_begin"></a>unsafe_begin

Возвращает итератор типа `iterator` или `const_iterator` в начало параллельной очереди. Этот метод не является типобезопасным в режиме параллелизма.

```cpp
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Итератор типа `iterator` или `const_iterator` в начало объекта параллельной очереди.

### <a name="remarks"></a>Remarks

Итераторы для класса `concurrent_queue` в основном предназначены для отладки, так как они выполняются слишком долго, а итерация не является надежной по отношению к другим операциям очереди.

## <a name="unsafe_end"></a>unsafe_end

Возвращает итератор типа `iterator` или `const_iterator` в конец параллельной очереди. Этот метод не является типобезопасным в режиме параллелизма.

```cpp
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>Возвращаемое значение

Итератор типа `iterator` или `const_iterator` в конец параллельной очереди.

### <a name="remarks"></a>Remarks

Итераторы для класса `concurrent_queue` в основном предназначены для отладки, так как они выполняются слишком долго, а итерация не является надежной по отношению к другим операциям очереди.

## <a name="unsafe_size"></a>unsafe_size

Возвращает количество элементов в очереди. Этот метод не является типобезопасным в режиме параллелизма.

```cpp
size_type unsafe_size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Размер параллельной очереди.

### <a name="remarks"></a>Remarks

`unsafe_size` не является типобезопасным и может давать неверные результаты, если вызывается параллельно с вызовами методов `push`, `try_pop`и `empty`.

## <a name="see-also"></a>См. также раздел

[Пространство имен concurrency](concurrency-namespace.md)
