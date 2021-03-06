---
title: Поддержка многопоточности для устаревшего кода (Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: 6f76ff42d2e28afe251ce234220051111736d3c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215089"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Поддержка многопоточности для устаревшего кода (Visual C++)

Визуальный C++ элемент позволяет одновременно выполнять несколько параллельных потоков. Многопоточность позволяет отключать фоновые задачи, управлять одновременными потоками ввода, управлять пользовательским интерфейсом и многое другое.

## <a name="in-this-section"></a>в этом разделе

[Реализация многопоточности на языке C с помощью функций Win32](multithreading-with-c-and-win32.md)<br/>
Обеспечивает поддержку создания многопоточных приложений с помощью Microsoft Windows

[Реализация многопоточности на языке C++ с помощью классов MFC](multithreading-with-cpp-and-mfc.md)<br/>
Описывает процессы и потоки, а также подход MFC к многопоточности.

[Многопоточность и языковые стандарты](multithreading-and-locales.md)<br/>
Обсуждаются проблемы, возникающие при использовании языковых функций библиотеки времени выполнения C и C++ стандартной библиотеки в многопоточном приложении.

## <a name="related-sections"></a>См. также

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Класс, представляющий поток исполнения в приложении.

[ксинкобжект](../mfc/reference/csyncobject-class.md)<br/>
Описывает чистый виртуальный класс, который предоставляет функциональные возможности, общие для объектов синхронизации в Win32.

[ксемафоре](../mfc/reference/csemaphore-class.md)<br/>
Представляет семафор, который является объектом синхронизации, который позволяет ограниченному количеству потоков в одном или нескольких процессах получить доступ к ресурсу.

[кмутекс](../mfc/reference/cmutex-class.md)<br/>
Класс представляет мьютекс — объект синхронизации, позволяющий ограничить доступ к ресурсу одним потоком.

[ккритикалсектион](../mfc/reference/ccriticalsection-class.md)<br/>
Представляет критическую секцию, которая представляет собой объект синхронизации, позволяющий одному потоку за раз обращаться к ресурсу или разделу кода.

[цевент](../mfc/reference/cevent-class.md)<br/>
Представляет событие, которое представляет собой объект синхронизации, позволяющий одному потоку уведомлять другой, что произошло событие.

[кмултилокк](../mfc/reference/cmultilock-class.md)<br/>
Класс представляет механизм контроля доступа к ресурсам в многопоточных программах.

[ксинглелокк](../mfc/reference/csinglelock-class.md)<br/>
Класс представляет механизм контроля доступа к определенному ресурсу в многопоточных программах.
