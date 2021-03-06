---
title: Обработчики сбоев
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: 2fc22ae77d729868adbf8c37d40e450e35a8e866
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292852"
---
# <a name="failure-hooks"></a>Обработчики сбоев

Обработчик сбоев включается в так же, как [обработчика уведомлений](notification-hooks.md). Процедура обработки требует возврата подходящего значения таким образом, чтобы обработку можно продолжить (HINSTANCE или FARPROC) или 0, чтобы указать, что должно вызываться исключение.

— Указатель на переменную, ссылающуюся на пользовательской функции:

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

**DelayLoadInfo** структура содержит все соответствующие необходимые данные для точного отчета об ошибках, включая значение из `GetLastError`.

Если это уведомление **dliFailLoadLib**, функция-обработчик может вернуть:

- 0, если он не может обработать ошибку.

- HMODULE, когда обработчик сбоев проблему и загружает библиотеку.

Если это уведомление **dliFailGetProc**, функция-обработчик может вернуть:

- 0, если он не может обработать ошибку.

- Допустимый адрес процедуры (адрес функции импорта), когда обработчик сбоев успешно загружает адрес.

## <a name="see-also"></a>См. также

[Обработка ошибок и предупреждений](error-handling-and-notification.md)
