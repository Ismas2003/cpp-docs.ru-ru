---
title: '&lt;> seeAlso (C++ комментарии к документации)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 698db2df462f561acd897d0d0e56b3106a915466
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988605"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

Кроме того, с помощью тега \<seealso> можно указать текст, который должен отображаться в разделе "См. также". Тег [\<see>](see-visual-cpp.md) позволяет задать ссылку из текста.

## <a name="syntax"></a>Синтаксис

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Параметры

*member*<br/>
Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.  Заключите имя в одинарные или двойные кавычки.

Компилятор проверяет, существует ли элемент кода, и разрешает `member` в имя элемента в выходных XML-данных.  Если компилятору не удается найти `member`, он выдает предупреждение.

Дополнительные сведения о создании ссылки cref на универсальный тип см. в разделе [\<see>](see-visual-cpp.md).

## <a name="remarks"></a>Заметки

Чтобы обработать и сохранить комментарии документации в файл, при компиляции необходимо использовать параметр [/doc](doc-process-documentation-comments-c-cpp.md).

В разделе [\<summary>](summary-visual-cpp.md) можно найти пример использования тега \<seealso>.

Компилятор КОМПИЛЯТОРОМ MSVC будет пытаться разрешить ссылки cref в одном проходе через комментарии к документации.  Поэтому если при использовании правил поиска C++ компилятор не найдет символ, ссылка будет помечена как не разрешенная.

## <a name="example"></a>Пример

В следующем примере cref ссылается на неразрешенный символ. XML-комментарием для ссылки cref на B::Test будет `<seealso cref="!:B::Test" />`, тогда как ссылка на A::Test представляет собой `<seealso cref="M:A.Test" />` с правильным форматом.

```cpp
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>См. также:

[Документация XML](xml-documentation-visual-cpp.md)
