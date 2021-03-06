---
title: TN002. Формат данных постоянного объекта
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: f65a7b7afcf6bd832c9c23560bb29374038fae1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370441"
---
# <a name="tn002-persistent-object-data-format"></a>TN002. Формат данных постоянного объекта

В этой заметке описаны процедуры MFC, поддерживающие постоянные объекты C,s, и формат данных объекта при хранении в файле. Это относится только к классам с [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) и [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) макросов.

## <a name="the-problem"></a>Проблема

Реализация MFC для постоянных данных хранит данные для многих объектов в одной смежной части файла. `Serialize` Метод объекта переводит данные объекта в компактный двоичный формат.

Реализация гарантирует, что все данные сохраняются в одном формате с помощью [класса CArchive.](../mfc/reference/carchive-class.md) Он использует `CArchive` объект в качестве переводчика. Этот объект сохраняется с момента его создания до вызова [CArchive::Закрыть](../mfc/reference/carchive-class.md#close). Этот метод может быть вызван либо явно программистом, либо косвенно деструктором, когда `CArchive`программа выходит из области, содержащей .

Эта записка описывает `CArchive` реализацию членов [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) и [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Код для этих функций вы найдете в Arcobj.cpp, а также основную реализацию в `CArchive` Arccore.cpp. Код пользователя не `ReadObject` `WriteObject` звонит и напрямую. Вместо этого эти объекты используются операторами ввода и извлечения типового типа, которые автоматически генерируются DECLARE_SERIAL и IMPLEMENT_SERIAL макросов. Следующий код `WriteObject` показывает, как и `ReadObject` неявно называются:

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Сохранение объектов в магазине (CArchive:WriteObject)

Метод `CArchive::WriteObject` записывает данные заголовка, которые используются для реконструкции объекта. Эти данные состоят из двух частей: типа объекта и состояния объекта. Этот метод также отвечает за поддержание идентичности записанного объекта, так что сохраняется только одна копия, независимо от количества указателей на этот объект (включая круговые указатели).

Сохранение (вставка) и восстановление (извлечение) объектов зависит от нескольких "явных констант". Это значения, которые хранятся в двоичном и предоставляют важную информацию в архив (обратите внимание на приставку "w" указывает 16-битные количества):

|Тег|Описание|
|---------|-----------------|
|wНулTag|Используется для указателей объектов NULL (0).|
|wNewClassTag|Отосевание описания класса, которое следует за этим, является новым для контекста архива (-1).|
|wOldClassTag|В этом контексте был замечен класс читаемого объекта (0x8000).|

При хранении объектов архив сохраняет [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) *(m_pStoreMap),* который представляет собой отображение от сохраненного объекта к 32-битного стойким идентификатору (PID). PID присваивается каждому уникальному объекту и каждому уникальному названию класса, которое сохраняется в контексте архива. Эти PID раздаются последовательно, начиная с 1. Эти PID не имеют никакого значения за пределами архива и, в частности, не следует путать с рекордными номерами или другими элементами идентификации.

В `CArchive` классе PID являются 32-битными, но они выписываются как 16-разрядные, если они не больше, чем 0x7FFE. Большие PID написаны как 0x7FFF, за которыми следует 32-разрядный PID. Это поддерживает совместимость с проектами, которые были созданы в более ранних версиях.

При запросе на сохранение объекта в архиве (обычно с помощью глобального оператора вставки) проводится проверка указателя NULL [CObject.](../mfc/reference/cobject-class.md) Если указатель NULL, *wNullTag* вставляется в архивный поток.

Если указатель не является NULL и может быть `DECLARE_SERIAL` сериализован (класс является классом), код проверяет *m_pStoreMap,* чтобы увидеть, был ли объект сохранен уже. В этом случае код вставляет 32-разрядный PID, связанный с этим объектом, в поток архива.

Если объект не был сохранен ранее, есть две возможности для рассмотрения: либо объект, так и точный тип (т.е. класс) объекта являются новыми для этого контекста архива, или объект имеет точный тип, который уже видел. Чтобы определить, был ли тип замечен, код запрашивает *m_pStoreMap* для объекта `CRuntimeClass` [CRuntimeClass,](../mfc/reference/cruntimeclass-structure.md) который соответствует объекту, связанному с сохраненным объектом. Если есть совпадение, `WriteObject` вставляет тег, `OR` который является бит-мудрый *wOldClassTag* и этот индекс. Если `CRuntimeClass` он является новым для `WriteObject` этого контекста архива, присваивает новый PID этому классу и вставляет его в архив, предшествуя значению *wNewClassTag.*

Затем дескриптор для этого класса вставляется `CRuntimeClass::Store` в архив с помощью метода. `CRuntimeClass::Store`вставляет номер схемы класса (см. ниже) и текстовое название ASCII класса. Обратите внимание, что использование текстового имени ASCII не гарантирует уникальность архива в разных приложениях. Поэтому следует отметить файлы данных, чтобы предотвратить коррупцию. После вставки информации о классе архив помещает объект в *m_pStoreMap,* а затем вызывает `Serialize` метод для вставки данных, специфичным для классов. Размещение объекта в *m_pStoreMap* `Serialize` перед вызовом предотвращает сохранение нескольких копий объекта в хранилище.

При возвращении к первоначальному вызывающему абоненту (обычно корню сети объектов) необходимо позвонить [в CArchive::Close](../mfc/reference/carchive-class.md#close). Если вы планируете выполнять другие операции `CArchive` [CFile,](../mfc/reference/cfile-class.md)необходимо вызвать метод [Flush,](../mfc/reference/carchive-class.md#flush) чтобы предотвратить порча архива.

> [!NOTE]
> Эта реализация налагает жесткий предел индексов 0x3FFFFE на контекст архива. Это число представляет собой максимальное количество уникальных объектов и классов, которые могут быть сохранены в одном архиве, но один диск файл может иметь неограниченное количество контекстов архива.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Загрузка объектов из магазина (CArchive:ReadObject)

Загрузка (извлечение) `CArchive::ReadObject` объектов использует `WriteObject`метод и является обратным . Как `WriteObject`с `ReadObject` , не вызван сразу кодом потребителя; пользовательский код должен вызывать оператора по `ReadObject` извлечению данных, который звонит с ожидаемым. `CRuntimeClass` Это гарантирует целостность типа операции экстракта.

Поскольку `WriteObject` реализация назначена увеличение PIDs, начиная с 1 (0 `ReadObject` предопределено как объект NULL), реализация может использовать массив для поддержания состояния контекста архива. Когда PID читается из магазина, если PID больше текущей верхней `ReadObject` границы *m_pLoadArray,* знает, что новый объект (или описание класса) следует.

## <a name="schema-numbers"></a>Цифры схемы

Номер схемы, который присваивается `IMPLEMENT_SERIAL` классу при возникновении метода класса, является «версией» реализации класса. Схема относится к реализации класса, а не к количеству раз, когда данный объект был сделан стойким (обычно именуемым объектной версией).

Если со временем планируется поддерживать несколько различных реализаций одного и того же класса, `Serialize` то принеобходимости схемы при пересмотре реализации метода объекта позволит написать код, который может загрузить объекты, хранящиеся с помощью старых версий реализации.

Метод `CArchive::ReadObject` будет бросать [CArchiveException,](../mfc/reference/carchiveexception-class.md) когда он сталкивается с номером схемы в постоянном магазине, который отличается от числа схемы описания класса в памяти. Это не легко оправиться от этого исключения.

Вы можете `VERSIONABLE_SCHEMA` использовать в сочетании с (bitwise **OR)** версия схемы, чтобы сохранить это исключение от бросали. Используя, `VERSIONABLE_SCHEMA`ваш код может принять соответствующие меры в своей `Serialize` функции, проверяя значение возврата от [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Вызов сериализировать непосредственно

Во многих случаях накладные расходы `WriteObject` на `ReadObject` общую схему архива объектов и не являются необходимыми. Это распространенный случай сериализации данных в [CDocument](../mfc/reference/cdocument-class.md). В этом случае `Serialize` метод `CDocument` вызова называется непосредственно, а не с экстрактом или вставкой операторов. Содержимое документа, в свою очередь, может использовать более общую схему архивирования объектов.

Вызов `Serialize` непосредственно имеет следующие преимущества и недостатки:

- Дополнительные байты в архив не добавляются до или после сериализации объекта. Это не только делает сохраненные данные `Serialize` меньше, но позволяет реализовать процедуры, которые могут обрабатывать любые форматы файлов.

- MFC настроен так, `WriteObject` чтобы `ReadObject` и реализации и связанные коллекции не будут связаны с вашим приложением, если вам не понадобится более общая схема архива объектов для некоторых других целей.

- Код не должен восстанавливаться после старых номеров схемы. Это делает код сериализации документов ответственным за кодирование номеров схем, номеров версий формата файлов или любых идентификационных номеров, которые вы используете в начале файлов данных.

- Любой объект, который сериализируется с прямым вызовом, не `Serialize` должен использовать `CArchive::GetObjectSchema` или должен обрабатывать возвратное значение (UINT)-1, указывающего на то, что версия неизвестна.

Поскольку `Serialize` он вызывается непосредственно на документе, подобъекты документа обычно не могут архивировать ссылки на их родительский документ. Этим объектам необходимо дать указатель на их контейнерный документ явно или вы должны `CDocument` использовать функцию [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) для картирования указателя на PID до архивирования этих указателей.

Как отмечалось ранее, вы должны кодировать информацию `Serialize` о версии и классе самостоятельно, когда вы звоните напрямую, что позволяет изменить формат позже, сохраняя при этом обратную совместимость со старыми файлами. Функция `CArchive::SerializeClass` может быть вызвана явно перед прямой серизацией объекта или перед вызовом базового класса.

## <a name="see-also"></a>См. также раздел

[Технические примечания по номеру](../mfc/technical-notes-by-number.md)<br/>
[Технические заметки по категориям](../mfc/technical-notes-by-category.md)
