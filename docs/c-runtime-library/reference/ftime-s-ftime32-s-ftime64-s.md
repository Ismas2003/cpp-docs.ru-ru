---
title: _ftime_s, _ftime32_s, _ftime64_s
ms.date: 4/2/2020
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
- _o__ftime32_s
- _o__ftime64_s
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
ms.openlocfilehash: a77d149f367c7f565141fbc3be1db1bfc3f3f362
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909952"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s, _ftime32_s, _ftime64_s

Получает текущее время. Это версии функций [_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md) с усовершенствованной безопасностью, как описано в разделе [Усовершенствования безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>Параметры

*timeptr*<br/>
Указатель на структуру **_timeb**, **__timeb32**или **__timeb64** .

## <a name="return-value"></a>Возвращаемое значение

Нуль в случае успеха или код ошибки в случае неудачи. Если *timeptr* имеет значение **null**, возвращается значение **еинвал**.

## <a name="remarks"></a>Remarks

Функция **_ftime_s** возвращает текущее местное время и сохраняет его в структуре, на которую указывает *timeptr*. Структуры **_timeb**, **__timeb32**и **__timeb64** определены в файле sys\timeb.h. Они содержат четыре поля, которые описываются в следующей таблице.

|Поле|Описание|
|-|-|
|**дстфлаг**|Ненулевое значение, если для местного часового пояса в данный момент действует летнее время. (Описание принципов определения летнего времени см. в разделе [_tzset](tzset.md).)|
|**миллитм**|Доля секунды в миллисекундах.|
|**time**|Время представляется в виде числа секунд, истекших после полуночи (00:00:00) 1 января 1970 года, время в формате UTC.|
|**стандарт**|Разница в минутах между временем UTC и местным временем при движении в западном направлении. Значение **часового пояса** задается на основе значения глобальной переменной **_timezone** (см. **_tzset**).|

Функция **_ftime64_s** , использующая структуру **__timeb64** , позволяет выражать даты создания файлов до 23:59:59, 31 декабря 3000, UTC; в то время как **_ftime32_s** представляет только даты до 23:59:59 января 2038 года, в формате UTC. Полночь 1 января 1970 года — нижняя граница диапазона дат для всех этих функций.

Функция **_ftime_s** эквивалентна **_ftime64_s**, а **_timeb** содержит 64-разрядное время, если только не определен **_USE_32BIT_TIME_T** , в этом случае действует старое поведение. **_ftime_s** использует 32-разрядное время, а **_timeb** содержит 32-бит времени.

**_ftime_s** проверяет свои параметры. Если в качестве *timeptr*передается пустой указатель, функция вызывает обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, **функция устанавливает значение** по **еинвал**.

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> и \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> и \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> и \<sys/timeb.h>|

Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Все версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Пример

```C
// crt_ftime64_s.c
// This program uses _ftime64_s to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime64_s( &timebuffer );

    time1 = timebuffer.time;
    millitm1 = timebuffer.millitm;
    timezone1 = timebuffer.timezone;
    dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>См. также раздел

[Операции управления временем](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
