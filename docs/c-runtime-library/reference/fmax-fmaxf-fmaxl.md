---
title: fmax, fmaxf, fmaxl
ms.date: 04/05/2018
api_name:
- fmax
- fmaxf
- fmaxl
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 27b495e9344ca7e2e3e061b19fee696ce2bdceb2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957118"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Определяет большее из двух указанных числовых значений.

## <a name="syntax"></a>Синтаксис

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Параметры

*x*<br/>
Первое сравниваемое значение.

*y*<br/>
Второе сравниваемое значение.

## <a name="return-value"></a>Возвращаемое значение

В случае успеха возвращает большее значение *x* или *y*. Возвращает точное значение независимо от формы округления.

В случае неудачи может возвращать одно из следующих значений:

|Проблемы|Назад|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x* и *y* = NaN|NaN|

Эта функция не использует ошибки, указанные в [_matherr](matherr.md).

## <a name="remarks"></a>Примечания

Так как C++ допускает перегрузку, можно вызывать перегрузки функции fmax, принимающие и возвращающие типы значений float и long double. В программе на языке C и fmax всегда принимает и возвращает значение типа double.

## <a name="requirements"></a>Требования

|Функция|Заголовок C|Заголовок C++|
|--------------|--------------|------------------|
|**FMAX**, **fmaxf**, **fmaxl**|\<math.h>|\<cmath> или \<math.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Алфавитный указатель функций](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
