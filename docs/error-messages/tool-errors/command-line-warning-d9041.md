---
title: Предупреждение командной строки D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 7c685a1ca3195ad4ab52bab8b5d32b1a51534b24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196579"
---
# <a name="command-line-warning-d9041"></a>Предупреждение командной строки D9041

Недопустимое значение "значение" для "/Option"; предполагается "значение"; При указании этого предупреждения добавьте "/Analyze" в параметры командной строки

Номер предупреждения анализа кода был добавлен в параметр командной строки **/WD**, **/We**, **/WO**или **/WL** без указания параметра **/Analyze** в командной строке. Чтобы устранить эту ошибку, либо добавьте параметр командной строки **/Analyze** , либо удалите недопустимый номер предупреждения из соответствующего параметра командной строки **/w** .

## <a name="example"></a>Пример

Следующий пример командной строки создает предупреждение D9041:

```
cl /EHsc /LD /wd6001 filename.cpp
```

Чтобы устранить предупреждение, добавьте параметр командной строки **/Analyze** . Если параметр **/Analyze** не поддерживается в вашей версии компилятора, Удалите недопустимый номер предупреждения из параметра **/WD** .

## <a name="see-also"></a>См. также раздел

[Ошибки командной строки с D8000 по D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Параметры компилятора MSVC](../../build/reference/compiler-options.md)
