---
title: Арифметические выражения (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- expressions [XQuery], arithmetic
- arithmetic expressions
ms.assetid: 90d675bf-56da-459a-9771-8cd13920a9fc
author: rothja
ms.author: jroth
ms.openlocfilehash: ccbeda01726a3473f8e955676c3ebd62a93fd630
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985735"
---
# <a name="arithmetic-expressions-xquery"></a>Арифметические выражения (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Поддерживаются все арифметические операторы, за исключением **идив**. Следующие примеры иллюстрируют использование арифметических операторов:  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 Поскольку **идив** не поддерживается, решение заключается в использовании конструктора **xs: integer ()** :  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 Тип результата арифметического оператора зависит от типов входных значений. Если операнды имеют различные типы, то при необходимости они будут приведены к общему базовому типу в соответствии с иерархией типов. Сведения об иерархии типов см. [в разделе правила приведения типов в XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 Если обе операции имеют различные числовые базовые типы, то проводится преобразование типов. Например, при добавлении **xs: decimal** к **типу xs: Double** сначала необходимо изменить десятичное значение на Double. Затем выполняется операция сложения, в результате которой получается значение типа double.  
  
 Нетипизированные атомарные значения приводятся к числовому базовому типу другого операнда или к типу **xs: Double** , если другой операнд также имеет нетипизированный тип.  
  
## <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Аргументы арифметических операторов должны иметь числовой тип или **untypedAtomic**.  
  
-   Операции с значениями **xs: integer** приводят к значению типа **xs: decimal** вместо **xs: integer**.  
  
  
