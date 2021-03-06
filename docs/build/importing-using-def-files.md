---
title: Импорт с помощью DEF-файлов
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273421"
---
# <a name="importing-using-def-files"></a>Импорт с помощью DEF-файлов

Если вы решили использовать **__declspec(dllimport)** вместе с DEF-файлом, следует изменить DEF-файл так, чтобы в нем вместо раздела CONSTANT использовался раздел DATA. Это снизит вероятность возникновения проблем из-за неправильного написания кода.

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

Причины представлены в таблице ниже.

|Ключевое слово|Результат в библиотеке импорта|Экспортируемые элементы|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

При использовании **__declspec(dllimport)** и CONSTANT в библиотеке DLL импорта с расширением LIB, создаваемой для обеспечения явной компоновки, указываются как версия `imp`, так и недекорированное имя. При использовании **__declspec(dllimport)** и DATA указывается только версия `imp` имени.

При использовании CONSTANT для доступа к `ulDataInDll` можно использовать любую из следующих конструкций кода:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-или-

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Однако если в DEF-файле используется DATA, к переменной `ulDataInDll` будет иметь доступ только код, скомпилированный со следующим определением:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

Использовать CONSTANT опаснее, так как если вы пропустите дополнительный уровень косвенного обращения, то может случиться так, что вы обратитесь к указателю на переменную в таблице адресов импорта, а не к самой переменной. Подобная проблема часто проявляется как нарушение прав доступа, так как таблица адресов импорта в настоящее время доступна компилятору и компоновщику только для чтения.

По этой причине текущая версия компоновщика MSVC выдает предупреждение при обнаружении CONSTANT в DEF-файле. Единственной реальной причиной использования CONSTANT является невозможность перекомпиляции некоторого объектного файла, если в файле заголовка не содержится ключевое слово **__declspec(dllimport)** для прототипа.

## <a name="see-also"></a>См. также

[Импорт в приложение](importing-into-an-application.md)
