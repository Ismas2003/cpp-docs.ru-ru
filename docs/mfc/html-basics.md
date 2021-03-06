---
title: Основы HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 6d3a692eab47a1309ee0248b51ab8563fb077d5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377249"
---
# <a name="html-basics"></a>Основы HTML

Большинство браузеров имеют возможность изучения html-источника страниц, которые вы просматриваете. При просмотре источника вы увидите несколько тегов HTML (язык разметки Hypertext), окруженных угловыми скобками (<>), вперемежку с текстом.

Ниже приведенные ниже шаги используют HTML-теги для создания простой веб-страницы. В этих шагах вы введете простой текст в файл в блокноте, внесете несколько изменений, сохраните файл и перезагрузите страницу в браузере, чтобы увидеть ваши изменения.

#### <a name="to-create-an-html-file"></a>Создание HTML-файла

1. Открыть блокнот или любой простой текстовый редактор.

1. Из меню **файла** выберите **новое**.

1. Введите следующие строки:

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. Из меню **файла** выберите **Сохранить**и сохранить файл в виде c: веб-страницы -First.htm. Оставьте файл открытым в редакторе.

1. Переключитесь на браузер и из меню **файла,** выберите **Open**или введите *file://C:/webpages/first.htm* в окне URL-адреса браузера. Вы должны увидеть пустую страницу с подписью окна "Топ HTML теги".

   Обратите внимание, что теги являются парными и включены в угловые скобки. Теги не чувствительны к случаям, но капитализация часто используется, чтобы выделить теги.

   Тег \<HTML> запускает документ, \<и тег /HTML> заканчивается. Окончание теги (не всегда требуется) являются такими же, как начальный тег, но вперед слэш (/) перед тегом. Между угловой кронштейном (<) и началом тега не должно быть пробелов.

1. Переключитесь на блокнот, и после линии \</HEAD>, введите:

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. Из меню **файла** выберите **Сохранить**.

1. Вернитесь в браузер и обновите страницу.

   Слова будут отображаться в клиентской области окна вашего браузера. Обратите внимание, что возврат вагона игнорируется. Если вы хотите иметь разрыв строки, `<BR>` вы должны включить тег после первой строки.

   Для всех последующих шагов вставьте \<текст в \<любом месте между BODY> и /BODY> добавить в тело вашего документа.

1. Добавить заголовок:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Добавьте изображение, используя файл .gif, сохраненный в том же каталоге, что и ваша страница:

    ```html
    <IMG src="yourfile.gif">
    ```

1. Добавить список:

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. Чтобы пронумеровать список, используйте \<парные теги OL> и \</OL> вместо меток \<UL> и \</UL>.

Это должно начаться. Если вы видите отличную функцию на веб-странице, вы можете узнать, как она была создана, изучая источник HTML. HTML-редакторы, такие как Microsoft Front Page, могут использоваться для создания простых и продвинутых страниц.

Вот весь источник HTML для файла, который вы создали:

```html
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

Для полного описания тегов, атрибутов и расширений см.

[Последняя опубликованная версия HTML](https://www.w3.org/TR/html/) на W3C.org.

## <a name="see-also"></a>См. также раздел

[Основы программирования ВРЦ в Интернете](../mfc/mfc-internet-programming-basics.md)
