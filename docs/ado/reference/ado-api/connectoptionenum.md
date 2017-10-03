---
title: "ConnectOptionEnum |Microsoft 文档"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 582f85d3ce45071cd283f05f5d595e10b5d1614c
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="connectoptionenum"></a>ConnectOptionEnum
指定是否[打开](../../../ado/reference/ado-api/open-method-ado-connection.md)方法[连接](../../../ado/reference/ado-api/connection-object-ado.md)（同步） 建立连接之后或之前，应返回对象 （以异步方式）。  
  
|常量|值|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|以异步方式打开连接。 [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)事件可用于确定可用连接时。|  
|**adConnectUnspecified**|-1|默认值。 以同步方式打开连接。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 包： **com.ms.wfc.data**  
  
|常量|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>适用范围  
 [Open 方法 （ADO 连接）](../../../ado/reference/ado-api/open-method-ado-connection.md)