---
title: Вставка изображения из файла
description: Описывает, как работать с изображением из файла.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 613ae5b3326bc49ab25f30628ecd85e13959e2dc
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247743"
---
# <a name="inserting-an-image-from-a-file"></a>Вставка изображения из файла

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Большой двоичный объект (BLOB) можно записать в базу данных в виде двоичных или символьных данных в зависимости от типа поля в источнике данных. Большой двоичный объект — это универсальный термин, который относится к типам данных `text`, `ntext` и `image`, которые обычно содержат документы и изображения.  
  
Чтобы записать значение BLOB в базу данных, выполните соответствующую инструкцию INSERT или UPDATE, передав значение BLOB в качестве входного параметра. Если ваш большой двоичный объект хранится в виде текста, например поле `text` SQL Server, большой двоичный объект можно передать в виде строкового параметра. Если большой двоичный объект хранится в двоичном формате, например в поле `image` SQL Server, массив типа `byte`можно передать как двоичный параметр.
  
## <a name="example"></a>Пример  
В следующем примере кода данные о сотрудниках добавляются в таблицу "Сотрудники" в базе данных Northwind. Фотография сотрудника считывается из файла и добавляется в поле "Фото" в таблице, которая является полем изображения.  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Двоичные данные и данные больших значений SQL Server](sql-server-binary-large-value-data.md)
