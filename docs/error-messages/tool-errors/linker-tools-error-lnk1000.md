---
title: Ошибка средств компоновщика LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 48b976f6e996d0e076849dc9b20b4cedd47dfbcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195426"
---
# <a name="linker-tools-error-lnk1000"></a>Ошибка средств компоновщика LNK1000

> Неизвестная ошибка; Дополнительные сведения о вариантах технической поддержки см. в документации

Обратите внимание на обстоятельства ошибки, затем попробуйте изолировать проблему и создать воспроизводимый тестовый случай. Сведения о том, как исследовать и сообщать об этих ошибках, см. в разделе [как сообщить C++ о проблеме с визуальным набором инструментов или документацией](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Эта ошибка может возникнуть при смешении стандартных файлов заголовков (например, Windows. h) и собственных файлов. Включите предварительно скомпилированный заголовок, если он есть, сначала стандартные заголовки, а затем собственные файлы заголовков.
