---
title: Расширение аргументов заполнителей
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: f1fb964fe98223fb7187b83c7101027ed1f9cbea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233819"
---
# <a name="expanding-wildcard-arguments"></a>Расширение аргументов заполнителей

**Блок, относящийся только к системам Microsoft**

При выполнении программы на языке C можно использовать любой из двух подстановочных знаков, вопрос (?) или звездочку (*), для задания аргументов имени файла и пути в командной строке.

По умолчанию подстановочные знаки в аргументах командной строки не разворачиваются. Вы можете заменить обычную процедуру загрузки вектора аргументов `argv` на версию, которая разворачивает подстановочные знаки, используя компоновку с файлом setargv.obj или wsetargv.obj. Если программа использует функцию `main` , скомпонуйте ее с файлом setargv.obj. Если программа использует функцию `wmain` , скомпонуйте ее с файлом wsetargv.obj. Они оба реализуют эквивалентное поведение.

Чтобы скомпоновать программу с файлом setargv.obj или wsetargv.obj, используйте параметр **/link** . Пример:

**cl example.c /link setargv.obj**

Подстановочные знаки разворачиваются так же, как команды операционной системы. (См. ознакомительные сведения о подстановочных знаках в руководстве пользователя вашей ОС).

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Параметры ссылок](../c-runtime-library/link-options.md)<br/>
[Функция main и выполнение программ](../c-language/main-function-and-program-execution.md)
