---
title: /vd (отключение смещений при выполнении конструктора)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: db198dbdc7bd43ffd4de9bde39ee81a8b95a25ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316890"
---
# <a name="vd-disable-construction-displacements"></a>/vd (отключение смещений при выполнении конструктора)

## <a name="syntax"></a>Синтаксис

```
/vdn
```

## <a name="arguments"></a>Аргументы

**0**<br/>
Подавляет члена смещения конструктора или деструктора vtordisp. Выберите этот параметр только в том случае, если вы уверены, что все конструкторы и деструкторы классов вызывают виртуальные функции виртуально.

**1**<br/>
Позволяет создавать элементы смещения конструктора или деструктора скрытые vtordisp. Этот вариант используется по умолчанию.

**2**<br/>
Позволяет использовать [оператор dynamic_cast](../../cpp/dynamic-cast-operator.md) на создаваемого объекта. Например приведение dynamic_cast из виртуального базового класса в производном классе.

**/ vd2** добавляет поля vtordisp в том случае, если у вас есть виртуальный базовый класс с виртуальными функциями. **/ vd1** должно быть достаточно. Самый распространенный случай, когда **/vd2** необходим при только виртуальную функцию в виртуальном базовом деструктор.

## <a name="remarks"></a>Примечания

Эти параметры применяются только для кода C++, используются виртуальные базовые классы.

Visual C++ реализует поддержку смещения построения C++ в ситуациях, где используется виртуальное наследование. Смещений при выполнении конструктора решают проблему, возникающую, когда виртуальная функция, объявленному в виртуальном базовом и переопределении в производном классе, вызывается из конструктора во время построения дальнейшей производного класса.

Проблема в том, что виртуальная функция может быть передан неверный `this` указатель в результате несоответствий между смещениями виртуальной базы класса и смещениями его производных классов. Это решение предоставляет смещения одиночное коррекции, называемое полем vtordisp для каждого виртуального базового класса.

По умолчанию поля vtordisp вводятся всякий раз, когда код определяет пользовательские конструкторы и деструкторы, а также переопределяет виртуальные функции виртуальных базовых классов.

Эти параметры влияют на все исходные файлы. Используйте [vtordisp](../../preprocessor/vtordisp.md) Чтобы отключить и повторно включить Добавление полей vtordisp по принципу класс.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

1. Откройте папку **C/C++** .

1. Выберите страницу свойств **Командная строка** .

1. Введите параметр компилятора в поле **Дополнительные параметры** .

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора MSVC](compiler-options.md)<br/>
[Синтаксис командной строки компилятора MSVC](compiler-command-line-syntax.md)
