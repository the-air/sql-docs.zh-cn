---
title: 组对象 (ADOX) |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Group
helpviewer_keywords:
- group object [ADOX]
ms.assetid: 55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6cd3ef59e5a3d8a1a8e0a0e63d0e01d7a1f79e59
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="group-object-adox"></a>组对象 (ADOX)
表示具有受保护的数据库内的访问权限的组帐户。  
  
## <a name="remarks"></a>注释  
 [组](../../../ado/reference/adox-api/groups-collection-adox.md)集合[目录](../../../ado/reference/adox-api/catalog-object-adox.md)表示目录的所有组帐户。 **组**集合[用户](../../../ado/reference/adox-api/user-object-adox.md)表示仅用户所属的组。  
  
 与属性、 集合和方法的**组**对象，你可以：  
  
-   标识与组[名称](../../../ado/reference/adox-api/name-property-adox.md)属性。  
  
-   确定是否组具有读取、 写入或删除权限[GetPermissions](../../../ado/reference/adox-api/getpermissions-method-adox.md)和[SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)方法。  
  
-   访问的组中具有成员身份的用户帐户[用户](../../../ado/reference/adox-api/users-collection-adox.md)集合。  
  
-   访问与提供程序特定属性[属性](../../../ado/reference/ado-api/properties-collection-ado.md)集合。  
  
 本部分包含以下主题。  
  
-   [组对象属性、方法和事件](../../../ado/reference/adox-api/group-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>另请参阅  
 [组集合 (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [用户集合 (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
