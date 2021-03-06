---
title: Методы дискретизации (интеллектуальный анализ данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- discretization [Analysis Services]
- columns [data mining], discretization
- THRESHOLDS method
- CLUSTERS method
- DiscretizationBuckets property
- AUTOMATIC method
- EQUAL_AREAS method
- coding [Data Mining]
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5e984fe2ea57ab175e3224d099f5392f96287c74
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66084638"
---
# <a name="discretization-methods-data-mining"></a>Методы дискретизации (Интеллектуальный анализ данных)
  Для правильной работы некоторых алгоритмов, используемых для создания моделей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] интеллектуального анализа данных в, требуются определенные типы содержимого. Например, упрощенный алгоритм Байеса [!INCLUDE[msCoName](../../includes/msconame-md.md)] не может использовать непрерывные столбцы на входе и прогнозировать непрерывные значения. Кроме того, некоторые столбцы могут содержать так много значений, что алгоритм будет не в состоянии легко выявить содержательные закономерности в данных, из которых создается модель.  
  
 В таких случаях можно дискретизировать данные в столбцах, чтобы воспользоваться алгоритмами для выработки модели интеллектуального анализа данных. *Дискретизация* — это процесс помещения значений в сегменты, чтобы существовало ограниченное количество возможных состояний. С самими сегментами обращаются как с упорядоченными дискретными значениями. Можно дискретизировать как численные, так и строковые столбцы.  
  
 Существует несколько способов дискретизации данных. Если в решении по интеллектуальному анализу данных используются реляционные данные, можно ограничить число сегментов, используемых для группирования данных, задав свойство <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> . Число сегментов по умолчанию равно 5.  
  
 Если в решении интеллектуального анализа данных используются данные из куба оперативной аналитической обработки (OLAP), то алгоритм интеллектуального анализа данных автоматически вычислит число создаваемых сегментов по следующей формуле, где n — это число уникальных значений данных в столбце:  
  
 `Number of Buckets = sqrt(n)`  
  
 Если вам не нужно, чтобы службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] вычисляли число сегментов, можно воспользоваться свойством <xref:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount%2A> и указать число сегментов вручную.  
  
 Следующая таблица описывает методы, которые можно использовать для дискретизации данных в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Метод дискретизации|Description|  
|---------------------------|-----------------|  
|`AUTOMATIC`|
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] определяют, какой метод дискретизации использовать.|  
|`CLUSTERS`|Алгоритм разделяет данные на группы путем создания выборки обучающих данных, инициализации по ряду случайных точек и дальнейшего запуска несколько итераций алгоритма кластеризации (Майкрософт) с помощью метода кластеризации с максимизацией ожидания (EM). Метод `CLUSTERS` полезен, так как он работает с любой кривой распределения. Однако он требует большего времени на обработку, чем другие методы дискретизации.<br /><br /> Этот метод можно использовать только для числовых столбцов.|  
|`EQUAL_AREAS`|Алгоритм делит данные на группы, содержащие равное число значений. Этот метод лучше всего использовать для кривых нормального распределения, но он не работает, если распределение содержит большое число значений, встречающихся в узкой группе непрерывных данных. Например, если половина элементов имеет значение цены 0, то половина данных окажется в одной точке кривой. При таком распределении, этот метод разрушит данные в попытке установить равномерную дискретизацию по нескольким областям. Это вызовет неточное представление данных.|  
  
## <a name="remarks"></a>Remarks  
  
-   Можно использовать метод `EQUAL_AREAS` для дискретизации строк.  
  
-   Метод `CLUSTERS` использует случайную выборку из 1 000 записей для дискретизации данных. Используйте метод `EQUAL_AREAS`, если не нужно, чтобы алгоритм отбирал данные.  
  
-   В учебнике по модели интеллектуального анализа данных нейронной сети приводится пример пользовательской настройки дискретизации. Дополнительные сведения см. в разделе [занятие 5. Создание моделей нейронной сети и логистической регрессии &#40;учебнике по интеллектуальному анализу данных&#41;](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md).  
  
## <a name="see-also"></a>См. также:  
 [Типы содержимого &#40;&#41;интеллектуального анализа данных](content-types-data-mining.md)   
 [Типы содержимого &#40;расширений интеллектуального анализа данных&#41;](/sql/dmx/content-types-dmx)   
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Структуры интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ&#41;](mining-structures-analysis-services-data-mining.md)   
 [Типы данных &#40;&#41;интеллектуального анализа данных](data-types-data-mining.md)   
 [Столбцы структуры интеллектуального анализа данных](mining-structure-columns.md)   
 [Распределения столбцов &#40;интеллектуального анализа данных&#41;](column-distributions-data-mining.md)  
  
  
