---
title: Рекомендации и ограничения диаграмм обновления (SQLXML)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9eb717968b191bb7d80f5d68542178bf32734b00
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75241300"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Правила и ограничения диаграмм обновления XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  При использовании диаграмм обновления XML следует помнить следующее.  
  
-   Если вы используете диаграмма обновления для операции вставки с одной парой ** \<до>** и ** \<после блоков>** , то ** \<блок Before>** можно опустить. И наоборот, в случае операции удаления блок ** \<After>** можно опустить.  
  
-   Если вы используете диаграмма обновления с несколькими ** \<>** и ** \<после>ных** блоков в теге ** \<>синхронизации** , ** \<перед** ** \<>** и ** \<после**>ных пар необходимо ** \<** указать оба блока>и After>.  
  
-   Обновления в диаграммах обновления применяются к XML-представлению, предоставленному схемой XML. Поэтому для успешного сопоставления по умолчанию следует либо указать имя файла схемы в диаграмме обновления, либо, если имя файла не указано, имена элемента и атрибута должны совпадать с именами таблицы и столбца базы данных.  
  
-   SQLXML 4.0 требует, чтобы все значения столбцов в диаграмме обновления были бы явно сопоставлены в схеме (XDR или XSD), предоставленной для создания XML-представления для дочерних элементов. Это поведение отличается от предыдущих версий SQLXML, которые позволяли использовать значение для столбца, не сопоставленного в схеме, если он был указан как часть внешнего ключа в заметке **SQL: relationship** . (Следует отметить, что подобное изменение не повлияет на распространение значений первичного ключа на дочерние элементы, которое по-прежнему происходит в SQLXML 4.0, если явно не указано значение для дочернего элемента.  
  
-   Если вы используете диаграмма обновления для изменения данных в двоичном [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] столбце (например, тип данных **Image** ), необходимо указать схему сопоставления, в которой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должен быть указан тип данных (например, **SQL: datatype = "Image"**) и тип данных XML (например, **DT: Type = "BinHex"** или **DT: Type = "binbase64)"**. Данные для двоичного столбца должны быть указаны в диаграмма обновления; заметка **SQL: URL-encoded** , указанная в схеме сопоставления, игнорируется диаграмма обновления.  
  
-   Если при написании схемы XSD значение, указанное для заметки **SQL: relation** или **SQL: field** , содержит специальный символ, например символ пробела (например, в имени таблицы "сведения о заказе"), это значение должно быть заключено в квадратные скобки (например, "[Order Details]").  
  
-   При использовании диаграмм обновления цепочки связей не поддерживаются. Например, если таблицы А и С связаны через цепочку связей, которая использует таблицу В, при попытке запустить и выполнить диаграмму обновления возникнет следующая ошибка:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Даже если как схема, так и диаграмма обновления верны и правильно оформлены, эта ошибка возникнет, если имеется цепочка связей.  
  
-   Диаграмм обновления не допускают передачи данных типа **изображения** в качестве параметров во время обновления.  
  
-   Типы больших двоичных объектов (BLOB), такие как **Text/ntext** и Images, не следует использовать в блоке ** \<Before>** в при работе с диаграмм обновления, так как он будет включать их для использования в управлении параллелизмом. Это может вызвать проблемы в работе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из-за ограничений, налагаемых на сравнение для типов больших двоичных объектов. Например, ключевое слово LIKE используется в предложении WHERE для сравнения столбцов типа данных **Text** . Однако в случае с типами больших двоичных объектов, где размер данных превышает 8 КБ, сравнение завершится ошибкой.  
  
-   Специальные символы в данных типа **ntext** могут вызвать проблемы с SQLXML 4,0 из-за ограничений на сравнение типов больших двоичных объектов. Например, использование "[Serializable]" в блоке ** \<Before>** диаграмм обновления при использовании в проверке параллелизма столбца типа **ntext** приведет к сбою со следующим описанием ошибки SQLOLEDB:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Вопросы безопасности диаграмма обновления &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
