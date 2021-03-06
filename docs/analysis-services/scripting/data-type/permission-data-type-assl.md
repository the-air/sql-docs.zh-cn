---
title: 权限数据类型 (ASSL) |Microsoft 文档
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7a7e400a8fbdca47ff678e8b02c89064771c9450
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="permission-data-type-assl"></a>Permission 数据类型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  定义一个抽象的基元数据类型，该类型表示单个权限的相关信息。  
  
## <a name="syntax"></a>語法  
  
```xml  
  
<Permission>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreateTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <RoleID>...</RoleID>  
   <Description>...</Description>  
   <Process>...</Process>  
   <ReadDefinition>...</ReadDefinition>  
   <Read>...</Read>  
   <Write>...</Write>  
   <Annotations>...</Annotations>  
</Permission>  
```  
  
## <a name="data-type-characteristics"></a>数据类型特征  
  
|特征|说明|  
|--------------------|-----------------|  
|基本数据类型|无|  
|派生数据类型|[CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md)， [DatabasePermission](../../../analysis-services/scripting/objects/databasepermission-element-assl.md)， [DimensionPermission](../../../analysis-services/scripting/data-type/dimensionpermission-data-type-assl.md)， [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)， [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
  
## <a name="data-type-relationships"></a>数据类型关系  
  
|关系|元素|  
|------------------|-------------|  
|父元素|无|  
|子元素|[批注](../../../analysis-services/scripting/collections/annotations-element-assl.md)， [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)，[说明](../../../analysis-services/scripting/properties/description-element-assl.md)， [ID](../../../analysis-services/scripting/properties/id-element-assl.md)， [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)，[名称](../../../analysis-services/scripting/properties/name-element-assl.md)，[过程](../../../analysis-services/scripting/properties/process-element-assl.md)，[读取](../../../analysis-services/scripting/properties/read-element-assl.md)， [ReadDefinition](../../../analysis-services/scripting/properties/readdefinition-element-assl.md)， [RoleID](../../../analysis-services/scripting/properties/roleid-element-assl.md)，[编写](../../../analysis-services/scripting/properties/write-element-assl.md)|  
|派生元素|無|  
  
## <a name="remarks"></a>注释  
 **权限**用作派生的权限类型的实例中使用大量的抽象基类型[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]。  
  
 此数据类型在 DeploymentMode 值 2（表格服务器模式）下具有以下验证。  
  
-   *进程*属性默认值设置为**False**，当用户具有除**刷新**权限。 具有的用户**刷新**权限*过程*属性值设置为**True**。  
  
-   *ReadDefinition*属性值设置为**无**; 任何其他值生成一个错误。  
  
-   *读取*属性值设置为**允许**具有的用户**用户**权限并对其**无**时将用户分配给**刷新**权限; 如果用户具有**用户**和**刷新**权限，则该属性设置为**允许**。 对于具有管理权限的用户的属性值设置为**允许**。  
  
-   *编写*属性值设置为**无**; 任何其他值生成一个错误。  
  
 分析管理对象 (AMO) 对象模型中的相应元素是<xref:Microsoft.AnalysisServices.Permission>。  
  
## <a name="see-also"></a>另请参阅  
 [Role 元素 & #40;ASSL & #41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Analysis Services 脚本语言 XML 数据类型 & #40;ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
