---
title: rsModelGenerationError — ошибка служб Reporting Services | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 870f1fbc49e99e2cd43c6adb857137776c275550
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65574088"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a>rsModelGenerationError - Ошибка службы Reporting Services
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|rsRenderingError|  
|Источник события|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Компонент|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Текст сообщения|Во время построения модели произошла ошибка. (rsModelGenerationError) (ReportingServicesLibrary) %1|  
  
## <a name="explanation"></a>Объяснение  
 Невозможно сформировать модель отчета. В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 с пакетом обновления 1 (SP1) и ранее эта ошибка обычно происходит в том случае, если объекту System.Data.DataSet не удается обработать таблицу или связь в схеме базы данных, например когда для одного и того же столбца таблицы определены два внешних ключа.  
  
## <a name="user-action"></a>Действие пользователя  
 Для определения причины ошибки просмотрите файлы журналов сервера отчетов, расположенные в папке \Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles.  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
