---
title: Прагма section
ms.date: 08/29/2019
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: 47ae2ff2503317e937e2b3a497357afbd5522a64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216597"
---
# <a name="section-pragma"></a>Прагма section

Создает раздел в OBJ-файле.

## <a name="syntax"></a>Синтаксис

> **#pragma раздел (** "*имя раздела*" [ **,** *атрибуты* ] **)**

## <a name="remarks"></a>Примечания

Термины *сегмент* и *раздел* имеют одинаковое значение в этой статье.

После определения раздел остается допустимым для остальной части компиляции. Однако необходимо использовать [__declspec (allocate)](../cpp/allocate.md)или ничего не помещается в раздел.

*section-name* — это обязательный параметр, который становится именем раздела. Имя не должно конфликтовать со стандартными именами раздела. Список имен, которые не следует использовать при создании раздела, см. в разделе [/section](../build/reference/section-specify-section-attributes.md) .

*атрибуты* — это необязательный параметр, состоящий из одного или нескольких атрибутов, разделенных запятыми, для назначения разделу. Возможны следующие *атрибуты* :

|Атрибут|Описание|
|-|-|
|**read**|Позволяет выполнять операции чтения данных.|
|**write**|Позволяет выполнять операции записи данных.|
|**execute**|Позволяет выполнять код.|
|**используемый**|Предоставляет совместный доступ к разделу всем процессам, загружающим образ.|
|**страница**|Помечает раздел как нестраничный. Используется для драйверов устройств Win32.|
|**NoCache**|Помечает раздел как некэшированный. Используется для драйверов устройств Win32.|
|**исключить**|Помечает раздел как отброшенный. Используется для драйверов устройств Win32.|
|**remove**|Помечает раздел как не находящийся в памяти. Только для драйверов виртуальных устройств (V*x*D).|

Если не указать атрибуты, раздел имеет атрибуты **Read** и **Write** .

## <a name="example"></a>Пример

В этом примере первая секция директива pragma определяет раздел и его атрибуты. Целое `j` число не помещается в `mysec` , поскольку оно не `__declspec(allocate)`было объявлено с помощью. Вместо этого `j` переходит в раздел данных. Целое число `i` переходит в `mysec` как результат атрибута класса хранения `__declspec(allocate)`.

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>См. также

[Директивы pragma и ключевое слово __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
