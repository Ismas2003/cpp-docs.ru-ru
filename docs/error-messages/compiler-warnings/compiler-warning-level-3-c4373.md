---
title: Предупреждение компилятора (уровень 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 5891d4679b74695f187fb50bb24fe941882fdcc7
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518352"
---
# <a name="compiler-warning-level-3-c4373"></a>Предупреждение компилятора (уровень 3) C4373

> "*функция*": виртуальная функция переопределяет "*base_function*", предыдущие версии компилятора не были переопределены, если параметры отличаются только квалификаторами const или volatile

## <a name="remarks"></a>Заметки

Ваше приложение содержит метод в производном классе, который переопределяет виртуальный метод в базовом классе, и параметры в переопределяющем методе отличаются от параметров виртуального метода только по квалификатору [const](../../cpp/const-cpp.md) или [volatile](../../cpp/volatile-cpp.md) . Это означает, что компилятор должен привязать ссылку на функцию к методу в базовом или производном классе.

Версии компилятора до Visual Studio 2008 привязывают функцию к методу в базовом классе, а затем выдают предупреждающее сообщение. Последующие версии компилятора игнорируют квалификатор `const` или `volatile`, привязывают функцию к методу в производном классе, а затем выдают предупреждение **C4373**. Поведение в последнем случае соответствует стандарту C++.

## <a name="example"></a>Пример

Следующий пример кода приводит к возникновению ошибки C4373. Чтобы устранить эту проблему, можно сделать переопределение, используя те же квалификаторы ОПС, что и базовая функция-член, или, если вы не планировали создавать переопределение, можно присвоить функции в производном классе другое имя.

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
