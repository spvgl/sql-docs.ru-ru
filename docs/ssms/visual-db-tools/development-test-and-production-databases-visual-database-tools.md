---
title: Базы данных для разработки, тестирования и производства
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- production databases [SQL Server]
- testing databases
- database testing [SQL Server]
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 2b055385ca5ee06b0fba1c87376835b16695ef57
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251826"
---
# <a name="development-test-and-production-databases-visual-database-tools"></a>Базы данных для разработки, тестирования и производства (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
В случае, когда две базы данных обладают одинаковыми структурами, изменения в одной базе данных можно распространить на вторую. Например, если имеется личная база данных для разработки и база данных для совместного тестирования, можно изменить первую базу данных и распространить эти изменения в тестовую базу данных.  
  
Для этого в базе данных, предназначенной для разработки, выполните все модификации за один сеанс, создайте скрипт изменения этого сеанса и выполните данный скрипт в базе данных, предназначенной для тестирования.  
  
## <a name="see-also"></a>См. также:  
[Многопользовательские среды (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/multiuser-environments-visual-database-tools.md)  
  
