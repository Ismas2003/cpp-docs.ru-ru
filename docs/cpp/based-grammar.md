---
title: Грамматика выражения __based
ms.date: 11/04/2016
helpviewer_keywords:
- based addressing
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
ms.openlocfilehash: 149439c82780f12669e5a3180f975c573ed30422
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181412"
---
# <a name="__based-grammar"></a>Грамматика выражения __based

**Блок, относящийся только к системам Microsoft**

Базовая адресация полезна, когда требуется точный контроль над сегментом, в котором выделяются объекты (статические и динамические данные).

Единственная форма одноадресной адресации в 32-разрядных и 64-разрядных компиляциях — это "основанный на указателе", который определяет тип, который 32 содержит откомпилированное или 64-разрядное смещение к-разрядному или 32-битному основанию или на основе **void**.

## <a name="grammar"></a>Грамматика

*Модификатор на основе диапазона*: **__based (**  *базовое выражение*  **)**

*базовый-Expression*: *на основе вариаблебасед-abstract-деклараторсегмент-намесегмент-CAST*

*переменная на основе*: *идентификатор*

*декларатор на основе абстрактного объявления*: *абстрактное* объявление

*базовый тип*: *имя типа*

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также раздел

[Относительные указатели](../cpp/based-pointers-cpp.md)
