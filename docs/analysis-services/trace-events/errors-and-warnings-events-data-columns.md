---
title: 错误和警告事件数据列 |Microsoft 文档
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84a1f21e5556efcf64e1ff1b7c6d5ab2208d1038
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="errors-and-warnings-events-data-columns"></a>错误和警告事件数据列
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  “安全审核”事件类别具有以下事件类：  
  
-   错误类  
  
 下表列出了此事件类的数据列。  
  
## <a name="error-event-classdata-columns"></a>错误事件类 - 数据列  
  
|**列名**|**列 ID**|**列类型**|**列说明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|事件类用于将事件分类。|  
|StartTime|3|5|包含事件（如果有）的开始时间。 为了便于筛选，采用的格式为“YYYY-MM-DD”和“YYYY-MM-DD HH:MM:SS”。|  
|SessionType|8|8|包含导致了错误的实体的类型。|  
|Severity|22|1|包含与错误事件关联的异常的严重性级别。 值为：<br /><br /> 0 = 成功<br /><br /> 1 = 信息<br /><br /> 2 = 警告<br /><br /> 3 = 错误|  
|成功|23|1|包含错误事件的成功或失败。 值为：<br /><br /> 0 = 失败<br /><br /> 1 = 成功|  
|错误|24|1|包含与错误事件关联的任何错误的错误号。|  
|ConnectionID|25|1|包含与错误事件关联的唯一连接 ID。|  
|DatabaseName|28|8|包含其上发生错误事件的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的名称。|  
|NTUserName|32|8|包含与错误事件关联的 Windows 用户名。|  
|NTDomainName|33|8|包含与登录事件关联的 Windows 域帐户。|  
|ClientHostName|35|8|包含正在运行客户端程序的计算机的名称。 如果客户端提供了主机名，则填充此数据列。|  
|ClientProcessID|36|1|包含客户端应用程序的进程 ID。|  
|ApplicationName|37|8|包含创建了到服务器连接的客户端应用程序的名称。 此列由应用程序传递的值填充，而不是由所显示的程序名填充。|  
|SessionID|39|8|包含唯一标识与错误事件关联的用户会话的服务器进程 ID (SPID)。 SPID 直接对应于 XML for Analysis (XMLA) 所使用的会话 GUID。|  
|SPID|41|1|包含唯一标识与错误事件关联的用户会话的服务器进程 ID (SPID)。 SPID 直接对应于 XML for Analysis (XMLA) 所使用的会话 GUID。|  
|TextData|42|9|包含与错误事件关联的文本数据。|  
|ServerName|43|8|包含正在运行发生了错误事件的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的服务器的名称。|  
  
## <a name="see-also"></a>另请参阅  
 [“安全审核”事件类别](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
