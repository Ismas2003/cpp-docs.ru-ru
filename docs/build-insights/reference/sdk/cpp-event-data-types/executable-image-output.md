---
title: ИсполняемыйКлассImageOutput
description: Ссылка на класс SDK Build Insights SDK ExecutableImageOutput.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExecutableImageOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 834689a3605b729260f2d4c925396ee1af1bb705
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324945"
---
# <a name="executableimageoutput-class"></a>ИсполняемыйКлассImageOutput

::: moniker range="<=vs-2015"

SDK Build Insights совместим с Visual Studio 2017 и выше. Чтобы увидеть документацию для этих версий, установите элемент управления **селектора** визуальной версии для этой статьи на Visual Studio 2017 или Visual Studio 2019. Он находится в верхней части таблицы содержимого на этой странице.

::: moniker-end
::: moniker range=">=vs-2017"

Класс `ExecutableImageOutput` используется с функциями [MatchEvent,](../functions/match-event.md) [MatchEventInMemberFunction,](../functions/match-event-in-member-function.md) [MatchEventStack](../functions/match-event-stack.md)и [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Используйте его для EXECUTABLE_IMAGE_OUTPUT [события.](../event-table.md#executable-image-output)

## <a name="syntax"></a>Синтаксис

```cpp
class ExecutableImageOutput : public FileOutput
{
public:
    ExecutableImageOutput(const RawEvent& event);
};
```

## <a name="members"></a>Участники

Наряду с унаследованных членов из `ExecutableImageOutput` своего базового класса [FileOutput,](file-output.md) класс содержит следующие члены:

### <a name="constructors"></a>Конструкторы

[ИсполняемыйИзображениеВыход](#executable-image-output)

## <a name="executableimageoutput"></a><a name="executable-image-output"></a>ИсполняемыйИзображениеВыход

```cpp
ExecutableImageOutput(const RawEvent& event);
```

### <a name="parameters"></a>Параметры

*Событие*\
[Событие EXECUTABLE_IMAGE_OUTPUT.](../event-table.md#executable-image-output)

::: moniker-end
