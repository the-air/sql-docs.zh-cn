---
title: 监视跟踪 (XMLA) |Microsoft 文档
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 24aab35b34ed9339ec2d7950efab21a94b2c0d96
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="monitoring-traces-xmla"></a>监视跟踪 (XMLA)
  你可以使用[订阅](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)命令，在 XML 用于 Analysis (XMLA) 监视的实例上定义的现有跟踪[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。 **订阅**命令返回的结果作为行集跟踪。  
  
## <a name="specifying-a-trace"></a>指定跟踪  
 [对象](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)属性**订阅**命令必须包含对象引用为[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例或上的跟踪[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例。 如果**对象**未指定属性，或在未指定跟踪标识符**对象**属性，**订阅**命令监视的默认会话跟踪该命令的 SOAP 标头中指定的显式会话。  
  
## <a name="returning-results"></a>返回结果  
 **订阅**命令返回行集包含指定的跟踪捕获的跟踪事件。 **订阅**命令返回跟踪结果，直到该命令取消通过[取消](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)命令。  
  
 下表列出了该行集包含的列。  
  
|列|数据类型|Description|  
|------------|---------------|-----------------|  
|EventClass|Integer|跟踪所接收的事件的事件类。|  
|EventSubclass|Long integer|跟踪所接收的事件的事件子类。|  
|CurrentTime|日期时间|事件（如果有）的开始时间。 为了便于筛选，采用的格式为“YYYY-MM-DD”和“YYYY-MM-DD HH:MM:SS”。|  
|StartTime|日期时间|事件（如果有）的开始时间。 为了便于筛选，采用的格式为“YYYY-MM-DD”和“YYYY-MM-DD HH:MM:SS”。|  
|EndTime|日期时间|事件（如果有的话）的结束时间。 为了便于筛选，采用的格式为“YYYY-MM-DD”和“YYYY-MM-DD HH:MM:SS”。<br /><br /> 对于描述进程或操作启动的事件类，不填充此列。|  
|Duration|Long integer|事件所用的总时间（毫秒）。|  
|CPUTime|Long integer|事件所用的处理器时间（毫秒）。|  
|作业 ID|Long integer|进程的作业标识符。|  
|SessionID|字符串|发生事件的会话的标识符。|  
|SessionType|字符串|发生事件的会话的类型。|  
|ProgressTotal|Long integer|事件所报告的进度总数。|  
|IntegerData|Long integer|与事件关联的整数数据。 此列的内容取决于事件的事件类和子类。|  
|ObjectID|字符串|发生事件的对象的标识符。|  
|ObjectType|字符串|ObjectName 中指定的对象的类型。|  
|ObjectName|字符串|发生事件的对象的名称。|  
|ObjectPath|字符串|发生事件的对象的分层路径。 对于 ObjectName 中所指定的对象的父级，该路径表示为以逗号分隔的对象标识符字符串。|  
|ObjectReference|字符串|ObjectName 中所指定对象的对象引用的 XML 表示形式。|  
|NestLevel|Integer|发生事件的事务的级别。|  
|NumSegments|Long integer|发生事件的命令所影响或访问的数据段数量。|  
|Severity|Integer|事件异常的严重级别。 此列可包含下列值之一：<br /><br /> <br /><br /> 0： 成功<br /><br /> <br /><br /> 1： 信息<br /><br /> <br /><br /> 2： 警告<br /><br /> <br /><br /> 3： 错误|  
|成功|Boolean|指示命令成功还是失败。|  
|错误|Long integer|事件的错误号（如果适用）。|  
|ConnectionID|字符串|发生事件的连接的标识符。|  
|DatabaseName|字符串|发生事件的数据库的名称。|  
|NTUserName|字符串|与事件关联的用户的 Windows 用户名。|  
|NTDomainName|字符串|与事件关联的用户的 Windows 域。|  
|ClientHostName|字符串|正在运行客户端应用程序的计算机的名称。 此列由该客户端应用程序传递的值填充。|  
|ClientProcessID|Long integer|客户端应用程序的进程标识符。|  
|ApplicationName|字符串|客户端应用程序的名称，该客户端应用程序创建了到 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的连接。 此列由客户端应用程序传递的值填充，而不是由所显示的程序名填充。|  
|NTCanonicalUserName|字符串|与事件关联的用户的 Windows 规范用户名。|  
|SPID|字符串|发生事件的会话的服务器进程 ID (SPID)。 此列的值直接对应于发生事件的 XMLA 消息的 SOAP 标头中指定的会话 ID。|  
|TextData|字符串|与事件关联的文本数据。 此列的内容取决于事件的事件类和子类。|  
|ssSqlProfiler|字符串|发生事件的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 实例的名称。|  
|RequestParameters|字符串|发生事件的参数化查询或 XMLA 命令的参数。|  
|RequestProperties|字符串|发生事件的 XMLA 方法的属性。|  
  
## <a name="see-also"></a>另请参阅  
 [使用 Analysis Services 中的 XMLA 进行开发](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
