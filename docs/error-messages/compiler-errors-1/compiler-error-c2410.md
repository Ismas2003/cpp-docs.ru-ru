---
title: Ошибка компилятора C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: e4d30ff0fbca7428fb1dcf252bcad50bd53488d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205713"
---
# <a name="compiler-error-c2410"></a>Ошибка компилятора C2410

"идентификатор": неоднозначное имя члена в "Context"

Идентификатор является членом более чем одной структуры или объединения в этом контексте.

Используйте структуру или описатель объединения для операнда, вызвавшего ошибку. Описатель структуры или объединения — это идентификатор типа `struct` или `union` (имя `typedef` или переменная того же типа, что и у ссылки на структуру или объединение). Для использования операнда спецификатор должен быть левым операндом первого оператора выбора члена (.).
