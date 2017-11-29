---
title: "sys.dm_server_memory_dumps (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_server_memory_dumps_TSQL
- dm_server_memory_dumps_TSQL
- dm_server_memory_dumps
- sys.dm_server_memory_dumps
dev_langs: TSQL
helpviewer_keywords: sys.dm_server_memory_dumps dynamic management view
ms.assetid: 41782719-f54d-4e11-941a-c050c7576e23
caps.latest.revision: "6"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd4af6e42415814c6fc0771346f94a5283a41730
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmservermemorydumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  为 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]生成的每个内存转储文件返回一行。 使用此动态管理视图解决潜在的问题。  
 
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**文件名**|**nvarchar(256)**|内存转储文件的路径和名称。 不可为 null。|  
|**creation_time**|**datetimeoffset(7)**|创建文件的日期和时间。 不可为 null。|  
|**size_in_bytes**|**bigint**|文件的大小（以字节为单位）。 可以为 Null。|  
  
## <a name="general-remarks"></a>一般备注  
 转储类型可以是小型转储、所有线程转储或完整转储。 文件的扩展名为 .mdmp。  
  
## <a name="security"></a>安全性  
 转储文件可能包含敏感信息。 为了帮助保护敏感信息，可以使用访问控制列表 (ACL) 来限制对这些文件的访问，或将这些文件复制到具有受限访问权限的文件夹中。 例如，发送调试文件到 Microsoft 支持服务之前，我们建议你删除任何敏感或机密信息。  
  
### <a name="permissions"></a>Permissions  
 需要 VIEW SERVER STATE 权限。  
  
  