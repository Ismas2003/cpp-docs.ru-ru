---
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: b66cf0df998b4e33a9f3425fdf0f260d163f423b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944713"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

Указывает, выполнен ли вход в блок `__finally`[оператора try-finally](../cpp/try-finally-statement.md), когда система выполняет внутренний список обработчиков завершения.

## <a name="syntax"></a>Синтаксис

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Возвращаемое значение

Значение **true**, если система *очищает* стек; в противном случае — значение **false**.

## <a name="remarks"></a>Примечания

Это внутренняя функция, используемая для управления исключениями очистки, и она не должна вызываться из пользовательского кода.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|_abnormal_termination|excpt.h|

## <a name="see-also"></a>См. также

[Оператор try-finally](../cpp/try-finally-statement.md)
