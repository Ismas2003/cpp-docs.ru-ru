---
title: Ошибка компилятора C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: a25c59fa5c9ba0102666f6c8922a61b063e7627a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202310"
---
# <a name="compiler-error-c2712"></a>Ошибка компилятора C2712

> Невозможно использовать __try в функциях, требующих уничтожения объектов

## <a name="remarks"></a>Remarks

Ошибка C2712 может возникать при использовании [/EHsc](../../build/reference/eh-exception-handling-model.md), а функция с структурированной обработкой исключений также содержит объекты, требующие очистки (уничтожения).

Возможные решения

- переместите код, для которого требуется SEH, в другую функцию;

- заново напишите функции, использующие SEH, чтобы избежать использования локальных переменных и параметров с деструкторами; не используйте SEH в конструкторах и деструкторах;

- компилируйте код без параметра /EHsc.

Ошибка C2712 также может возникать при вызове метода, объявленного с помощью ключевого слова [__event](../../cpp/event.md) . Поскольку событие может использоваться в многопоточной среде, компилятор создает код, который не позволяет управлять базовым объектом события, а затем заключает созданный код в [инструкцию try-finally](../../cpp/try-finally-statement.md). Поэтому ошибка C2712 может возникнуть, если вызвать метод события и передать аргумент, тип которого содержит деструктор. Одно из решений в данном случае — передача аргумента в качестве константной ссылки.

C2712 также может возникнуть при компиляции с **параметром/clr: pure** и объявлении статического массива указателей на функции в блоке `__try`. Статический член требует, чтобы компилятор использовал динамическую инициализацию в **/clr: pure**, что C++ подразумевает обработку исключений. Однако обработка исключений C++ не допускается в блоке `__try`.

Параметры компилятора **/clr: pure** и **/clr: Сейф** являются устаревшими в Visual Studio 2015 и не поддерживаются в Visual Studio 2017.

## <a name="example"></a>Пример

В следующем примере показано возникновение ошибки C2712 и приводятся сведения по ее устранению.

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```
