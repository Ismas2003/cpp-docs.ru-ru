---
title: Операторы &lt;system_error&gt;
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 8631cae146a311f1890583900b564471d5a80958
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076262"
---
# <a name="ltsystem_errorgt-operators"></a>Операторы &lt;system_error&gt;

## <a name="operator"></a><a name="op_eq_eq"></a>Оператор = =

Проверяет равенство объекта слева от оператора объекту справа от оператора.

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>Параметры

*left*\
Объект для проверки на равенство.

*справа*\
Объект для проверки на равенство.

### <a name="return-value"></a>Возвращаемое значение

Значение **true**, если объекты равны, значение **false**, если объекты не равны.

### <a name="remarks"></a>Примечания

Функция возвращает `left.category() == right.category() && left.value() == right.value()`.

## <a name="operator"></a><a name="op_neq"></a>operator! =

Проверяет неравенство объекта слева от оператора объекту справа от оператора.

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>Параметры

*left*\
Объект для проверки на неравенство.

*справа*\
Объект для проверки на неравенство.

### <a name="return-value"></a>Возвращаемое значение

**значение true** , если переданный объект не равен объекту, переданному по *правому* *краю* ; в противном случае — **false**.

### <a name="remarks"></a>Примечания

Функция возвращает `!(left == right)`.

## <a name="operatorlt"></a><a name="op_lt">Оператор </a>&lt;

Проверяет, меньше ли какой-либо объект переданного для сравнения объекта.

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>Параметры

*left*\
Сравниваемый объект.

*справа*\
Сравниваемый объект.

### <a name="return-value"></a>Возвращаемое значение

**значение true** , если объект, переданный в *левой части* , меньше объекта, переданного *правым*; В противном случае — **значение false**.

### <a name="remarks"></a>Примечания

Эта функция проверяет порядок ошибок.

## <a name="operatorltlt"></a><a name="op_ostream"></a>&lt;оператора &lt;

```cpp
template <class charT, class traits>
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
