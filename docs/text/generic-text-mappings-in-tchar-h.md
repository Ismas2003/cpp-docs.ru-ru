---
title: Универсальные текстовые сопоставления в файле tchar.h
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: bf872df2e6fb49e64a973e8799eef98dec1cb472
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361342"
---
# <a name="generic-text-mappings-in-tcharh"></a>Универсальные текстовые сопоставления в файле tchar.h

Чтобы упростить транспортировку кода для международного использования, библиотека времени выполнения Майкрософт предоставляет специальные отображения общего текста корпорации Майкрософт для многих типов данных, процедур и других объектов. Эти отображения, определяемые в tchar.h, можно использовать для записи, которая может быть составлена для наборов символов с одним `#define` байтом, мультибайтом или Unicode, в зависимости от явной константы, которую вы определяете с помощью оператора. Универсальные текстовые сопоставления представляют собой расширения Microsoft, несовместимые со стандартами ANSI.

Используя приложения tchar.h, можно создавать приложения с одним байтом, Multibyte Character Set (MBCS) и Unicode из одних и тех же источников. tchar.h определяет макросы (которые `_tcs`имеют префикс), что, с правильными определениями предварительного процессора, `str`карта, `_mbs`или `wcs` функции, по мере необходимости. Чтобы построить MBCS, `_MBCS`определите символ. Чтобы построить Unicode, `_UNICODE`определите символ. Чтобы создать однобайное приложение, определите ни одно из них (по умолчанию). По умолчанию `_UNICODE` определяется для приложений MFC.

Тип `_TCHAR` данных определяется условно в tchar.h. Если символ `_UNICODE` определен для сборки, `_TCHAR` определяется как **wchar_t;** в противном случае, для однобайных и MBCS строит, он определяется как **символ**. **(wchar_t**, основной тип данных Unicode широкого характера, является 16-битным аналогом 8-битного подписанного **символа**.) Для международных приложений `_tcs` используйте семейство `_TCHAR` функций, которые действуют в единицах, а не байтах. Например, `_tcsncpy` `n` `_TCHARs`копии, `n` а не байты.

Поскольку некоторые функции одноразового набора символов Байт `char*` (SBCS) принимают (подписанные) параметры, результаты предупреждения о несоответствии компилятора типа, когда `_MBCS` они определены. Есть три способа избежать этого предупреждения:

1. Используйте тип-безопасный вонлайн функции thunks в tchar.h. Это поведение установлено по умолчанию.

1. Используйте прямые макросы в `_MB_MAP_DIRECT` tchar.h, определяя на командной строке. После этого необходимо сопоставить типы вручную. Это самый быстрый метод, но не является безопасным для типа.

1. Используйте тип-безопасной статически связанной функции библиотеки thunks в tchar.h. Для этого необходимо определить константу `_NO_INLINING` в командной строке. Это самый медленный и в то же время самый типобезопасный способ.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Директивы препроцессора для универсальных текстовых сопоставлений

|Определить - определить|Скомпилированная версия|Пример|
|---------------|----------------------|-------------|
|`_UNICODE`|Юникод (расширенные символы)|`_tcsrev` сопоставляется с `_wcsrev`|
|`_MBCS`|Многобайтовые символы|`_tcsrev` сопоставляется с `_mbsrev`|
|Нет (по умолчанию `_MBCS` не имеет ни `_UNICODE` определены)|Однобайтовая кодировка (ASCII)|`_tcsrev` сопоставляется с `strrev`|

Например, функция `_tcsrev`общего текста, которая определена в tchar.h, карты, `_mbsrev` если вы определили `_MBCS` в вашей программе, или если `_wcsrev` вы определили `_UNICODE`. В противном случае `_tcsrev` сопоставляется с `strrev`. Другие отображения типов данных предоставляются в `_TCHAR` tchar.h для удобства программирования, но являются наиболее полезными.

### <a name="generic-text-data-type-mappings"></a>Сопоставления типов данных универсального текста

|Общий текст<br /> Имя типа данных|_UNICODE &<br /> _MBCS не определено|_MBCS<br /> Определено|_UNICODE<br /> Определено|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**INT**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**signed char**|**signed char**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` или `_TEXT`|Не действует (удаляется препроцессором)|Не действует (удаляется препроцессором)|`L`(преобразует следующий символ или строку в его аналог Unicode)|

Для списка общих текстовых карт процедур, переменных и других [Generic-Text Mappings](../c-runtime-library/generic-text-mappings.md) объектов см.

> [!NOTE]
> Не используйте `str` семейство функций со строками Unicode, которые, вероятно, содержат встроенные нулевые байты. Аналогичным образом, не `wcs` используйте семейство функций со строками MBCS (или SBCS).

В следующих примерах кода показано использование функций `_TCHAR` и `_tcsrev` для сопоставления моделям многобайтовой кодировки, Юникод и однобайтовой кодировки.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Если `_MBCS` определено, препроцессор отображает этот фрагмент в этом коде:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Если `_UNICODE` определено, препроцессор отображает этот фрагмент в этом коде:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Если `_MBCS` ни `_UNICODE` один из них не определен, препроцессор отображает фрагмент до однобайного кода ASCII:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Таким образом, можно писать, поддерживать и компилировать файл кода с одним исходным кодом для выполнения процедур, характерных для любого из трех типов наборов символов.

## <a name="see-also"></a>См. также раздел

[Текст и струны](../text/text-and-strings-in-visual-cpp.md)<br/>
[Использование TCHAR. Типы данных H с _MBCS кодом](../text/using-tchar-h-data-types-with-mbcs-code.md)
