---
title: /Zc:wchar_t (wchar_t – это собственный тип)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: 962bb2aaa2f05ad0dc4c9c86cd5cc9694cfad98b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446157"
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t – это собственный тип)

Разбор `wchar_t` как встроенного типа в соответствии со стандартом C++.

## <a name="syntax"></a>Синтаксис

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>Примечания

Если **/Zc: wchar_t** , `wchar_t` является ключевым словом для встроенных целочисленного типа в коде, скомпилированном как C++. Если **/Zc:wchar_t-** (со знаком минус) указанного, или код компилируется как C, `wchar_t` не является встроенным типом. Вместо этого `wchar_t` определяется как `typedef` для `unsigned short` в канонический заголовок stddef.h. (Microsoft реализация определяет ее в другой заголовок, включенный по stddef.h и других стандартных заголовках.)

Мы не рекомендуем **/Zc:wchar_t-** поскольку C++ стандарт требует, `wchar_t` был встроенным типом. Использование версии `typedef` может вызывать проблемы переносимости. При обновлении более ранних версиях Visual Studio и возникает ошибка компилятора [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) тем, что код пытается выполнить неявное преобразование `wchar_t` для `unsigned short`, рекомендуется изменить код, чтобы устранить ошибку, Вместо того чтобы задавать **/Zc:wchar_t-**.

**/Zc: wchar_t** включен параметр по умолчанию в C++ компиляциям и учитывается в компиляции C. [/ Permissive-](permissive-standards-conformance.md) параметр не влияет на **/Zc: wchar_t**.

Microsoft реализует тип `wchar_t` как двухбайтовое значение без знака. Он сопоставляется с типом собственного характерные для Майкрософт `__wchar_t`. Дополнительные сведения о `wchar_t`, см. в разделе [диапазоны типов данных](../../cpp/data-type-ranges.md) и [фундаментальные типы](../../cpp/fundamental-types-cpp.md).

При написании нового кода, который должен взаимодействовать со старым кодом, который по-прежнему использует `typedef` версии `wchar_t`, можно предоставить перегрузки для обоих `unsigned short` и `__wchar_t` разновидности `wchar_t`так, чтобы ваш код могут быть связаны с кода, компилируемого с **/Zc: wchar_t** или код, скомпилированный без него. В противном случае пришлось бы предоставлять два различных построения библиотеки: с и без **/Zc: wchar_t** включена. Даже в этом случае рекомендуется произвести сборку старого кода с использованием компилятора, который используется для компиляции нового кода. Никогда не смешивайте двоичные файлы, скомпилированные разными компиляторами.

Когда **/Zc: wchar_t** указано,  **\_WCHAR\_T\_ОПРЕДЕЛЕННЫЕ** и  **\_СОБСТВЕННОГО\_WCHAR\_T\_ОПРЕДЕЛЕННЫЕ** определены символы. Для получения дополнительной информации см. [Predefined Macros](../../preprocessor/predefined-macros.md).

Если код использует глобальные функции компилятора COM, так как **/Zc: wchar_t** сейчас на по умолчанию, мы рекомендуем изменять явные ссылки на comsupp.lib (из [комментарий pragma](../../preprocessor/comment-c-cpp.md) или на командной строки) ссылками на comsuppw.lib или comsuppwd.lib. (Если необходимо выполнять компиляцию с **/Zc:wchar_t-**, используйте comsupp.lib.) Если включен файл заголовка comdef.h, правильная библиотека задается автоматически. Сведения о поддержке COM компилятором см. в разделе [поддержки компилятора COM](../../cpp/compiler-com-support.md).

`wchar_t` Встроенный тип не поддерживается при компиляции кода C. Дополнительные сведения о вопросах соответствия в Visual C++, см. в разделе [нестандартное поведение](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

1. Выберите **свойства конфигурации** > **C/C++** > **языка** страницы.

1. Изменить **обрабатывать wchar_t как встроенный тип** свойства.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>.

## <a name="see-also"></a>См. также

[/Zc (соответствие)](zc-conformance.md)<br/>
