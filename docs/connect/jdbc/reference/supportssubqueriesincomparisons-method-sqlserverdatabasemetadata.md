---
title: Метод supportsSubqueriesInComparisons (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSubqueriesInComparisons
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 467d32e6-b47e-4095-9f8b-73e07fb814e8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6766181d669498dedd09a475d75315cb2770f414
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67968751"
---
# <a name="supportssubqueriesincomparisons-method-sqlserverdatabasemetadata"></a>Метод supportsSubqueriesInComparisons (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных вложенные запросы в выражениях сравнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsSubqueriesInComparisons()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsSubqueriesInComparisons указывается с помощью метода supportsSubqueriesInComparisons в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
