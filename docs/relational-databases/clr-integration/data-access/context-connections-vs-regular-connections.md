---
title: Обычные и контекстные соединения | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: 69733cbf3357ba26dc9e9fdf818858dc4e747b99
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138711"
---
# <a name="context-connections-vs-regular-connections"></a>Контекстные соединения и обычные соединения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При соединении с удаленным сервером всегда пользуйтесь обычными, а не контекстными соединениями. Если нужно подключиться к тому же серверу, на котором выполняется хранимая процедура или функция, в большинстве случаев используется контекстное соединение. Преимущества заключаются в выполнении приложений в одной области транзакций и отсутствии необходимости повторной проверки подлинности имени входа.  
  
 Кроме того, использование контекстного соединения обычно приводит к повышению производительности при меньшем потреблении ресурсов. Контекстное соединение является подключением только для обработки, поэтому оно может напрямую связаться с сервером, обходя сетевой протокол и транспортные уровни, чтобы отправлять инструкции Transact-SQL и получать результаты. Также обходится процесс проверки подлинности. На следующем рисунке показаны основные компоненты управляемого поставщика **SqlClient** , а также, как различные компоненты взаимодействуют друг с другом при использовании обычного соединения и при использовании контекстного соединения.  
  
 ![Кодовые пути контекстного и обычного соединений.](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Кодовые пути контекстного и обычного соединений.")  
  
 Контекстное соединение требует более короткого кода и меньшего числа компонентов, поэтому запрос к серверу, как и получение результатов, происходит быстрее, чем при обычном соединении. Время выполнение запроса на сервере остается одинаковым для контекстных и обычных соединений.  
  
 В некоторых случаях, возможно, потребуется открыть отдельное обычное соединение с тем же сервером. Например, существуют определенные ограничения на использование контекстного соединения, описанные в разделе [ограничения для обычных и контекстных соединений](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>См. также:  
 [Контекстное соединение](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
