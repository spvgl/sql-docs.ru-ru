---
title: Указание механизма параметризации запросов с помощью структур плана
ms.custom: seo-dt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- PARAMETERIZATION FORCED option
- PARAMETERIZATION option
- PARAMETERIZATION SIMPLE option
- parameterization [SQL Server]
- overriding parameterization behavior
- plan guides [SQL Server], parameterization
- parameterized queries [SQL Server]
ms.assetid: f0f738ff-2819-4675-a8c8-1eb6c210a7e6
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 8c4c252de5a9d23ecfbaee06ca6322f3b08b275f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76761891"
---
# <a name="specify-query-parameterization-behavior-by-using-plan-guides"></a>Указание механизма параметризации запросов с помощью структур плана
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Если для параметра базы данных PARAMETERIZATION установлено значение SIMPLE, оптимизатор запросов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может выбрать параметризацию запросов. Это значит, что все литеральные значения, содержащиеся в запросе, заменяются параметрами. Этот процесс называется простой параметризацией. При применении простой (SIMPLE) параметризации невозможно контролировать, какие запросы параметризуются, а какие нет. Однако можно параметризовать все запросы в базе данных, присвоив параметру базы данных PARAMETERIZATION значение FORCED. Этот процесс называется принудительной параметризацией.  
  
 Механизм параметризации в базе данных можно переопределить с помощью структур планов следующим путем.  
  
-   Если значение параметра базы данных PARAMETERIZATION равно SIMPLE, можно указать, чтобы попытки принудительной параметризации выполнялись в определенном классе запросов. Это можно сделать путем создания структуры плана TEMPLATE для параметризованной формы запроса и задания указания запроса PARAMETERIZATION FORCED с помощью хранимой процедуры [sp_create_plan_guide](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md) . Такая разновидность структуры плана представляет собой способ включения принудительной параметризации только для определенного класса запросов, а не для всех. Дополнительные сведения о простой параметризации см. в разделе [Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md#SimpleParam). 
  
-   Если значение параметра базы данных PARAMETERIZATION равно FORCED, можно указать, чтобы для определенного класса запросов выполнялись только попытки простой параметризации вместо принудительной. Это можно сделать путем создания структуры плана TEMPLATE для формы запроса с принудительной параметризацией и задания указания запроса PARAMETERIZATION SIMPLE с помощью хранимой процедуры **sp_create_plan_guide**.  Дополнительные сведения о принудительной параметризации см. в разделе [Руководство по архитектуре обработки запросов](../../relational-databases/query-processing-architecture-guide.md#ForcedParam). 
  
 Рассмотрим следующий запрос к базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
```sql  
SELECT pi.ProductID, SUM(pi.Quantity) AS Total  
FROM Production.ProductModel AS pm   
    INNER JOIN Production.ProductInventory AS pi   
        ON pm.ProductModelID = pi.ProductID   
WHERE pi.ProductID = 101   
GROUP BY pi.ProductID, pi.Quantity HAVING SUM(pi.Quantity) > 50;  
```  
  
 Администратор базы данных решил не включать принудительную параметризацию для всех запросов к базе данных. Однако необходимо избегать затрат на компиляцию для всех запросов, синтаксически эквивалентных предыдущему и различающихся только литеральными значениями констант. Иными словами, необходимо реализовать параметризацию запроса таким образом, чтобы план для данного вида запроса использовался повторно. В этом случае нужно выполнить следующее.  
  
1.  Получить параметризованную форму запроса. Единственным безопасным путем получения этого значения для последующего использования в процедуре **sp_create_plan_guide** является использование системной хранимой процедуры [sp_get_query_template](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md) .  
  
2.  Создать структуру плана для параметризованной формы запроса, задав указание запроса PARAMETERIZATION FORCED.  

    > [!IMPORTANT]  
    >  В ходе параметризации запроса [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присваивает параметрам, заменяющим литеральные значения, определенный тип данных в зависимости от значения и размера литерала. Подобный процесс выполняется и для значений констант-литералов, передаваемых в качестве выходного параметра **\@stmt** процедуры **sp_get_query_template**. Так как тип данных, указанный в аргументе **\@params** процедуры **sp_create_plan_guide**, должен соответствовать типу данных в запросе после его параметризации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], может потребоваться создание нескольких структур планов для охвата всего диапазона возможных значений параметров запроса.  

Следующий скрипт можно использовать как для получения параметризированного запроса, так и для дальнейшего создания по нему структуры плана:  
  
```sql  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT pi.ProductID, SUM(pi.Quantity) AS Total   
      FROM Production.ProductModel AS pm   
      INNER JOIN Production.ProductInventory AS pi ON pm.ProductModelID = pi.ProductID   
      WHERE pi.ProductID = 101   
      GROUP BY pi.ProductID, pi.Quantity   
      HAVING sum(pi.Quantity) > 50',  
    @stmt OUTPUT,   
    @params OUTPUT;  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
Подобным образом в базе данных, в которой уже включена принудительная параметризация, можно гарантировать, что указанный в качестве примера запрос и другие синтаксически ему эквивалентные, в которых различаются только литеральные значения констант, будут параметризованы согласно правилам простой параметризации. Для этого следует указать PARAMETERIZATION SIMPLE вместо PARAMETERIZATION FORCED в предложении OPTION.  
  
> [!NOTE]  
>  С помощью структур плана TEMPLATE осуществляется сопоставление инструкций с запросами, поступающими в пакетах, каждый из которых состоит только из одной инструкции. Инструкции, находящиеся в пакетах с несколькими инструкциями, не подлежат сопоставлению со структурами планов TEMPLATE.
