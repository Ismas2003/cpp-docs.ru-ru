---
title: '&lt;map&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 2e861d2250585fbcdf3e1ef63d92f18185fc7f1c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687780"
---
# <a name="ltmapgt"></a>&lt;map&gt;

Определяет шаблоны классов контейнеров Map и multimap и их вспомогательные шаблоны.

## <a name="requirements"></a>Требования

**Заголовок:** \<map>

**Пространство имен:** std

> [!NOTE]
> Библиотека \<map > также использует инструкцию `#include <initializer_list>`.

## <a name="members"></a>Члены

### <a name="operators"></a>Операторы

|Версия Map|Версия Multimap|Описание|
|-----------------|----------------------|-----------------|
|[operator!= (map)](../standard-library/map-operators.md#op_neq)|[operator!= (multimap)](../standard-library/map-operators.md#op_neq)|Проверяет неравенство объекта map или multimap слева от оператора объекту map или multimap справа от оператора.|
|[оператор< (map)](../standard-library/map-operators.md#op_eq_eq)|[оператор< (multimap)](../standard-library/map-operators.md#op_eq_eq)|Проверяет, меньше ли объект map или multimap слева от оператора объекта map или multimap справа от оператора.|
|[оператор<= (map)](../standard-library/map-operators.md#op_lt)|[оператор\<= (multimap)](../standard-library/map-operators.md#op_lt)|Проверяет, меньше или равен объект map или multimap слева от оператора объекту map или multimap справа от оператора.|
|[оператор== (map)](../standard-library/map-operators.md#op_eq_eq)|[оператор== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Проверяет равенство объекта map или multimap слева от оператора объекту map или multimap справа от оператора.|
|[оператор> (map)](../standard-library/map-operators.md#op_gt)|[оператор> (multimap)](../standard-library/map-operators.md#op_gt_multimap)|Проверяет, больше ли объект map или multimap слева от оператора объекта map или multimap справа от оператора.|
|[оператор>= (map)](../standard-library/map-operators.md#op_gt_eq)|[оператор>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Проверяет, больше или равен объект map или multimap слева от оператора объекту map или multimap справа от оператора.|

### <a name="specialized-template-functions"></a>Специализированные функции шаблонов

|Версия Map|Версия Multimap|Описание|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Обменивает элементы между двумя объектами map или multimap.|

### <a name="classes"></a>Классы

|||
|-|-|
|[Класс value_compare](../standard-library/value-compare-class-map.md)|Предоставляет объект функции, который может сравнить элементы объекта map, сравнивая значения их ключей, чтобы определить их относительный порядок в объекте map.|
|[Класс map](../standard-library/map-class.md)|Используется для хранения и извлечения данных из коллекции, в которой у каждого элемента есть уникальный ключ, по которым данные автоматически упорядочиваются.|
|[Класс multimap](../standard-library/multimap-class.md)|Используется для хранения и извлечения данных из коллекции, в которой у каждого элемента есть ключ, по которым данные автоматически упорядочиваются. При этом значения ключей не обязаны быть уникальными.|

## <a name="see-also"></a>См. также

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)
