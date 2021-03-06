---
title: Инструкция UPDATE CUBE (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f52dd59b67b42ad430df9bb1e9d00dce7ad6d697
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68003527"
---
# <a name="mdx-data-manipulation---update-cube"></a>Операции с данными многомерных выражений — UPDATE CUBE


  Инструкция UPDATE CUBE используется для обратной записи данных в любую ячейку куба, которая суммируется с родительским элементом с помощью агрегатного выражения SUM. Дополнительные сведения и пример см. в подразделе «общее представление о выделении» этой записи блога: [Создание приложения обратной записи с Analysis Services (блог)](https://go.microsoft.com/fwlink/?LinkId=394977).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATE [ CUBE ] Cube_Name   
   SET   
            <update clause>   
           [, <update clause> ...n ]  
  
<update clause> ::=   
      Tuple_Expression[.VALUE]= New_Value  
      [   
        USE_EQUAL_ALLOCATION   
        | USE_EQUAL_INCREMENT   
        | USE_WEIGHTED_ALLOCATION [ BY Weight_Expression]   
        | USE_WEIGHTED_INCREMENT [ BY Weight_Expression]  
      ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, возвращающее имя куба.  
  
 *Tuple_Expression*  
 Допустимое многомерное выражение, возвращающее кортеж.  
  
 *New_Value*  
 Допустимое числовое выражение.  
  
 *Weight_Expression*  
 Допустимое числовое многомерное выражение, возвращающее десятичное значение от 0 до 1.  
  
## <a name="remarks"></a>Remarks  
 Можно обновить значение указанной конечной или неконечной ячейки куба, по желанию размещая значение для указанной неконечной ячейки в зависимых конечных ячейках. Ячейка, указанная кортежным выражением, может представлять любую ячейку многомерного пространства (другими словами, ячейка необязательно должна быть конечной). Однако ячейка должна быть агрегирована с помощью статистической функции [Sum](../mdx/sum-mdx.md) и не должна содержать вычисляемый элемент в кортеже, который используется для его обнаружения.  
  
 Может оказаться полезным рассматривать инструкцию **Update Cube** как подпрограммы, которая автоматически создает ряд отдельных операций обратной записи в ячейках для конечных и неконечных ячеек, которые будут сведены в указанную сумму.  
  
 Ниже приведено описание методов выделения.  
  
 **USE_EQUAL_ALLOCATION:** Каждой конечной ячейке, которая участвует в обновленной ячейке, будет присвоено значение равенства, основанное на следующем выражении.  
  
```  
<leaf cell value> =   
<New Value> / Count(leaf cells that are contained in <tuple>)  
```  
  
 **USE_EQUAL_INCREMENT:** Каждая конечная ячейка, которая участвует в обновленной ячейке, будет изменена в соответствии со следующим выражением.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value > - <existing value>) /  
Count(leaf cells contained in <tuple>)  
```  
  
 **USE_WEIGHTED_ALLOCATION:** Каждой конечной ячейке, которая участвует в обновленной ячейке, будет присвоено значение равенства, основанное на следующем выражении.  
  
```  
<leaf cell value> = < New Value> * Weight_Expression  
```  
  
 **USE_WEIGHTED_INCREMENT:** Каждая конечная ячейка, которая участвует в обновленной ячейке, будет изменена в соответствии со следующим выражением.  
  
```  
<leaf cell value> = <leaf cell value> +   
(<New Value> - <existing value>)  * Weight_Expression  
```  
  
 Если выражение веса не указано, инструкция **Update Cube** неявно использует следующее выражение.  
  
```  
Weight_Expression = <leaf cell value> / <existing value>  
```  
  
 Выражение веса должно быть отображено как десятичное значение от нуля (0) до 1. Оно определяет ту часть размещаемого значения, которую требуется присвоить конечным ячейкам, участвующим в размещении. Задачей программиста клиентского приложения является создание выражений, статистических значений, свертки которых будут равны размещаемому значению выражения.  
  
> [!CAUTION]  
>  Клиентское приложение должно выполнять размещение во всех измерениях параллельно, чтобы избежать возможных непредвиденных результатов, в том числе неправильных значений свертки или несогласованности данных.  
  
 Каждое распределение **куба обновления** должно считаться атомарным для транзакционных целей. Это означает, что в случае сбоя при выполнении одной из операций размещения по какой-либо причине (например, вследствие ошибки в формуле или нарушения защиты), вся инструкция UPDATE CUBE завершается ошибкой. Перед обработкой вычислений отдельных операций размещения создается моментальный снимок данных, что обеспечивает правильность итоговых вычислений.  
  
> [!CAUTION]  
>  При использовании для меры, содержащей целые значения, метод USE_WEIGHTED_ALLOCATION может возвращать неточные результаты, что обусловлено округлениями при приращениях.  
  
> [!IMPORTANT]  
>  Если обновленные ячейки не пересекаются, свойство строки подключения **Update Isolation Level** может быть использовано для повышения производительности инструкции UPDATE CUBE.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [Инструкции обработки данных многомерных выражений &#40;многомерные выражения&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
