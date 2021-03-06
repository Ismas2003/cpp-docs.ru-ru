---
title: Мастер простых объектов ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.overview
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
ms.openlocfilehash: bd4c9eede16ed086020dd8f12d90876e50a0a341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319203"
---
# <a name="atl-simple-object-wizard"></a>Мастер простых объектов ATL

Этот мастер вставляет в проект минимальный объект COM. Используйте эту страницу мастера, чтобы указать имена, идентифицирующие класс ИК и файлы для объекта и его функциональность COM.

Используйте страницу [Options](../../atl/reference/options-atl-simple-object-wizard.md) этого мастера, чтобы указать модель потока объекта, его поддержку агрегации, а также поддерживает ли он двойные интерфейсы и автоматизацию. Вы также можете указать поддержку интерфейса информации об ошибках, точек подключения, поддержки Internet Explorer и свободного маршалинга.

## <a name="remarks"></a>Remarks

Начиная с Visual Studio 2008, сценарий регистрации, созданный этим мастером, зарегистрирует свои компоненты COM в разделе **HKEY_CURRENT_USER** вместо **HKEY_LOCAL_MACHINE**. Чтобы изменить это, задайте в мастере ATL параметр **Register component for all users** (Регистрация компонентов для всех пользователей).

## <a name="names"></a>именах

Укажите имена объекта, интерфейса и классов, которые необходимо добавить в проект. Все поля, кроме **Короткое имя**, можно редактировать независимо друг от друга. Если вы меняете текст для **короткого имени**, то это отображается в именах остальных полей на странице. Если в разделе COM вы измените имя **Coclass**, это отразится в полях **Type** и **ProgID**, но имя **Interface** не изменится. Этот принцип именования позволяет вам легко распознавать имена при разработке элементов управления.

> [!NOTE]
> **Coclass** можно изменять только для проектов без атрибутов. Если проект содержит атрибуты, **Coclass** изменить невозможно.

## <a name="c"></a>C++

Предоставляет информацию для класса C++, созданного для объекта.

- **Краткое название**

   Задает сокращенное имя для объекта. Имя, которым вы определяете имена `Class` и `Coclass`, **CPP-файла** и **H-файла**, **Interface**, **Type** и **ProgID**, если вы не изменили эти поля по отдельности.

- **H-файл**

   Задает имя файла заголовка для класса нового объекта. По умолчанию это имя основано на имени, указанном в поле **Короткое имя**. Нажмите кнопку с многоточием, чтобы сохранить имя файла в выбранном расположении или добавить объявление класса к существующему файлу. При выборе существующего файла мастер не сохраняет его в выбранном расположении, пока вы не нажмете в мастере кнопку **Готово**.

   Мастер не перезаписывает файл. Если выбрать имя существующего файла, при нажатии кнопки **Готово** мастер предложит указать, нужно ли добавить объявление класса к содержимому файла. Чтобы добавить данные в файл, нажмите кнопку **Да**; чтобы вернуться в мастер и указать другое имя файла, нажмите кнопку **Нет**.

- **Class**

   Задает имя создаваемого класса. Это имя основано на имени, указанном в поле **Короткое имя**, с предшествующей "С" — типичным префиксом для имени класса.

- **CPP-файл**

   Задает имя файла реализации для класса нового объекта. По умолчанию это имя основано на имени, указанном в поле **Короткое имя**. Нажмите кнопку с многоточием, чтобы сохранить имя файла в выбранном расположении. Файл не сохраняется в выбранном расположении, пока вы не нажмете кнопку **Готово** в мастере.

   Мастер не перезаписывает файл. Если выбрать имя существующего файла, при нажатии кнопки **Готово** мастер предложит указать, нужно ли добавить реализацию класса к содержимому файла. Чтобы добавить данные в файл, нажмите кнопку **Да**; чтобы вернуться в мастер и указать другое имя файла, нажмите кнопку **Нет**.

- **Attributed**

   Указывает, использует ли объект атрибуты. Если вы добавляете объект в проект ATL с атрибутами, этот параметр будет установлен и недоступен для изменения. То есть вы можете добавить только помеченные атрибутами объекты в проект, созданный с поддержкой атрибутов.

   Объект с атрибутами можно добавить только в проект ATL с поддержкой атрибутов. Если выбрать этот параметр для проекта ATL без поддержки атрибутов, мастер предложит указать, нужно ли добавить поддержку атрибутов в проект.

   По умолчанию объекты, которые добавляются после установки этого параметра, определяются как атрибуты (флажок установлен). Вы можете снять этот флажок, чтобы добавить объект, который не использует атрибуты.

   Дополнительные сведения см. в статьях [Application Settings, ATL Project Wizard](../../atl/reference/application-settings-atl-project-wizard.md) (Параметры приложений, мастер проектов ATL) и [C++ Attributes for COM and .NET](../../windows/basic-mechanics-of-attributes.md) (Атрибуты C++ для COM и .NET).

## <a name="com"></a>COM

Предоставляет сведения о функциональных возможностях модели COM для объекта.

- **Coclass**

   Задает имя класса компонентов, содержащего список интерфейсов, поддерживаемых объектом.

   > [!NOTE]
   > Если проект создается с помощью атрибутов или если на странице мастера указывается, что объект использует атрибуты, вы не можете изменить эту опцию, поскольку ATL не включает `coclass` атрибут.

- **Type**

   Задает описание объекта, которое отобразится в реестре.

- **Интерфейс**

   Задает интерфейс, созданный вами для объекта. Этот интерфейс содержит настраиваемые методы.

- **Progid**

   Задает имя, которое можно использовать для контейнеров вместо CLSID объекта.

## <a name="see-also"></a>См. также раздел

[Простой объект ATL](../../atl/reference/adding-an-atl-simple-object.md)
