---
title: Ошибка компилятора C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 97d9ef1eeeffa0e5a63d2c8ae2428a3fad0ff238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165591"
---
# <a name="compiler-error-c3851"></a>Ошибка компилятора C3851

> "*char*": универсальное имя символа не может обозначать символ в базовом наборе символов

## <a name="remarks"></a>Remarks

В коде, скомпилированном как C++, нельзя использовать универсальное имя символа, представляющее символ в основной кодировке исходного кода, вне строки или символьного литерала. Дополнительные сведения см. в разделе [Character Sets](../../cpp/character-sets.md). В коде, скомпилированном как C, нельзя использовать универсальное имя символа для символов в диапазоне от 0x20 до 0x7F включительно, за исключением 0x24 (' $ '), 0x40 ('\@') или 0x60 ('\`').

## <a name="example"></a>Пример

Приведенные ниже примеры кода создают ошибку C3851; также показаны способы ее устранения:

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```
