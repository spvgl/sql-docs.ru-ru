---
title: SELECT INTO (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a2e9fb0dfd3607adc1773d4a43561f32ba650ee5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68887676"
---
# <a name="select-into-dmx"></a>SELECT INTO (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Создает новую модель интеллектуального анализа данных на основе структуры интеллектуального анализа данных существующей модели. Инструкция **SELECT INTO** создает новую модель интеллектуального анализа данных путем копирования схемы и других сведений, не относящихся к реальному алгоритму.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SELECT INTO <new model>   
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH[,] [FILTER(<expression>)]]  
FROM <existing model>  
```  
  
## <a name="arguments"></a>Аргументы  
 *новая модель*  
 Уникальное имя для новой создаваемой модели.  
  
 *Microsof*  
 Имя алгоритма интеллектуального анализа данных, определенное поставщиком.  
  
 *список параметров*  
 Необязательный параметр. Список параметров, определенных поставщиком для алгоритма и разделенный запятыми.  
  
 *expression*  
 Выражение, значением которого является действительное условие фильтрации для обучающих данных. Дополнительные сведения о выражениях, которые можно использовать в качестве фильтров, см. в разделе [фильтры для моделей интеллектуального анализа данных &#40;Analysis Services-&#41;интеллектуального анализа ](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
 *Существующая модель*  
 Имя существующей модели для копирования.  
  
## <a name="remarks"></a>Remarks  
 Если существующая модель является обученной, новая модель автоматически обрабатывается при выполнении этой инструкции. В противном случае новая модель оставляется необработанной.  
  
 Инструкция **SELECT INTO** работает только в том случае, если структура существующей модели совместима с алгоритмом новой модели. Следовательно, эта инструкция больше всего подходит для быстрого создания и тестирования моделей, основанных на одном алгоритме. Если изменить тип алгоритма, новый алгоритм должен поддерживать тип данных каждого столбца существующей модели, иначе при обработке модели может произойти ошибка.  
  
 Предложение **WITH DRILLTHROUGH** позволяет выполнять детализацию в новой модели интеллектуального анализа данных. Включить детализацию можно только при создании модели.  
  
## <a name="example-1-altering-the-parameters-of-the-model"></a>Пример 1. изменение параметров модели  
 В следующем примере создается новая модель интеллектуального анализа на основе существующей модели интеллектуального `TM_Clustering`анализа данных, созданной в [учебнике по основам интеллектуального анализа](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). В новой модели параметр CLUSTER_COUNT изменяется так, чтобы существовало максимум пять кластеров. В существующей модели, напротив, используется значение по умолчанию, равное 10.  
  
```  
SELECT * INTO [New_Clustering]  
USING [Microsoft_Clustering] (CLUSTER_COUNT = 5)   
FROM [TM Clustering]  
```  
  
## <a name="example-2-adding-a-filter-to-the-model"></a>Пример 2. Добавление фильтра в модель  
 В следующем примере создается новая модель интеллектуального анализа данных на базе существующей модели интеллектуального анализа данных и к этой модели добавляется фильтр. Фильтр ограничивает обучающие данные тремя клиентами, которые проживают в определенном районе.  
  
```  
SELECT * INTO [Clustering Europe Region]  
USING [Microsoft_Clustering] WITH FILTER(Region='Europe')  
FROM [TM Clustering]  
```  
  
> [!NOTE]  
>  Фильтры, применяемые к таблице вариантов, можно изменить с помощью инструкции SELECT INTO, как показано в данном примере; однако, если исходная модель содержит фильтр для вложенной таблицы, этот фильтр нельзя изменить или удалить с помощью данной синтаксической конструкции; он будет копироваться из исходной модели в неизменном виде. Чтобы создать модели с другим фильтром для вложенной таблицы, используйте синтаксическую конструкцию ALTER STRTUCTURE...ADD MODEL.  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41; DDL](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
