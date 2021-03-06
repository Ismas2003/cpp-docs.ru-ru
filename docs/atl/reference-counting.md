---
title: Подсчет ссылок (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 095f0ad2ecc1e1a870077899d61a3c594f8cc95f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321746"
---
# <a name="reference-counting"></a>Подсчет ссылок

Сам COM не пытается автоматически удалить объект из памяти, когда он думает, что объект больше не используется. Вместо этого программист объекта должен удалить неиспользованный объект. Программист определяет, может ли объект быть удален на основе подсчета ссылок.

COM использует `IUnknown` методы, [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) и [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), для управления подсчетом ссылок интерфейсов на объекте. Общие правила вызова этих методов:

- Всякий раз, когда клиент `AddRef` получает указатель интерфейса, должны быть вызваны на интерфейс.

- Всякий раз, когда клиент закончил с помощью указателя интерфейса, он должен позвонить. `Release`

В простой реализации каждый `AddRef` вызов `Release` приращений и каждый вызов декреции счетчика внутри объекта. Когда счет возвращается к нулю, интерфейс больше не имеет пользователей и может свободно удалить себя из памяти.

Подсчет ссылок также может быть реализован таким образом, чтобы каждая ссылка на объект (не на отдельный интерфейс) была подсчитана. В этом случае `AddRef` `Release` каждый из них призывает делегатов `Release` к центральной реализации объекта, и освобождает весь объект, когда его количество ссылок достигает нуля.

> [!NOTE]
> Когда `CComObject`объект, полученный из-за полученного, строится с помощью **нового** оператора, количество ссылок составляет 0. Таким образом, `AddRef` вызов должен быть сделан `CComObject`после успешного создания-производного объекта.

## <a name="see-also"></a>См. также раздел

[Введение в модель COM](../atl/introduction-to-com.md)<br/>
[Управление сроком службы объектов с помощью подсчета ссылок](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
