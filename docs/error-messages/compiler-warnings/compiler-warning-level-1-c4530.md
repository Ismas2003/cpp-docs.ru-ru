---
title: Предупреждение компилятора (уровень 1) C4530
description: Справочное руководство по компилятору Microsoft C' предупреждение C4530.
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 9de88a4b0b6c7176ff82b68c92d09d9fe75a70b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369786"
---
# <a name="compiler-warning-level-1-c4530"></a>Предупреждение компилятора (уровень 1) C4530

> Используется обработчик исключений, но семантика раскручивания не включена. Указать /EHsc

В коде используется обработка исключений, но [/EHsc](../../build/reference/eh-exception-handling-model.md) не был включен в параметры компилятора.

## <a name="remarks"></a>Remarks

Компилятору **`/EHsc`** требуется возможность создания кода СЗ, который соответствует стандарту C's для обработки исключений. Стандартная *семантика раскрутки* указывает на то, что объекты и стек-рамки, построенные между тем, где выбрасывается исключение и где оно поймано, должны быть уничтожены, а их ресурсы восстановлены. Этот процесс известен как *раскручивание стека.*

Опция **`/EHsc`** говорит компилятору генерировать код, который вызывает деструкторы на автоматических объектах хранения, когда исключение проходит через содержащую рамку стека. *Автоматические* объекты хранения — это объекты, выделенные в стеке, такие как локальные переменные. Это называется автоматическим хранилищем, потому что оно автоматически выделяется при вызове функций и автоматически высвобождается при их возвращении. *Кадр стека* — это данные, размещенные в стеке при вызове функции, а также автоматическое хранение.

Когда исключение брошено, оно может переместить через несколько кадров стека прежде чем оно уловлено. Эти кадры стека должны быть развёрнуты, поскольку исключение проходит через них в обратном порядке вызова. Автоматические объекты хранения в каждом кадре стека должны быть уничтожены, чтобы восстановить свои ресурсы чисто. Это тот же процесс разрушения и восстановления, который происходит автоматически, когда функция возвращается нормально.

Когда **`/EHsc`** опция не включена, автоматические объекты хранения в кадрах стека между функцией метания и функцией, в которой поймано исключение, не разрушаются. Уничтожаются только автоматические объекты хранения, созданные в **попытке** или **блоке catch,** что может привести к значительным утечкам ресурсов и другим неожиданным поведением.

Если никакие исключения не могут быть брошены в ваш исполняемый, вы можете спокойно игнорировать это предупреждение. Некоторые коды могут потребовать других вариантов обработки исключений. Для получения дополнительной информации [см.](../../build/reference/eh-exception-handling-model.md)

## <a name="example"></a>Пример

Следующий образец генерирует C4530:

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Составить образец **`/EHsc`** для устранения предупреждения.
