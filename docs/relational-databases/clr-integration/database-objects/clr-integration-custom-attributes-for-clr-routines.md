---
title: "Настраиваемые атрибуты для процедур CLR значением | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
caps.latest.revision: "82"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d1ddfeafa4d4b678a9fb20bb597e9fd041bb201
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>Пользовательских атрибутах интеграции со средой CLR для процедур CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Перечисленные атрибуты могут применяться для общих подпрограмм языка среды CLR, определяемые пользователем типы и определяемые пользователем статистические функции, которые зарегистрированы в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если атрибут не применен, то [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предполагает значение по умолчанию. Перечисленные атрибуты определены в **Microsoft.SqlServer.Server** пространства имен.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Атрибут SqlUserDefinedAggregate  
 **SqlUserDefinedAggregate** атрибут указывает, что метод должен быть зарегистрирован как определяемой пользователем статистической функции. Каждое пользовательское статистическое выражение должно иметь этот атрибут.  
  
 Дополнительные сведения см. в разделе [SqlUserDefinedAggregateAttribute](http://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Атрибут SqlFunction  
 **SqlFunction** атрибут указывает, метод должен быть зарегистрирован как функция, с соответствующим функции набором атрибутов.  
  
 Дополнительные сведения см. в разделе [SqlFunctionAttribute](http://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Атрибут SqlFacet  
 **SqlFacet** атрибут используется для возврата сведений о возвращаемом типе выражения определяемого пользователем типа (UDT).  
  
 Дополнительные сведения см. в разделе [SqlFacetAttribute](http://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Атрибут SqlProcedure  
 **SqlProcedure** атрибут указывает, метод должен быть зарегистрирован как хранимая процедура. Этот атрибут используется только в среде Visual Studio для автоматической регистрации указанного метода как хранимой процедуры. В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не используется.  
  
 Дополнительные сведения см. в разделе [SqlProcedureAttribute](http://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Атрибут SqlTrigger  
 **SqlTrigger** атрибут указывает, метод должен быть зарегистрирован как триггер.  
  
 Дополнительные сведения см. в разделе [SqlTriggerContext](http://go.microsoft.com/fwlink/?LinkId=128022) и [SqlTriggerAttribute](http://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 К определению класса в сборке можно применить SqlUserDefinedTypeAttribute. В результате этого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] создает определяемый пользователем тип, привязанный к определению класса с этим пользовательским атрибутом.  
  
 Дополнительные сведения см. в разделе [SqlUserDefinedTypeAttribute](http://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Атрибут SqlMethod  
 **SqlMethod** атрибут используется для указания свойства доступа детерминизм и данные для метода или свойства определяемого пользователем типа.  
  
 Дополнительные сведения см. в разделе [SqlMethodAttribute](http://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>См. также:  
 [Определяемые пользователем статистические функции CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Определяемые пользователем функции CLR](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Определяемые пользователем типы среды CLR](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Хранимые процедуры CLR](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [Триггеры CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  