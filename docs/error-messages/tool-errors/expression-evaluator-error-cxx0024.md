---
title: Ошибка вычислителя выражений CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 525210090b0a4c2966f2e1432f85fd4bb6a8156d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195764"
---
# <a name="expression-evaluator-error-cxx0024"></a>Ошибка вычислителя выражений CXX0024

операции требуется l-значение

Для операции, для которой требуется l-значение, указано выражение, результатом вычисления которого является l-значение.

L-значение (так называемое, так как оно отображается в левой части оператора присваивания) является выражением, указывающим на место в памяти.

Например, `buffer[count]` является допустимым l-значением, так как указывает на определенное место в памяти. Логическое `zed != 0` сравнения не является допустимым l-значением, так как оно имеет значение TRUE или FALSE, а не адрес памяти.

Эта ошибка идентична CAN0024.
