---
title: /w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (уровень предупреждения)
description: Справочник по параметрам компилятора MicrosoftC++ C/Compiler:/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/WO,/WV и/ВКС.
ms.date: 01/31/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarningLevel
- VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarnAsError
- VC.Project.VCCLWCECompilerTool.WarnAsError
- /wx
- VC.Project.VCCLWCECompilerTool.WarningLevel
- /wall
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- /Wv
- /w0
- /w1
- /w2
- /w3
- /w4
- /wd
- /we
- /wo
helpviewer_keywords:
- /W1 compiler option [C++]
- w compiler option [C++]
- -wo compiler option [C++]
- Warning Level compiler option
- W1 compiler option [C++]
- -we compiler option [C++]
- /WX compiler option [C++]
- -wd compiler option [C++]
- WX compiler option [C++]
- wo compiler option [C++]
- Wall compiler option [C++]
- /w compiler option
- W2 compiler option [C++]
- -W2 compiler option [C++]
- wd compiler option [C++]
- /we compiler option [C++]
- we compiler option [C++]
- -W1 compiler option [C++]
- -W4 compiler option [C++]
- -Wall compiler option [C++]
- /Wall compiler option [C++]
- -W0 compiler option [C++]
- W0 compiler option [C++]
- -WX compiler option [C++]
- /wo compiler option [C++]
- W4 compiler option [C++]
- W3 compiler option [C++]
- /wd compiler option [C++]
- warnings, as errors compiler option
- /W3 compiler option [C++]
- /W0 compiler option [C++]
- /W4 compiler option [C++]
- -W3 compiler option [C++]
- -w compiler option [C++]
- /W2 compiler option [C++]
- /Wv compiler option [C++]
ms.openlocfilehash: 80b6d0c1fe684de9af62683a75f0fd1107a94089
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972173"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (уровень предупреждения)

Указывает, как компилятор создает предупреждения для данной компиляции.

## <a name="syntax"></a>Синтаксис

> **/w**\
> **/W0**\
> **/W1**\
> **/W2**\
> **/W3**\
> **/W4**\
> **/Wall**\
> **/WV**\[ **:** _версия_] \
> **/Wx**\
> **/W1**_warning_\
> **/W2**_warning_\
> **/W3**_warning_\
> **/W4**_warning_\
> **/WD**_warning_\
> **/We**_warning_\
> _предупреждение_ /WO

## <a name="remarks"></a>Заметки

Параметры предупреждения определяют отображаемые предупреждения компилятора и поведение предупреждений для всей компиляции.

Параметры предупреждений и связанные с ними аргументы описаны в следующих таблицах:

