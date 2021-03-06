---
title: /PDBPATH
ms.date: 11/04/2016
f1_keywords:
- /pdbpath
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
ms.openlocfilehash: f29b8e61fbfbdb0f373e3e7510cb3f1fe0b9cc2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319854"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>Параметры

*filename*<br/>
Имя файла .dll или .exe, для которого требуется найти соответствующий файл PDB.

**: VERBOSE**<br/>
(Необязательно) Сообщает все каталоги, где была предпринята попытка найти PDB-файл.

## <a name="remarks"></a>Примечания

/ PDBPATH выполняет поиск на компьютере по тем же путям, которые отладчик будет выполнять поиск PDB-файл и сообщит о соответствующих, если таковые имеются, PDB-файлы с файлом, указанным в *filename*.

При использовании отладчика Visual Studio, могут возникнуть проблемы из-за того, что отладчик использует PDB-файл для различных версий файла, который при отладке.

/ PDBPATH поиск PDB-файлы по следующим путям:

- Проверьте расположение, где находится исполняемый файл.

- Проверьте расположение PDB-файлов, записанных в исполняемый файл. Обычно это расположение во время образ был связан.

- Проверьте путь поиска, настроенные в интегрированной среде разработки Visual Studio.

- Проверьте по путям в _NT_SYMBOL_PATH и _NT_ALT_SYMBOL_PATH переменные среды.

- Проверьте в каталоге Windows.

## <a name="see-also"></a>См. также

[Параметры DUMPBIN](dumpbin-options.md)<br/>
[/PDBALTPATH (использование альтернативного пути к файлу PDB)](pdbaltpath-use-alternate-pdb-path.md)
