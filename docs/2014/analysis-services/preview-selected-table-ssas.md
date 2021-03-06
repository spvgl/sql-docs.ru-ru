---
title: Предварительный просмотр выбранной таблицы (SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.previewselecttable.f1
ms.assetid: b6b34b5a-43b3-4a75-9f3b-b2ad1084b1b6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0a0f168dabd237fe685eb90d2caeeba0db4eed97
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070722"
---
# <a name="preview-selected-table-ssas"></a>Предварительный просмотр выбранной таблицы (SSAS)
  Эта страница **мастера импорта таблиц** позволяет просмотреть данные в выбранной таблице, выбрать столбцы для включения в импорт данных и отфильтровать данные в выбранных столбцах. Для доступа к мастеру из [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
 В таблице отображаются не все строки. Однако можно настроить фильтры так, чтобы они применялись ко всем данным в таблице во время импорта.  
  
 Для источников данных, в которых используется проверка подлинности Windows, учетные данные текущего пользователя используются для выборки данных, отображаемых в диалоговом окне «Просмотр и фильтрация». Для других источников данных для выборки данных используются учетные данные, указанные в строке подключения.  
  
 Внешний вид данных на этой странице не гарантирует, что импорт будет выполнен успешно. Импорт завершится ошибкой, если имя пользователя, указанное на странице сведений об олицетворении, не имеет достаточных прав для чтения из выбранной базы данных.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Флажок в заголовке столбца**  
 Установите флажок, чтобы включить столбец в импорт данных. Снимите флажок, чтобы не импортировать столбец.  
  
 **Стрелка вниз в заголовке столбца**  
 Фильтровать данные в столбце.  
  
 **Очистить фильтры строк**  
 Удалить все фильтры, примененные к данным в столбцах.  
  
  
