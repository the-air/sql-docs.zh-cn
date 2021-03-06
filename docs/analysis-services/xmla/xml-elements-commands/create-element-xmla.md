---
title: 创建元素 (XMLA) |Microsoft 文档
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 78cdf8b38828e8b9f96a89ffc026ec39ae40366b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2018
ms.locfileid: "34574569"
---
# <a name="create-element-xmla"></a>Create 元素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  包含所使用的 Analysis Services 脚本语言 (ASSL) 元素**执行**方法来创建 Analysis Services 实例上的对象。  
  
## <a name="syntax"></a>语法  
  
```xml  
  
<Command>  
   <Create Scope="enum" AllowOverwrite="boolean">  
      <ParentObject>...</ParentObject>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Create>  
</Command>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|Description|  
|--------------------|-----------------|  
|数据类型和长度|InclusionThresholdSetting|  
|默认值|InclusionThresholdSetting|  
|基数|0-n：可多次出现的可选元素。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子元素|[ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)， [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md)|  
  
## <a name="attributes"></a>属性  
  
|Attribute|Description|  
|---------------|-----------------|  
|AllowOverwrite|可选的 **Boolean** 属性。 如果设置为 True，对象中定义的**ObjectDefinition**元素可以覆盖现有对象上[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]实例。 如果忽略此属性或将其设置为 False，则存在现有对象时将生成一个错误。|  
|范围|可选**枚举**属性。 定义中定义的对象的持续时间**ObjectDefinition**元素。 如果省略此属性，在定义对象**ObjectDefinition**元素会保留在[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]实例。 下面的值有：<br /><br /> *会话*： 中定义的对象**ObjectDefinition**元素只存在于 Analysis (XMLA) 会话的 xml 的持续时间。<br />                  请注意，当使用*会话*设置， **ObjectDefinition**元素只能包含[维度](../../../analysis-services/scripting/objects/dimension-element-assl.md)，[多维数据集](../../../analysis-services/scripting/objects/cube-element-assl.md)，或[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) ASSL 元素。|  
  
## <a name="remarks"></a>Remarks  
 每个**创建**操作创建给定一个父级下的一个主要对象**ParentObject**元素。 如果忽略该父对象，则会将它假定为目标 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 实例。 如果主要对象的父级不是目标实例，则会产生错误。  
  
## <a name="example"></a>示例  
 下面的示例创建名为一个空数据库**测试数据库**上[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]实例。  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>另请参阅
 [命令&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
