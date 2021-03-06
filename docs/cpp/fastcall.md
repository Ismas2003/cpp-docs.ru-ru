---
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: d4b650542a3a85c8f0008374abef02686c5491a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188926"
---
# <a name="__fastcall"></a>__fastcall

**Блок, относящийся только к системам Microsoft**

Соглашение о вызовах **__fastcall** указывает, что аргументы функции должны передаваться в регистры, если это возможно. Это соглашение о вызовах применяется только к архитектуре x86. В следующем списке показана реализация этого соглашения о вызовах.

|Элемент|Реализация|
|-------------|--------------------|
|Порядок передачи аргументов|Первые два значения DWORD или меньшие аргументы, найденные в списке аргументов слева направо, передаются в регистрах ECX и EDX; все остальные аргументы передаются в стек справа налево.|
|Обязанность по обслуживанию стека|Вызываемая функция извлекает аргументы из стека.|
|Соглашение об оформлении имен|Префикс AT (\@) предваряется именами; символу, за которым следует число байтов (в десятичной системе) в списке параметров, присваивается имя.|
|Соглашение о преобразовании регистра|Изменение регистра не выполняется.|

> [!NOTE]
> В следующих версиях компилятора могут использовать другие регистры для сохранения параметров.

Использование параметра компилятора [/GR](../build/reference/gd-gr-gv-gz-calling-convention.md) приводит к тому, что каждая функция в модуле будет компилироваться как **__fastcall** , если только функция не объявлена с помощью конфликтующего атрибута или имя функции `main`.

Ключевое слово **__fastcall** принимается и игнорируется компиляторами, предназначенными для архитектуры ARM и x64; в микросхеме x64 по соглашению первые четыре аргумента передаются в регистры, когда это возможно, а дополнительные аргументы передаются в стек. Дополнительные сведения см. в разделе [соглашение о вызовах x64](../build/x64-calling-convention.md). На микросхеме ARM можно передавать в регистрах до четырех целочисленных аргументов и до восьми аргументов с плавающей запятой; дополнительные аргументы передаются в стеке.

Если используется внестрочное определение нестатической функции класса, то модификатор соглашения о вызовах не должен быть задан во внестрочном определении. То есть для нестатических методов-членов считается, что соглашение о вызовах, указанное во время объявления, было сделано в точке определения. Рассмотрим следующее определение класса:

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

В этом случае следующий код:

```cpp
void CMyClass::mymethod() { return; }
```

эквивалентен следующему:

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

Для совместимости с предыдущими версиями **_fastcall** является синонимом для **__fastcall** , если только не указан параметр компилятора [/Za \(отключить расширения языка)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Пример

В следующем примере аргументы передаются в функцию `DeleteAggrWrapper` в регистрах.

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также раздел

[Передача аргументов и соглашения об именовании](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)
