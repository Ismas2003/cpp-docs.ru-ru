---
title: Исключения. Высвобождение объектов в исключениях
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: 49c7c6b0481f90baa23609c1bb1596deda49f7bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371988"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Исключения. Высвобождение объектов в исключениях

В этой статье объясняется необходимость и метод освобождения объектов при возникновении исключения. Будут рассмотрены следующие задачи:

- [Обработка исключения локально](#_core_handling_the_exception_locally)

- [Исключение после уничтожения объектов](#_core_throwing_exceptions_after_destroying_objects)

Исключения, брошенные фреймворком или приложением, прерывают обычный поток программы. Таким образом, очень важно внимательно следить за объектами, чтобы вы могли правильно распоряжаться ими в случае, если исключение брошено.

Для этого есть два основных способа.

- Обработка исключений локально, используя **попытку** **поймать** ключевые слова, а затем уничтожить все объекты с помощью одного оператора.

- Уничтожить любой объект в блоке **catch,** прежде чем выбросить исключение за пределы блока для дальнейшей обработки.

Эти два подхода иллюстрируются ниже в качестве решений следующего проблемного примера:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Как написано `myPerson` выше, не будет удален, `SomeFunc`если исключение брошено . Выполнение переходит непосредственно к следующему обработчику внешнего исключения, минуя обычный выход функции и код, который удаляет объект. Указатель на объект выходит из области, когда исключение покидает функцию, и память, занятая объектом, никогда не будет восстановлена до тех пор, пока программа работает. Это утечка памяти; он будет обнаружен с помощью диагностики памяти.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Обработка исключений локально

Парадигма **try/catch** обеспечивает защитный метод программирования для предотвращения утечек памяти и обеспечения того, чтобы ваши объекты уничтожались при возникновении исключений. Например, пример, показанный ранее в этой статье, может быть переписан следующим образом:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Этот новый пример настраивает обработчик исключений, чтобы поймать исключение и обрабатывать его локально. Затем он выходит из функции нормально и разрушает объект. Важным аспектом этого примера является то, что контекст для получения исключения устанавливается с блоками **try/catch.** Без локальной рамки исключения функция никогда не узнает, что исключение было брошено, и не будет иметь возможности нормально выйти и уничтожить объект.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Исключение после уничтожения объектов

Другой способ обработки исключений — перейти их к следующему внешнему контексту обработки исключений. В блоке **ловли** вы можете сделать некоторую очистку локально выделенных объектов, а затем бросить исключение для дальнейшей обработки.

Функция метания может или не может нуждаться в распределении объектов кучи. Если функция всегда распределяет объект кучи перед возвращением в обычном случае, то функция должна также распределить объект кучи, прежде чем бросать исключение. С другой стороны, если функция обычно не размещает объект перед возвращением в обычном случае, то вы должны решить на индивидуальной основе, следует ли раздавать объект кучи.

Следующий пример показывает, как локально выделенные объекты могут быть очищены:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Механизм исключения автоматически распределяет объекты кадра; также называется деструктор объекта кадра.

Если вы называете функции, которые могут бросать исключения, вы можете использовать **блоки try/catch,** чтобы убедиться, что вы поймаете исключения и имеете возможность уничтожить любые созданные объекты. В частности, имейте в виду, что многие функции MFC могут бросать исключения.

Для получения дополнительной [информации см.](../mfc/exceptions-catching-and-deleting-exceptions.md)

## <a name="see-also"></a>См. также раздел

[Обработка исключений](../mfc/exception-handling-in-mfc.md)
