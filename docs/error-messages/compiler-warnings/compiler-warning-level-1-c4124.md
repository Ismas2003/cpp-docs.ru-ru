---
title: Предупреждение компилятора (уровень 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 6408185c99a54d5411fa5b1058cd5ec09d3326d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176316"
---
# <a name="compiler-warning-level-1-c4124"></a>Предупреждение компилятора (уровень 1) C4124

__fastcall с проверкой стека неэффективна

Для включения проверки стека использовалось ключевое слово `__fastcall`.

Соглашение `__fastcall` создает более быстрый код, но проверка стека вызывает медленный код. При использовании `__fastcall`отключите проверку стека с помощью директивы pragma **check_stack** или/ГС.

Это предупреждение выдается только для первой функции, объявленной в этих условиях.
