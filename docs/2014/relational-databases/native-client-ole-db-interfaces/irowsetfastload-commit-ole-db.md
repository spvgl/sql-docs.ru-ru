---
title: 'IRowsetFastLoad:: Commit (OLE DB) | Документация Майкрософт'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e6983eaccf1a934a318c69e72ebdfebf17d2ad9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63224726"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
  Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Примеры см. в разделе [копирование данных использование IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md) и [Отправка данных больших двоичных объектов в SQL Server с помощью IRowsetFastLoad и ISEQUENTIALSTREAM ](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)&#40;OLE DB.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *фдоне*[in]  
 Если значение равно FALSE, то набор строк сохраняет достоверность и может использоваться пользователем для дополнительной вставки строк. Если значение равно TRUE, то набор строк теряет достоверность и пользователь не может выполнять дальнейшую вставку.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод завершился успешно, и все добавленные записи были записаны в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 E_FAIL  
 Произошла ошибка, зависящая от поставщика. Получите сведения об ошибке для конкретного текста ошибки из поставщика.  
  
 E_UNEXPECTED  
 Этот метод был вызван применительно к набору строк массового копирования, который ранее стал недействительным в результате выполнения метода **IRowsetFastLoad::Commit**.  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Собственный клиент OLE DB набор строк с нестандартным копированием поставщика ведет себя как набор строк режима отложенного обновления. По мере вставки пользователем данных строк с помощью набора строк добавленные строки обрабатываются таким же образом, как и ожидающие выполнения вставки для набора строк, поддерживающего **IRowsetUpdate**.  
  
 Пользователь должен вызвать метод **Commit** применительно к набору строк массового копирования, чтобы записать добавленные строки в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таким же образом, как и при использовании метода **IRowsetUpdate::Update** для отправки ожидающих строк в экземпляр SQL Server.  
  
 Если пользователь освобождает ссылку на набор данных массового копирования, не вызывая метод **Commit**, то все добавленные строки, которые не были записаны, теряются.  
  
 Пользователь может сгруппировать добавленные строки, вызывая метод **Commit** с аргументом *fDone* в значении FALSE. Если аргумент *fDone* установлен в значение TRUE, то набор строк становится недействительным. Недействительным набором строк массового копирования поддерживаются только интерфейс **ISupportErrorInfo** и метод **IRowsetFastLoad::Release**.  
  
## <a name="see-also"></a>См. также:  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  
