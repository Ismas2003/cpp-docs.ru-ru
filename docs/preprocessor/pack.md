---
title: Прагма pack
ms.date: 11/11/2019
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 037c57a10b1de7dd00249ae60acaef0939e355eb
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765738"
---
# <a name="pack-pragma"></a>Прагма pack

Задает выравнивание упаковки для членов структуры, объединения и класса.

## <a name="syntax"></a>Синтаксис

> **пакет #pragma (показывать)**\
> **пакет #pragma (Push** [ **,** *identifier* ] [ **,** *n* ] **)**\
> **пакет #pragma (POP** [ **,** { *идентификатор* | *n* }] **)**\
> **пакет #pragma (** [ *n* ] **)**

### <a name="parameters"></a>Параметры

**казывающи**\
Используемых Отображает текущее значение байта для выравнивания упаковки. Значение отображается в предупреждении.

**распространение**\
Используемых Помещает текущее значение выравнивания упаковки во внутренний стек компилятора и устанавливает для текущего значения выравнивания упаковки значение *n*. Если *n* не задано, текущее значение выравнивания упаковки помещается.

**Рор**\
Используемых Удаляет запись из верхнего внутреннего стека компилятора. Если параметр *n* не указан вместе с **POP**, то значение упаковки, связанное с результирующей записью в верхней части стека, является новым значением выравнивания упаковки. Если указано значение *n* , то, например `#pragma pack(pop, 16)`, *n* становится новым значением выравнивания упаковки. Если вы открыли с помощью *идентификатора* `#pragma pack(pop, r1)`, например, все записи в стеке извлекаются до тех пор, пока не будет найдена запись с *идентификатором* . Эта запись извлекается, а значение упаковки, связанное с результирующей записью в верхней части стека, — это новое значение выравнивания упаковки. При использовании *идентификатора* , который не найден ни в одной записи в стеке, **POP** игнорируется.

Инструкция `#pragma pack (pop, r1, 2)` эквивалентна, `#pragma pack (pop, r1)` за которой следует `#pragma pack(2)`.

*Идентификатор*\
Используемых При использовании с **Push**назначает имя записи во внутреннем стеке компилятора. При использовании с **POP**выводит запись из внутреннего стека до тех пор, пока *идентификатор* не будет удален. Если *идентификатор* не найден во внутреннем стеке, ничего не извлекается.

*\n*\
Используемых Указывает значение в байтах, используемое для упаковки. Если параметр компилятора [/Zp](../build/reference/zp-struct-member-alignment.md) не задан для модуля, значение по умолчанию для *n* равно 8. Допустимые значения: 1, 2, 4, 8 и 16. Выравнивание элемента находится на границе, кратной *n*, или кратном размеру элемента, в зависимости от того, что меньше.

## <a name="remarks"></a>Remarks

Чтобы *упаковать* класс, необходимо разместить его члены непосредственно после друг друга в памяти. Это может означать, что некоторые или все элементы могут быть выровнены по границе меньше, чем выравнивание по умолчанию целевой архитектуры. **Pack** предоставляет управление на уровне объявления данных. Он отличается от параметра компилятора [/Zp](../build/reference/zp-struct-member-alignment.md), который обеспечивает только управление на уровне модуля. **пакет** вступает в силу в первом объявлении **структуры**, **объединения**или **класса** после того, как будет показана директива pragma. **Pack** не влияет на определения. Вызов **Pack** без аргументов задает значение *n* , заданное в параметре `/Zp`компилятора. Если параметр компилятора не установлен, по умолчанию используется значение 8 для x86, ARM и ARM64. Значение по умолчанию — 16 для машинного кода x64.

При изменении выравнивания структуры она может занимать меньше места в памяти, но возможно снижение производительности или даже возникновение аппаратного исключения для невыровненного доступа.  Это поведение исключения можно изменить с помощью [функцию SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode).

Дополнительные сведения об изменении выравнивания см. в следующих статьях:

- [__alignof](../cpp/alignof-operator.md)

- [нижнем](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Примеры выравнивания структуры](../build/x64-software-conventions.md#examples-of-structure-alignment) (только для x64)

   > [!WARNING]
   > В Visual Studio 2015 и более поздних версиях можно использовать стандартные операторы **alignas** и **alignof** , которые в `__alignof` отличие `declspec( align )` от и переносимы между компиляторами. Стандарт C++ не поддерживает упаковку, поэтому необходимо по-прежнему использовать **Pack** (или соответствующее расширение в других компиляторах) для задания выравнивания, размер которого меньше, чем длина слова целевой архитектуры.

## <a name="examples"></a>Примеры

В следующем примере показано, как использовать директиву pragma **Pack** для изменения выравнивания структуры.

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

В следующем примере показано, как использовать синтаксис *Push*, *POP*и *Показать* .

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810

// pop to the identifier and then set
// the value of the current packing alignment:
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>См. также

[Директивы pragma и ключевое слово __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
