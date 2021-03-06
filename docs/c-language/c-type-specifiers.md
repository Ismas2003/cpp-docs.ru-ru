---
title: Спецификаторы типов C
ms.date: 01/29/2018
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
ms.openlocfilehash: 1191cf4d2912cda535547f465fe4bfbedebe8fa2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313198"
---
# <a name="c-type-specifiers"></a>Спецификаторы типов C

Спецификаторы типа в объявлениях определяют тип объявления переменной или функции.

## <a name="syntax"></a>Синтаксис

*type-specifier*: &nbsp;&nbsp;&nbsp;&nbsp;**void** &nbsp;&nbsp;&nbsp;&nbsp;**char** &nbsp;&nbsp;&nbsp;&nbsp;**short** &nbsp;&nbsp;&nbsp;&nbsp;**int** &nbsp;&nbsp;&nbsp;&nbsp;**long** &nbsp;&nbsp;&nbsp;&nbsp;**float** &nbsp;&nbsp;&nbsp;&nbsp;**double** &nbsp;&nbsp;&nbsp;&nbsp;**signed** &nbsp;&nbsp;&nbsp;&nbsp;**unsigned** &nbsp;&nbsp;&nbsp;&nbsp;*struct-or-union-specifier* &nbsp;&nbsp;&nbsp;&nbsp;*enum-specifier* &nbsp;&nbsp;&nbsp;&nbsp;*typedef-name*

Типы **signed char**, **signed int**, **signed short int** и **signed long int** вместе с аналогичными типами **unsigned** и **enum** совокупно именуются *целочисленными*. Описатели типов **float**, **double** и **long double** называются типами *с плавающей* или *плавающей запятой*. Любой спецификатор целочисленного типа или типа с плавающей запятой можно использовать в объявлении переменной или функции. Если в объявлении отсутствует *описатель типа*, для него предполагается значение **int**.

Необязательные ключевые слова **signed** и **unsigned** могут указываться перед любым целочисленным типом или после него, за исключением **enum**. Также их можно использовать отдельно в качестве описателей типа, и тогда они трактуются соответственно как **signed int** и **unsigned int**. Если ключевое слово **int** используется отдельно, для него применяется модификатор **signed**. Если ключевые слова **long** или **short** используются отдельно, они трактуются как **long int** и **short int**.

Типы перечисления считаются базовыми типами. Описатели типов для типов перечисления рассматриваются в статье [Объявления перечислений C](../c-language/c-enumeration-declarations.md).

Ключевое слово **void** используется для трех целей: задание типа возвращаемого функцией значения, задание списка типов аргументов для функции, не принимающей аргументов, и задание указателя на неуказанный тип. Тип **void** можно использовать для объявления функций, не возвращающих никаких значений, или для объявления указателя на неуказанный тип. В статье [Аргументы](../c-language/arguments.md) описано, как расценивается **void**, если это единственное ключевое слово в скобках после имени функции.

**Блок, относящийся только к системам Microsoft**

Проверка типов теперь соответствует требованиям ANSI, то есть типы **short** и **int** считаются разными. Например, это является переопределением в компиляторе Microsoft C, которое принималось предыдущими версиями компилятора.

```C
int   myfunc();
short myfunc();
```

Следующий пример также создает предупреждение о косвенном обращении к разным типам:

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Компилятор Microsoft C также выдает предупреждения в случае разного использования знака (типы со знаком и без знака). Пример:

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

Выражения типа **void** вычисляются для учета побочных эффектов. Невозможно каким-либо образом использовать (несуществующее) значение выражения типа **void**; также невозможно преобразовать выражение типа **void** (с помощью явного или неявного преобразования) в любой тип, кроме **void**. При использовании в контексте, где требуется выражение **void**, выражения любого другого типа его значение игнорируется.

Для обеспечения соответствия спецификации ANSI тип <strong>void\*\*</strong> не может использоваться как <strong>int\*\*</strong>. В качестве указателя на неуказанный тип можно использовать только **void**<strong>\*</strong>.

**Завершение блока, относящегося только к системам Майкрософт**

С помощью объявлений **typedef** можно создавать дополнительные описатели типа, как описано в статье [Объявления Typedef](../c-language/typedef-declarations.md). Сведения о размерах для каждого типа см. в статье [Хранение базовых типов](../c-language/storage-of-basic-types.md).

## <a name="see-also"></a>См. также

[Объявления и типы](../c-language/declarations-and-types.md)
