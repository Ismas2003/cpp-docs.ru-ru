---
title: Предупреждение компилятора (уровни 2 и 4) C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 4b0750fe50e18214e0841eff6b3459438e9a6aec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197955"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Предупреждение компилятора (уровни 2 и 4) C4200

использовано нестандартное расширение: массив нулевого размера в конструкции/объединении

Указывает, что структура или объединение содержит массив нулевого размера.

Объявление массива нулевого размера — это расширение Майкрософт. При этом возникает предупреждение уровня 2 при компиляции файла C++ и предупреждение уровня 4 при компиляции файла C. При компиляции C++ также появляется предупреждение: «Невозможно создать конструктор копии или оператор присвоения копии, когда UDT содержит массив нулевого размера». Этот пример создает предупреждение C4200:

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

Это нестандартное расширение, часто используемое для реализации взаимодействия кода с существующими структурами данных переменной длины. Если этот сценарий применим для вашего кода, можно отключить это предупреждение:

## <a name="example"></a>Пример

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```
