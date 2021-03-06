---
title: Класс collate_byname
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 3e9a256ac7bdb5f6d077746fe2a08990ed41e931
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688275"
---
# <a name="collate_byname-class"></a>Класс collate_byname

Шаблон производного класса, описывающий объект, который может служить в качестве аспекта сортировки для данного языкового стандарта, позволяя получать информацию, относящуюся к правилам сортировки строк в соответствии с культурной областью.

## <a name="syntax"></a>Синтаксис

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>Параметры

*_Locname* \
Именованный языковой стандарт.

*_Refs* \
Начальное значение счетчика ссылок.

## <a name="remarks"></a>Заметки

Шаблон класса описывает объект, который может служить в качестве [аспекта языкового стандарта](../standard-library/locale-class.md#facet_class) для типа [COLLATE](../standard-library/collate-class.md#collate) \<CharType >. Его поведение определяется с помощью [именованного](../standard-library/locale-class.md#name) языкового стандарта *_Locname*. Каждый конструктор инициализирует свой базовый объект с [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`).

## <a name="requirements"></a>Требования

**Заголовок:** \<locale>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
