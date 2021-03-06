---
title: Обычные арифметические преобразования
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
ms.openlocfilehash: 729e173c695db3b4970490e84bedfd441e6ff6d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344841"
---
# <a name="usual-arithmetic-conversions"></a>Обычные арифметические преобразования

Большинство операторов C выполняют преобразования типов для приведения операндов выражения к общему типу или для расширения коротких значений в соответствии с размером целого числа, используемым в машинных операциях. Преобразования, выполняемые с помощью операторов С, зависят от конкретного оператора и типа операнда или операндов. Однако многие операторы выполняют аналогичные преобразования с операндами целочисленного типа и типа с плавающей запятой. Эти преобразования называются арифметическими преобразованиями. В результате преобразования значения операнда в совместимый тип значение не меняется.

Арифметические преобразования, представленные ниже, называются обычными арифметическими преобразованиями. Эти шаги применяются только к бинарным операторам, ожидающим арифметический тип. Цель — получить общий тип, который также будет типом результата. Чтобы определить, какие преобразования выполняются на самом деле, компилятор применяет следующий алгоритм к бинарным операциям в выражении. Шаги ниже представлены не в порядке приоритета.

1. Если какой-либо из операндов имеет тип `long double`, то другой операнд преобразуется в тип `long double`.

1. Если вышеуказанное условие не выполняется, а один из операндов имеет тип **double**, то второй операнд преобразуется в тип **double**.

1. Если оба вышеуказанных условия не выполняются, а один из операндов имеет тип **float**, то второй операнд преобразуется в тип **float**.

1. Если три вышеуказанных условия не выполняются (ни один из операндов не принадлежит типам с плавающей запятой), то целочисленные преобразования операндов выполняются следующим образом.

   - Если какой-либо из операндов имеет тип `unsigned long`, то другой операнд преобразуется в тип `unsigned long`.

   - Если вышеуказанное условие не выполняется, при этом один из операндов имеет тип **long**, а второй — тип `unsigned int`, то оба операнда преобразуются в тип `unsigned long`.

   - Если два вышеуказанных условия не выполняются, а один из операндов имеет тип **long**, то второй операнд преобразуется в тип **long**.

   - Если три вышеуказанных условия не выполняются и какой-либо из операндов имеет тип `unsigned int`, то другой операнд преобразуется в тип `unsigned int`.

   - Если ни одно из вышеуказанных условий не соблюдается, то оба операнда преобразуются в тип `int`.

Эти правила преобразования демонстрируются в следующем примере.

```
float   fVal;
double  dVal;
int   iVal;
unsigned long ulVal;

dVal = iVal * ulVal; /* iVal converted to unsigned long
                      * Uses step 4.
                      * Result of multiplication converted to double
                      */
dVal = ulVal + fVal; /* ulVal converted to float
                      * Uses step 3.
                      * Result of addition converted to double
                      */
```

## <a name="see-also"></a>См. также

[Операторы в C](../c-language/c-operators.md)
