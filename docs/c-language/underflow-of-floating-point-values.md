---
title: Потеря точности значений с плавающей запятой
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344065"
---
# <a name="underflow-of-floating-point-values"></a>Потеря точности значений с плавающей запятой

**ANSI 4.5.1** Задают ли математические функции значение макроса `ERANGE` для целочисленного выражения `errno` при ошибках потери значимости

При потере точности числа с плавающей запятой выражение `errno` не получает значения `ERANGE`. Если значение стремится к нулю и, наконец, теряет значимость, значение устанавливается равным 0.

## <a name="see-also"></a>См. также

[Функции библиотеки](../c-language/library-functions.md)
