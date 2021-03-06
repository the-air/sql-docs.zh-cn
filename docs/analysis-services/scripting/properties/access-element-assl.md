---
title: 访问元素 (ASSL) |Microsoft 文档
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 00bcd1f7cb86e66f521c0dd95c265225f4cf1ef1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="access-element-assl"></a>Access 元素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指示提供给访问级别[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)元素。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<CellPermission>  
   ...  
   <Access>...</Access>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|说明|  
|--------------------|-----------------|  
|数据类型和长度|String（枚举）|  
|默认值|无|  
|基数|0-1：可出现一次且仅出现一次的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[CellPermission](../../../analysis-services/scripting/objects/cellpermission-element-assl.md)|  
|子元素|无|  
  
## <a name="remarks"></a>注释  
 此元素的值被限制为下表中列出的字符串之一。  
  
|“值”|Description|  
|-----------|-----------------|  
|*读取*|允许只读访问。|  
|*ReadContingent*|允许有条件读取访问。|  
|*ReadWrite*|允许读写访问。|  
  
 对应于的允许值为枚举**访问**在分析管理对象 (AMO) 对象模型并<xref:Microsoft.AnalysisServices.CellPermissionAccess>。  
  
## <a name="see-also"></a>另请参阅  
 [Role 元素 & #40;ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [属性 & #40;ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
