---
title: Ограничения обработчиков завершения
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: befe181a41ed418a4a824b131e741a9f02f90e38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179072"
---
# <a name="restrictions-on-termination-handlers"></a>Ограничения обработчиков завершения

Нельзя использовать инструкцию **goto** для перехода в блок оператора **__try** или блок инструкций **__finally** . Входить в этот блок необходимо только через обычный поток управления. (Однако можно перейти к блоку оператора **__try** .) Кроме того, нельзя вложить обработчик исключений или обработчик завершения в блок **__finally** .

Кроме того, некоторые типы кода, разрешенные в обработчике завершения, дают спорные результаты, поэтому их следует либо не использовать вообще, либо использовать с осторожностью. Одна из них — оператор **goto** , который выполняет переход из блока оператора **__finally** . Если блок выполняется как часть нормального завершения, ничего необычного не происходит. Однако если система разматывает стек, эта операция останавливается, и текущая функция получает контроль над происходящим, как если бы аномального завершения не было.

Оператор **return** в блоке оператора **__finally** представляет примерно такую же ситуацию. Контроль возвращается непосредственному вызывающему объекту функции, которая содержит обработчик завершения. Если система разматывала стек, этот процесс останавливается, и программа выполняется, как если бы исключения не было создано.

## <a name="see-also"></a>См. также раздел

[Написание обработчика завершения](../cpp/writing-a-termination-handler.md)<br/>
[Структурированная обработка исключений (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
