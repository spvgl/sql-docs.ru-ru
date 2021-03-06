---
title: Инструкции SQL, созданные во время выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8333000c9bb806116244ac6d4f654fa195205868
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107465"
---
# <a name="sql-statements-constructed-at-run-time"></a>Инструкции SQL, сформированные во время выполнения
Приложения, выполняющие автоматизированный анализ, обычно создают инструкции SQL во время выполнения. Например, электронная таблица может позволить пользователю выбирать столбцы, из которых будут извлекаться данные:  
  
```  
// SQL_Statements_Constructed_at_Run_Time.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <sqltypes.h>  
  
int main() {  
   SQLCHAR *Statement = 0, *TableName = 0;  
   SQLCHAR **TableNamesArray, **ColumnNamesArray = 0;  
   BOOL *ColumnSelectedArray = 0;  
   BOOL  CommaNeeded;  
   SQLSMALLINT i = 0, NumColumns = 0;  
  
   // Use SQLTables to build a list of tables (TableNamesArray[]). Let the  
   // user select a table and store the selected table in TableName.  
  
   // Use SQLColumns to build a list of the columns in the selected table  
   // (ColumnNamesArray). Set NumColumns to the number of columns in the  
   // table. Let the user select one or more columns and flag these columns  
   // in ColumnSelectedArray[].  
  
   // Build a SELECT statement from the selected columns.  
   CommaNeeded = FALSE;  
   Statement = (SQLCHAR*)malloc(8);  
   strcpy_s((char*)Statement, 8, "SELECT ");  
  
   for (i = 0 ; i = NumColumns ; i++) {  
      if (ColumnSelectedArray[i]) {  
         if (CommaNeeded)  
            strcat_s((char*)Statement, sizeof(Statement), ",");  
         else  
            CommaNeeded = TRUE;  
         strcat_s((char*)Statement, sizeof(Statement), (char*)ColumnNamesArray[i]);  
      }  
   }  
  
   strcat_s((char*)Statement, 15, " FROM ");  
   // strcat_s((char*)Statement, 100, (char*)TableName);  
  
   // Execute the statement . It will be executed once, do not prepare it.  
   // SQLExecDirect(hstmt, Statement, SQL_NTS);  
}  
```  
  
 Другой класс приложений, которые обычно создают инструкции SQL во время выполнения, — это среды разработки приложений. Однако эти операторы жестко запрограммированы в создаваемом приложении, где их обычно можно оптимизировать и тестировать.  
  
 Приложения, которые создают инструкции SQL во время выполнения, могут обеспечить огромную гибкость для пользователя. Как видно из предыдущего примера, который не поддерживает такие общие операции, как предложения **WHERE** , предложения **ORDER BY** или объединения, построение инструкций SQL во время выполнения гораздо сложнее, чем в инструкциях с жестким кодированием. Более того, тестирование таких приложений проблематично, поскольку они могут создавать произвольное количество инструкций SQL.  
  
 Невозможным недостатком построения инструкций SQL во время выполнения является то, что создание инструкции занимает гораздо больше времени, чем использование жестко заданной инструкции. К счастью, это редко бывает проблемой. Такие приложения, как правило, интенсивно задают пользовательский интерфейс, и время, затрачиваемое приложением на построение инструкций SQL, обычно невелико по сравнению с тем временем, которое пользователь тратит на ввод критериев.
