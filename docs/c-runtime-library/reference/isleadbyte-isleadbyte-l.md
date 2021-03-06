---
title: isleadbyte, _isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: 078efc2fa5499e23ce7f2fb6f8fc0ffc5123de1e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909545"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Определяет, является ли символ начальным байтом многобайтового символа.

> [!IMPORTANT]
> Этот API нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Параметры

*ц*<br/>
Проверяемое целое число.

## <a name="return-value"></a>Возвращаемое значение

**ислеадбите** возвращает ненулевое значение, если аргумент удовлетворяет условию теста, или 0, если нет. В языковых стандартах "C" и в национальных кодировках однобайтовых кодировок (SBCS) **ислеадбите** всегда возвращает 0.

## <a name="remarks"></a>Remarks

Макрос **ислеадбите** возвращает ненулевое значение, если его аргумент является первым байтом многобайтового символа. **ислеадбите** дает значимый результат для любого целочисленного аргумента от-1 (**EOF**) до **UCHAR_MAX** (0xFF) включительно.

Ожидаемый тип аргумента для **ислеадбите** — **int**; Если передается знак подписывания, компилятор может преобразовать его в целое число по расширению знака, что приведет к непредсказуемым результатам.

Версия этой функции с суффиксом **_l** идентична за исключением того, что использует переданный языковой стандарт вместо текущего языкового стандарта для поведения, зависящего от языкового стандарта.

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Всегда возвращает значение false|**_isleadbyte**|Всегда возвращает значение false|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также раздел

[Классификация байтов](../../c-runtime-library/byte-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[подпрограммы _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
