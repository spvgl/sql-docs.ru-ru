---
title: Создание файлов переменных значений (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Variable Value File Creation
- Variable Value File, Variable Value File Validation
ms.assetid: f583d81a-8e34-41b1-8100-ee3a6a82213b
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 87db0ebd006e2ca87ddc4744a4bbcd396a827712
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266124"
---
# <a name="creating-variable-value-files-oracletosql"></a>Создание файлов переменных значений (OracleToSQL)
Файл значения переменной — это XML-файл, состоящий из значений параметров таких команд, как, имя исходного или целевого сервера, которое часто меняются при миграции с одного сервера на другой. При выполнении большого количества миграций базы данных создается несколько переменных файлов для хранения значений каждого исходного сервера и на них указывают ссылки в файле главного сценария с помощью параметра **-v** в командной строке. Это помогает поддерживать статические значения в нескольких файлах скриптов с переменными значениями в нескольких файлах переменных.  
  
> [!NOTE]  
> 1.  Имена переменных добавляются с префиксом в символ $ (доллар). Если переменным не присвоено значение в файле значения переменной, то во время синтаксического анализа файла скрипта будет возникать ошибка, что привело к остановке процесса выполнения консоли.  
> 2.  Escape-символ для **$** имеет **$$** значение. Если значение переменной или статического значения параметра содержит **$** символ (доллар), то **$$** необходимо указать, что он будет обрабатываться как символ, а не как переменная.  
> 3.  Для целей обслуживания переменные могут быть объявлены внутри `'variable-group'` элементов для логического разделения определяемых пользователем переменных.  Использование этого элемента не является обязательным.  
  
**Примеры:**  
  
**Пример 1:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**Пример 2.**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>Дальнейшее действие  
Следующий шаг в работе консоли — [Создание файлов подключения к серверу &#40;OracleToSQL&#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
## <a name="see-also"></a>См. также:  
[Создание серверных файлов (Oracle)](https://msdn.microsoft.com/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  
