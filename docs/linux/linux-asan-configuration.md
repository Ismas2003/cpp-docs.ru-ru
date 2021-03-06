---
title: Настройка проектов Linux для использования санитайзера адресов
description: Узнайте, как настроить проект C++ для Linux в Visual Studio для работы с AddressSanitizer.
ms.date: 06/07/2019
ms.openlocfilehash: 80e9ab46c948f2062391ae723c3425c435bd4507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364311"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Настройка проектов Linux для использования санитайзера адресов

В Visual Studio 2019 версии 16.1 поддержка AddressSanitizer (ASan) интегрирована в проектах Linux. Вы можете включить ASan для проектов Linux на основе MSBuild и проектов CMake. Это средство работает в удаленных системах Linux и подсистеме Windows для Linux (WSL).

## <a name="about-asan"></a>Об ASan

ASan — это средство обнаружения ошибок использования памяти в среде выполнения для C/C++, которое перехватывает следующие ошибки:

- Use after free (dangling pointer reference);
- Heap buffer overflow;
- Stack buffer overflow;
- Use after return;
- Use after scope;
- Initialization order bugs.

Когда средство ASan обнаруживает ошибку, оно немедленно останавливает выполнение. При запуске приложения с поддержкой ASan в отладчике появляется сообщение с описанием типа ошибки, адресом памяти и расположением в исходном файле, где произошла ошибка:

   ![Сообщение об ошибке ASan](media/asan-error.png)

Вы также можете просмотреть все выходные данные ASan (включая сведения о расположении выделенной или освобожденной поврежденной памяти) на панели отладки в окне вывода.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Включение ASan для проектов Linux на основе MSBuild

> [!NOTE]
> Начиная с версии 16.4 Visual Studio 2019, AddressSanitizer для проектов Linux включается в разделе **Свойства конфигурации** > **C/C++**  > **Enable AddressSanitizer** (Включить AddressSanitizer).

Чтобы включить ASan для проектов Linux на основе MSBuild, щелкните правой кнопкой мыши проект в **обозревателе решений** и выберите **Свойства**. Затем перейдите в меню **Свойства конфигурации** > **C/C++**  > **Санитайзеры**. ASan включается с помощью флагов компоновщика и компилятора. При этом проект должен быть перекомпилирован.

![Включение ASan для проекта MSBuild](media/msbuild-asan-prop-page.png)

Вы можете передать необязательные флаги среды выполнения ASan, выбрав **Свойства конфигурации** > **Отладка** > **Флаги среды выполнения AddressSanitizer**. Щелкните стрелку вниз, чтобы добавить или удалить флаги.

![Настройка флагов среды выполнения ASan](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Включение ASan для проектов Visual Studio CMake

Чтобы включить ASan для CMake, щелкните правой кнопкой мыши файл CMakeLists.txt в **обозревателе решений** и выберите **Параметры CMake для проекта**.

При этом следует выбрать конфигурацию Linux (например, **Linux-Debug**) в левой части диалогового окна:

![Конфигурация отладки Linux](media/linux-debug-configuration.png)

Параметры ASan доступны в разделе **Общие**. Введите флаги ASan среды выполнения в формате "флаг=значение", разделенные точкой с запятой.

![Конфигурация отладки Linux](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Установка отладочных символов ASan

Чтобы включить диагностику ASan, необходимо установить соответствующие отладочные символы (libasan-dbg) на удаленном компьютере Linux или в установке WSL. Версия libasan-dbg, которую можно загрузить, зависит от версии GCC, установленной на компьютере Linux:

|**Версия ASan**|**Версия GCC**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Чтобы узнать существующую версию GCC, выполните следующую команду:

```bash
gcc --version
```

Чтобы узнать требуемую версию libasan-dbg, запустите программу и просмотрите сведения на панели **Отладка** в окне **Вывод**. Загруженная версия libasan-dbg которую можно загрузить, соответствует требуемой версии libasan-dbg, установленной на компьютере Linux. Вы можете нажать клавиши **CTRL+F**, чтобы ввести libasan в окне. Например, если у вас есть libasan4, вы увидите примерно такую строку:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Биты отладки ASan можно установить в дистрибутивах Linux с поддержкой apt, выполнив следующую команду, которая устанавливает версию 4:

```bash
sudo apt-get install libasan4-dbg
```

Если средство ASan включено, в Visual Studio в верхней части панели **Отладка** в окне **Вывод** отобразится запрос на установку отладочных символов ASan.
