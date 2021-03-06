---
title: Пошаговое руководство. Работа с проектами и решениями (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 36c64a74310c72df38021aebd8abb3ee430da3f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375898"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Пошаговое руководство. Работа с проектами и решениями (C++)

В этой статье описано, как создать проект C++ в Visual Studio, добавить код, а затем выполнить сборку и запуск проекта. Проект в этом пошаговом руководстве представляет собой программу, которая отслеживает количество игроков в различных карточных играх.

В Visual Studio для организации работы служат проекты и решения. Решение может содержать несколько проектов, например библиотеку DLL и ссылающийся на нее исполняемый файл. Дополнительные сведения см. в статье [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) (Решения и проекты).

## <a name="before-you-start"></a>Перед началом работы

Для выполнения данного пошагового руководства требуется Visual Studio 2017 или более поздней версии. Если вам нужна копия, здесь приведено краткое руководство: [Установка поддержки С++ в Visual Studio](../build/vscpp-step-0-installation.md). Если вы еще не сделали этого, выполните приведенные ниже шаги после установки в рамках руководства "Hello, World", чтобы убедиться в правильности установки и работы компонентов C++.

Полезно владеть основами языка C++ и понимать назначение компилятора, компоновщика и отладчика. В руководстве также предполагается, что вы знакомы с Windows и умеете использовать меню и диалоговые окна.

## <a name="create-a-project"></a>Создание проекта

Чтобы создать проект, сначала выберите шаблон типа проекта. Для каждого типа проекта среда Visual Studio задает параметры компилятора и — в зависимости от типа — создает начальный код, который позже можно изменить. Приведенные ниже инструкции немного отличаются в зависимости от используемой версии Visual Studio. Чтобы просмотреть документацию для предпочтительной версии Visual Studio, используйте элемент управления селектора **версии.** Он находится в верхней части таблицы содержимого на этой странице.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Создание проекта в Visual Studio 2019

1. В главном меню выберите **Файл ** > **Создать ** > **Проект**, чтобы открыть диалоговое окно **Создание проекта**.

1. В верхней части диалогового окна для параметра **Язык** выберите значение **C++**, для параметра **Платформа** — значение **Windows**, а для параметра **Тип проекта** — значение **Консоль**.

1. В отфильтрованном списке типов проектов щелкните **Консольное приложение**, а затем нажмите кнопку **Далее**. На следующей странице введите имя проекта *Игра*.

   Вы можете принять расположение по умолчанию в раскрывающемся списке **Расположение**, ввести другое расположение или нажать кнопку **Обзор**, чтобы перейти к каталогу, в котором требуется сохранить проект.

   При создании проекта среда Visual Studio помещает его в решение. По умолчанию имя решения совпадает с именем проекта. Можно изменить имя в поле **Имя решения**, но для этого примера оставьте имя по умолчанию.

1. Нажмите кнопку **Создать**, чтобы создать проект.

   Visual Studio создает решение и файлы проекта и открывает редактор для созданного файла исходного кода Game.cpp.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Создание проекта в Visual Studio 2017

1. В строке меню щелкните **Файл** > **Создать** > **Проект**.

1. В левой области диалогового она **Новый проект** разверните узел **Установленные** и выберите **Visual C++**, если он еще не открыт.

1. В списке установленных шаблонов в центральной области выберите шаблон **Консольное приложение Windows**.

1. В поле **Имя** введите имя проекта. Для этого примера введите *Game* (Игра).

   Вы можете принять расположение по умолчанию в раскрывающемся списке **Расположение**, ввести другое расположение или нажать кнопку **Обзор**, чтобы перейти к каталогу, в котором требуется сохранить проект.

   При создании проекта среда Visual Studio помещает его в решение. По умолчанию имя решения совпадает с именем проекта. Можно изменить имя в поле **Имя решения**, но для этого примера оставьте имя по умолчанию.

1. Нажмите кнопку **ОК**, чтобы создать проект.

   Visual Studio создает решение и файлы проекта и открывает редактор для созданного файла исходного кода Game.cpp.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Создание проекта в Visual Studio 2015

1. В строке меню щелкните **Файл** > **Создать** > **Проект**.

1. В левой области диалогового она **Новый проект** разверните узел **Установленные** и выберите **Visual C++**, если он еще не открыт.

1. В списке установленных шаблонов в центральной области выберите шаблон **Консольное приложение Win32**.

1. В поле **Имя** введите имя проекта. Для этого примера введите *Game* (Игра).

   Вы можете принять расположение по умолчанию в раскрывающемся списке **Расположение**, ввести другое расположение или нажать кнопку **Обзор**, чтобы перейти к каталогу, в котором требуется сохранить проект.

   При создании проекта среда Visual Studio помещает его в решение. По умолчанию имя решения совпадает с именем проекта. Можно изменить имя в поле **Имя решения**, но для этого примера оставьте имя по умолчанию.

1. Нажмите кнопку **ОК**, чтобы создать проект.

   Visual Studio создает решение и файлы проекта и открывает редактор для созданного файла исходного кода Game.cpp.

::: moniker-end

## <a name="organize-projects-and-files"></a>Упорядочение файлов и проектов

Для организации проектов, файлов и других ресурсов в решении, а также для управления ими можно использовать **обозреватель решений**.

В этой части пошагового руководства описывается добавление класса в проект. При добавлении класса Visual Studio добавляет соответствующие H- и CPP-файлы. Результаты отображаются в **обозревателе решений**.

### <a name="to-add-a-class-to-a-project"></a>Добавление класса в проект

1. Если окно **Обозреватель решений** не отображается в Visual Studio, выберите в строке меню **Вид** > **Обозреватель решений**.

1. Выберите проект **Game** в **обозревателе решений**. В панели меню выберите **класс Project** > **Add.**

1. В диалоге **Add Class** введите *Cardgame* в поле **Типа Name.** Не изменяйте имена файлов и параметры по умолчанию. Выберите кнопку **ОК**.

   Visual Studio создает файлы и добавляет их в проект. Вы можете просмотреть их в **обозревателе решений**. Файлы Cardgame.h и Cardgame.cpp открываются в редакторе.

1. Внесите в файл Cardgame.h следующие изменения.

   - После открывающей скобки определения класса добавьте два частных элемента данных.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Измените конструктор по умолчанию, созданный средой Visual Studio. После описателя доступа `public:` найдите строку, которая выглядит следующим образом:

      `Cardgame();`

      Измените этот конструктор так, чтобы он принимал один параметр типа `int` с именем *players*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - После деструктора по умолчанию добавьте встроенное объявление функции-члена типа `static int` с именем *GetParticipants*, которая не принимает параметры и возвращает значение `totalParticipants`.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   После изменения файл Cardgame.h должен содержать примерно такой код:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   Строка `#pragma once` указывает компилятору включить файл заголовка только один раз. Дополнительные сведения см. в разделе [once](../preprocessor/once.md). Сведения о других ключевых словах C++ в представленном выше файле заголовка см. в разделах [class](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md) и [public](../cpp/public-cpp.md).

1. Перейдите на вкладку **Cardgame.cpp** в верхней части области редактирования, чтобы открыть этот файл для внесения изменений.

1. Удалите весь код в файле и замените его следующим кодом:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    int Cardgame::totalParticipants = 0;

    Cardgame::Cardgame(int players)
        : players(players)
    {
        totalParticipants += players;
        cout << players << " players have started a new game.  There are now "
             << totalParticipants << " players in total." << endl;
    }

    Cardgame::~Cardgame()
    {
    }
    ```

   > [!NOTE]
   > При вводе кода можно использовать автозавершение. Например, если вы введете этот код на клавиатуре, вы можете ввести *pl* или *tot,* а затем нажмите **Ctrl**+**Spacebar.** Функция автозавершения автоматически вводит `players` или `totalParticipants`.

## <a name="add-test-code-to-your-main-function"></a>Добавление тестового кода в функцию main

Добавьте в приложение код, тестирующий новые функции.

### <a name="to-add-test-code-to-the-project"></a>Добавление тестового кода в проект

1. В окне редактора **Game.cpp** замените существующий код следующим:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    void PlayGames()
    {
        Cardgame bridge(4);
        Cardgame blackjack(8);
        Cardgame solitaire(1);
        Cardgame poker(5);
    }

    int main()
    {
        PlayGames();
        return 0;
    }
    ```

   Этот код добавляет в исходный код функцию тестирования `PlayGames` и вызывает ее в `main`.

## <a name="build-and-run-your-app-project"></a>Сборка и запуск проекта приложения

Затем выполните сборку проекта и запустите приложение.

### <a name="to-build-and-run-the-project"></a>Построение и запуск проекта

1. В строке меню последовательно выберите **Сборка** > **Собрать решение**.

   Выходные данные сборки выводятся в окне **Вывод**. Если сборка пройдет успешно, выходные данные должны выглядеть следующим образом:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   В окне **Вывод** в зависимости от конфигурации сборки могут отображаться различные шаги, но если сборка проекта завершается успешно, то последняя строка выходных данных должна выглядеть так, как показано выше.

   Если сборка завершилась неудачей, сравните свой код с образцами в предыдущих действиях.

1. Для запуска проекта в панели меню выберите **Debug** > **Start Without Debugging.** Появится консольное окно, а результат выполнения должен выглядеть примерно следующим образом:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Для закрытия консольного окна нажмите любую клавишу.

Вы успешно выполнили сборку проекта приложения и решения. Продолжайте выполнять пошаговое руководство, чтобы получить дополнительные сведения о сборке проектов кода C++ в Visual Studio.

## <a name="next-steps"></a>Дальнейшие действия

**Предыдущий:** [Использование Визуальной студии IDE для разработки рабочего стола СЗ](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Далее:** [Прохождение: Строительство проекта (КЗ)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>См. также раздел

[Языковая справка к СЗ](../cpp/cpp-language-reference.md)<br/>
[Проекты и системы сборки](../build/projects-and-build-systems-cpp.md)<br/>
