---
title: Предупреждение компилятора (уровень 4) C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 82adb80310fb43c848c253f9bf5e436c8c379f35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198099"
---
# <a name="compiler-warning-level-4-c4985"></a>Предупреждение компилятора (уровень 4) C4985

"имя символа": атрибуты отсутствуют в предыдущем объявлении.

Примечания SAL к текущему объявлению или определению метода отличаются от примечаний к предыдущему объявлению. В определении и объявлениях метода должны использоваться одинаковые примечания SAL.

Язык примечаний к исходному коду (SAL), созданный Майкрософт, предоставляет набор примечаний, описывающих способы использования функцией ее параметров, предположения функции о ее параметрах и гарантии, которые она дает по окончании. Примечания определены в файле заголовка sal.h.

Обратите внимание на то, что макросы SAL не будут расширяться, если в проекте не указан флаг [/analyze](../../build/reference/analyze-code-analysis.md) . При указании **/analyze**компилятор может выдать ошибку C4985, даже если без **/analyze**не было никаких ошибок или предупреждений.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. В определении метода и всех его объявлениях следует использовать одинаковые примечания SAL.

## <a name="see-also"></a>См. также раздел

[Заметки SAL](../../c-runtime-library/sal-annotations.md)
