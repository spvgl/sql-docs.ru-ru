---
title: ToggleDrillState (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8d027a76a82de3fd82b6c0c81c54ace08167039b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036609"
---
# <a name="toggledrillstate-mdx"></a>ToggleDrillState (многомерные выражения)


  Переключает состояние детализации элементов между режимами углубленной детализации и свертки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ToggleDrillState(Set_Expression1,Set_Expression2 [, [RECURSIVE] [,INCLUDE_CALC_MEMBERS] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Set_Expression1*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Set_Expression2*  
 Допустимое многомерное выражение, возвращающее набор.  
  
 *Рекурсивного*  
 (необязательно). Ключевое слово, которое обозначает рекурсивное сравнение наборов. Функция **ToggleDrillState** представляет собой сочетание функций **DrillupMember** и **DrilldownMember** . Рекурсия применяется только в том случае, если элемент находится в состоянии **DrilldownMember** .  
  
 *Include_calc_members*  
 (необязательно). Флажок, указывающий, следует ли включать вычисленные элементы и должны ли они существовать на уровне детализации углублением.  
  
## <a name="remarks"></a>Remarks  
 Функция **ToggleDrillState** переключает состояние детализации каждого элемента второго набора, присутствующего в первом наборе. Первый набор может содержать кортежи любой размерности, однако второй набор должен содержать элементы одного измерения. Функция **ToggleDrillState** представляет собой сочетание функций **DrillupMember** и **DrilldownMember** . Если элемент *m*второго набора представлен в первом наборе, а этот элемент детализирован вниз (то есть он содержит потомка, сразу после него), то `DrillupMember(Set_Expression1, {m})` применяется к элементу или кортежу в первом наборе. Если элемент *m* детализирован вверх (то есть нет потомка *m* , которая сразу после *m*), `DrilldownMember(Set_Expression1, {m}[, RECURSIVE])` применяется к первому набору.  
  
 Если используется дополнительный **рекурсивный** флаг, детализация и детализация применяются рекурсивно. Дополнительные сведения о рекурсивном флаге см. в разделе функции [DrillupMember](../mdx/drillupmember-mdx.md) и [DrilldownMember](../mdx/drilldownmember-mdx.md) .  
  
 Запрос свойства XMLA Мдпропмдксдриллфунктионс позволяет проверить уровень поддержки, предоставляемый сервером для функций сверления; Дополнительные сведения см. в разделе [Поддерживаемые свойства xmla &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) .  
  
 См. раздел [Журнал базы данных: функции наборов многомерных выражений: Функция ToggleDrillState ()](https://go.microsoft.com/fwlink/?LinkId=517759) для сценариев и примеров, использующих эту функцию.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется детализация углублением элемента Australia в первом наборе и детализация обобщением элемента United States в первом наборе.  
  
```  
SELECT ToggleDrillState  
   ({[Geography].[Geography].[Country].Members, [Geography].[Geography].[Country].&[United States].Children},  
      {[Geography].[Geography].[Country].[Australia]  
      , [Geography].[Geography].[Country].&[United States]}  
      --, recursive  
      --, include_calc_members  
   ) ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>См. также:  
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)  
  
  
