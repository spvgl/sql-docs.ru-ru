---
title: Использование хранимых процедур (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4daa38f185569e1579413870cc929a8b1b3b6570
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038006"
---
# <a name="using-stored-procedures-mdx"></a>Использование хранимых процедур (многомерные выражения)


  Возможности служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и многомерных выражений можно расширить путем записи хранимых процедур платформы .NET или определяемых пользователем функций. Дополнительные сведения см. в разделе [ADOMD.NET Server Programming](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming) .  
  
 При обращении или вызове хранимой процедуры необходимо указать имя функции и круглые скобки. Внутри скобок можно указать выражения (или аргументы), представляющие собой данные, передаваемые в виде параметров. Вызывая функцию, необходимо указать значения аргументов для всех параметров, причем в той последовательности, в которой параметры перечислены в определении пользовательской функции.  
  
 В следующем примере запроса предполагается, что на сервере служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] зарегистрирована сборка SampleAssembly:  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  *Хранимая процедура* — это терминология [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , используемая в для этих типов функций. Более ранние [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] версии вызывали эти типы функций в качестве *определяемых пользователем функций*.  
  
## <a name="types-of-stored-procedures"></a>Типы хранимых процедур  
 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] поддерживает сборки COM и CLR. Рекомендуется использовать сборки CLR, поскольку для них имеются расширенные механизмы защиты. Если на сервере установлена электронная таблица Microsoft Office Excel, можно также использовать функции Excel.  
  
> [!NOTE]  
>  COM-сборки Microsoft Visual Basic for Applications (VBA) регистрируются автоматически.  
  
## <a name="see-also"></a>См. также:  
 [Функции &#40;синтаксиса многомерных выражений&#41;](../mdx/functions-mdx-syntax.md)  
  
  
