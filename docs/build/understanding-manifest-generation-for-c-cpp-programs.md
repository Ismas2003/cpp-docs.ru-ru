---
title: Основные сведения о создании манифестов для программ C/C++
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
ms.openlocfilehash: 16d5efc5c5f7ce81b4b60269b0c666fd5d24266e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492523"
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>Основные сведения о создании манифестов для программ C/C++

[Манифест](/windows/win32/sbscs/manifests) представляет собой XML-документ, который может быть внешним XML-файлом или ресурсом, встроенным в приложение или сборку. Файл манифеста [изолированного приложения](/windows/win32/SbsCs/isolated-applications) используется для управления именами и версиями совместно используемых параллельных сборок, с которыми должно быть связано приложение во время выполнения. Манифест параллельной сборки задает зависимости от имен, версий, ресурсов и других сборок.

Существует два способа создания манифеста для изолированного приложения или параллельной сборки. Во-первых, автор сборки может вручную создать файл манифеста, следуя правилам и требованиям к именованию. Кроме того, если программа зависит только от сборок MSVC, таких как CRT, MFC, ATL и другие, манифест может создаваться автоматически компоновщиком.

Заголовки библиотек Visual C++ содержат сведения о сборке, а если библиотеки включены в код приложения, эти сведения о сборке используются компоновщиком для формирования манифеста для конечного двоичного файла. Компоновщик не внедряет файл манифеста в двоичный файл и может создавать манифест только как внешний файл. Наличие манифеста в качестве внешнего файла может подходить не для всех сценариев. Например, рекомендуется, чтобы закрытые сборки имели внедренные манифесты. В сборках командной строки, например тех, которые используют NMAKE для построения кода, манифест можно внедрить с помощью средства манифеста. Дополнительные сведения см. в разделе [Создание манифеста в командной строке](manifest-generation-at-the-command-line.md). При сборке в Visual Studio манифест можно внедрить, задав свойство для средства манифеста в диалоговом окне **Свойства проекта**. См. раздел [Создание манифеста в Visual Studio](manifest-generation-in-visual-studio.md).

## <a name="see-also"></a>См. также

[Основные понятия, связанные с изолированными приложениями и параллельными сборками](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Создание изолированных приложений и параллельных сборок C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
