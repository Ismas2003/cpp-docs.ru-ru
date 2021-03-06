---
title: /DLL (построение библиотеки DLL)
ms.date: 11/04/2016
f1_keywords:
- /dll
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
ms.openlocfilehash: 5f7907d659ee3bedc590b88320df03edce005b06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293762"
---
# <a name="dll-build-a-dll"></a>/DLL (построение библиотеки DLL)

```
/DLL
```

## <a name="remarks"></a>Примечания

Параметр/DLL создает библиотеку DLL в качестве основного выходного файла. Библиотеки DLL, обычно содержит экспортов, которые могут использоваться другой программой. Указание экспортов, перечислены в порядке предпочтительности использования тремя способами:

1. [__declspec(dllexport)](../../cpp/dllexport-dllimport.md) в исходном коде

1. [ЭКСПОРТОВ](exports.md) инструкции в DEF-файла

1. [/EXPORT](export-exports-a-function.md) спецификации в команде LINK

Программа может использовать более одного метода.

Другой способ построения библиотеки DLL — с помощью **БИБЛИОТЕКИ** оператор определения модуля. Параметры/Base и/DLL вместе эквивалентны **БИБЛИОТЕКИ** инструкции.

Не использовать этот параметр в среде разработки; Этот параметр предназначен для использования только в командной строке. Этот параметр имеет значение при создании проекта библиотеки DLL с помощью мастера приложений.

Обратите внимание на то, что при создании библиотеки импорта в предварительном перед созданием файла DLL, необходимо передать тот же набор объектных файлов при построении библиотеки DLL, как Вы передали при сборке библиотеки импорта.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

1. Нажмите кнопку **свойства конфигурации** папки.

1. Нажмите кнопку **Общие** страницу свойств.

1. Изменить **тип конфигурации** свойство.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.

## <a name="see-also"></a>См. также

[Справочник по компоновщику MSVC](linking.md)<br/>
[Параметры компоновщика MSVC](linker-options.md)