Параметр | Описание
------ | -----------
**/w** | Подавляет все предупреждения компилятора.
**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4** | Задает уровень предупреждений, создаваемых компилятором. Допустимые уровни предупреждений находятся в диапазоне от 0 до 4:<br />**/W0** подавляет все предупреждения. Это эквивалентно **/w**.<br />**/W1** отображает предупреждения уровня 1 (серьезные). **/W1** является параметром по умолчанию в компиляторе командной строки.<br />**/W2** отображает предупреждения уровня 1 и 2 (существенные).<br />**/W3** отображает предупреждения уровня 1, уровня 2 и уровня 3 (качество производства). **/W3** — это параметр по умолчанию в интегрированной среде разработки.<br />**/W4** отображает предупреждения уровня 1, уровня 2 и 3 и все предупреждения уровня 4 (информационные), которые по умолчанию не отключены. Рекомендуется использовать этот параметр для предоставления Lint предупреждений. Для нового проекта, возможно, лучше использовать **/W4** во всех компиляциях. Этот параметр позволяет обеспечить минимальный возможный дефект кода.
**/Wall** | Отображает все предупреждения, отображаемые **/W4** , и все другие предупреждения, не включенные в **/W4** , например предупреждения, отключенные по умолчанию. Дополнительные сведения см. [в разделе предупреждения компилятора, которые по умолчанию отключены](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
**/WV**\[ **:** _версия_] | Отображает только предупреждения, появившиеся в версии компилятора *версий* и более ранних версиях. Этот параметр можно использовать для подавления новых предупреждений в коде при миграции на более новую версию компилятора. Это позволяет сохранить существующий процесс сборки при их исправлении. Необязательный параметр *Version* имеет форму *nn*\[.\[*mm* . *bbbbb*]], где *nn* — основной номер версии, *mm* — необязательный дополнительный номер версии, а *bbbbb* — необязательный номер сборки компилятора. Например, используйте **/WV: 17** для отображения только предупреждений, появившихся в Visual Studio 2012 (основной номер версии 17) или более ранней. То есть он отображает предупреждения от любой версии компилятора, имеющей номер версии не ниже 17. Он подавляет предупреждения, появившиеся в Visual Studio 2013 (старшая версия 18) и более поздних версий. По умолчанию **/WV** использует текущий номер версии компилятора, и предупреждения не подавляются. Сведения о предупреждениях, подавленных версией компилятора, см. [в разделе предупреждения компилятора по версии компилятора](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).
**/WX** | Интерпретирует все предупреждения компилятора как ошибки. Для нового проекта рекомендуется использовать параметр **/WX** во всех компиляциях. устранение всех предупреждений обеспечивает минимальный возможный дефект кода.<br /><br /> Компоновщик также имеет параметр **/WX** . Дополнительные сведения см. в разделе [/WX (обработка предупреждений компоновщика как ошибок)](wx-treat-linker-warnings-as-errors.md).

Следующие параметры являются взаимоисключающими друг с другом. Последний параметр, указанный из этой группы, применяется к:

Параметр | Описание
------ | -----------
**/W1**_nnnn_<br /><br /> **/W2**_nnnn_<br /><br /> **/W3**_nnnn_<br /><br /> **/W4**_nnnn_ | Задает уровень предупреждений для номера предупреждения, заданного параметром _nnnn_. Эти параметры позволяют изменить поведение компилятора для этого предупреждения, если задан конкретный уровень предупреждений. Эти параметры можно использовать совместно с другими параметрами предупреждений для применения собственных стандартов кодирования предупреждений, а не по умолчанию, предоставляемых Visual Studio.<br /><br /> Например, **/w34326** приводит к тому, что C4326 создается как предупреждение уровня 3, а не на уровне 1. Если компиляция выполняется с параметром **/w34326** и параметром **/W2** , то предупреждение C4326 не создается.
**/WD**_nnnn_ | Подавляет предупреждение компилятора, заданное параметром _nnnn_.<br /><br /> Например, **/wd4326** подавляет предупреждение компилятора C4326.
**/We**_nnnn_ | Обрабатывает предупреждение компилятора, указанное в _nnnn_ как ошибка.<br /><br /> Например, **/we4326** приводит к тому, что предупреждение Number C4326 считается ошибкой компилятора.
**/WO**_nnnn_ | Сообщает о предупреждении компилятора, заданном параметром _nnnn_ только один раз.<br /><br /> Например, **/wo4326** приводит к сообщению о предупреждении C4326 только один раз, при первом обнаружении компилятором.

При использовании любых параметров предупреждений при создании предкомпилированного заголовка эти параметры сохраняются. Использование предкомпилированного заголовка помещает те же параметры предупреждения в силе. Чтобы переопределить параметры предупреждений предкомпилированного заголовка, установите другой параметр предупреждения в командной строке.

Директиву [предупреждения #pragma](../../preprocessor/warning.md) можно использовать для управления уровнем предупреждения, о котором сообщается во время компиляции в конкретных исходных файлах.

Параметр **/w** не влияет на директивы pragma warning в исходном коде.

[Документация по ошибкам сборки](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) описывает уровни предупреждений и предупреждений, а также указывает причину, по которой определенные инструкции могут не компилироваться по мере необходимости.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Установка параметров компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Чтобы задать параметры **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/Wall**, **/WV**, **/WX**или **/ВКС-** , выберите **Свойства конфигурации** > **Общие**сведения о **языкеC++ C/**  > .

   - Чтобы задать параметры **/W0**, **/W1**, **/W2**, **/W3**, **/W4**или **/Wall** , измените свойство **уровень предупреждения** .

   - Чтобы задать параметры **/WX** или **/ВКС-** , измените свойство **обрабатывать предупреждения как ошибки** .

   - Чтобы задать версию для параметра **/WV** , введите номер версии компилятора в свойстве **warning Version** .

1. Чтобы задать параметры **/WD** или **/We** , выберите страницу свойства **конфигурации** > **CC++ /**  > **Дополнительные** свойства.

   - Чтобы задать параметр **/WD** , выберите элемент управления раскрывающийся список свойства **Отключить определенные предупреждения** и нажмите кнопку **изменить**. В диалоговом окне **Отключение конкретных предупреждений** введите номер предупреждения в поле изменить. Чтобы ввести более одного предупреждения, разделите их значениями, используя точку с запятой ( **;** ). Например, чтобы отключить C4001 и C4010, введите **4001; 4010**. Нажмите кнопку **ОК** , чтобы сохранить изменения и вернуться в диалоговое окно **страницы свойств** .

   - Чтобы установить параметр **/We** , установите флажок **обрабатывать определенные предупреждения как ошибки** и нажмите кнопку **изменить**. В диалоговом окне **Обработка конкретных предупреждений как ошибок** введите номер предупреждения в поле изменить. Чтобы ввести более одного предупреждения, разделите их значениями, используя точку с запятой ( **;** ). Например, чтобы обрабатывать и C4001, и C4010 как ошибки, введите **4001; 4010**. Нажмите кнопку **ОК** , чтобы сохранить изменения и вернуться в диалоговое окно **страницы свойств** .

1. Чтобы задать параметр **/WO** , выберите **Свойства конфигурации** > странице свойств **Командная строка** **C/C++**  > . В поле **Дополнительные параметры** введите параметр компилятора.

1. Выберите **ОК** для сохранения внесенных изменений.

### <a name="to-set-the-compiler-option-programmatically"></a>Установка параметра компилятора программным способом

- См. разделы <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> и <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также:

\ [параметров компилятора компилятором MSVC](compiler-options.md)
[Синтаксис командной строки компилятора КОМПИЛЯТОРОМ MSVC](compiler-command-line-syntax.md)
