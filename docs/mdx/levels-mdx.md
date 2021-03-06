---
title: 级别 (MDX) |Microsoft 文档
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2fba58261bb0ba8f91e8127b1d33b847accf0dc7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579509"
---
# <a name="levels-mdx"></a>Levels (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  返回由数值表达式指定在维度或层次结构中的位置的级别，或返回由字符串表达式指定名称的级别。  
  
## <a name="syntax"></a>语法  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>参数  
 *Hierarchy_Expression*  
 返回层次结构的有效多维表达式 (MDX)。  
  
 *Level_Number*  
 指定级别号的有效数值表达式。  
  
 *Level_Name*  
 指定级别名称的有效字符串表达式。  
  
## <a name="remarks"></a>Remarks  
 如果指定级别号，则**级别**函数返回与指定的从零开始位置相关联的级别。  
  
 如果指定级别的名称，则**级别**函数将返回指定的级别。  
  
> [!NOTE]  
>  将字符串表达式语法用于用户定义的函数。  
  
## <a name="examples"></a>示例  
 以下示例说明了每个**级别**函数语法。  
  
### <a name="numeric"></a>数字  
 以下示例返回国家（地区）级别：  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 以下示例返回国家（地区）级别：  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
