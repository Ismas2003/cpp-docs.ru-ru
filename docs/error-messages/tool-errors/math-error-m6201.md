---
title: Математическая ошибка M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 0b1cd0d3fcd86a2174b19da41176dd97f547a295
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193710"
---
# <a name="math-error-m6201"></a>Математическая ошибка M6201

"функция": ошибка _DOMAIN

Аргумент для данной функции находился вне домена допустимых входных значений для этой функции.

## <a name="example"></a>Пример

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Эта ошибка вызывает функцию `_matherr` с именем функции, ее аргументами и типом ошибки. Можно переписать функцию `_matherr`, чтобы настроить обработку определенных математических ошибок с плавающей запятой во время выполнения.
