---
title: "sys.dm_operation_status （Azure SQL 数据库） |Microsoft 文档"
ms.custom: 
ms.date: 06/05/2017
ms.prod: 
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: 
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_operation_status_TSQL
- dm_operation_status
- sys.dm_operation_status
- sys.dm_operation_status_TSQL
dev_langs: TSQL
helpviewer_keywords:
- dm_operation_status dynamic management view
- sys.dm_operation_status dynamic management view
ms.assetid: cc847784-7f61-4c69-8b78-5f971bb24d61
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6d6096c5a32f4c7cbcd2ddd99a8990545c552c1
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmoperationstatus-azure-sql-database"></a>sys.dm_operation_status (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  返回有关对 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 服务器中的数据库执行的操作的信息。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|session_activity_id|**uniqueidentifier**|操作的 ID。 不为 null。|  
|resource_type|**int**|指示针对其执行操作的资源类型。 不为 null。 在当前版本中，此视图仅跟踪对 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 执行的操作，对应的整数值为 0。|  
|resource_type_desc|**nvarchar(2048)**|针对其执行操作的资源类型的说明。 在当前版本中，此视图只跟踪对 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 执行的操作。|  
|major_resource_id|**sql_variant**|对其执行操作的 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 的名称。 不为 Null。|  
|minor_resource_id|**sql_variant**|仅限内部使用。 不为 null。|  
|操作|**nvarchar(60)**|在 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 上执行的操作，如 CREATE 或 ALTER。|  
|state|**tinyint**|操作的状态。<br /><br /> 0 = 等待批准<br />1 = 正在进行<br />2 = 已完成<br />3 = 失败<br />4 = 已取消|  
|state_desc|**nvarchar(120)**|PENDING = 操作正在等待提供资源或配额。<br /><br /> IN_PROGRESS = 操作已启动并且正在进行。<br /><br /> COMPLETED = 操作已成功完成。<br /><br /> FAILED = 操作失败。 请参阅**error_desc**有关详细信息的列。<br /><br /> CANCELLED = 在用户的要求下停止操作。|  
|percent_complete|**int**|操作已完成的百分比。 值不是连续的并下面列出了有效的值。 不为 NULL。<br/><br/>0 = 未启动的操作<br/>50 = 正在进行的操作<br/>100 = 操作完成|  
|error_code|**int**|指示在操作失败过程中发生的错误的代码。 如果值为 0，则指示操作已成功完成。|  
|error_desc|**nvarchar(2048)**|在操作失败过程中发生的错误的说明。|  
|error_severity|**int**|在操作失败过程中发生的错误的严重性级别。 有关错误严重级别的详细信息，请参阅[数据库引擎错误严重性](http://go.microsoft.com/fwlink/?LinkId=251052)。|  
|error_state|**int**|保留供将来使用。 不保证以后的兼容性。|  
|start_time|**datetime**|开始操作的时间戳。|  
|last_modify_time|**datetime**|上次修改长时间运行的操作的记录的时间戳。 在成功完成操作的情况下，此字段显示操作完成的时间戳。|  
  
## <a name="permissions"></a>Permissions  
 此视图选项仅适用于**master**与服务器级别主体登录名的数据库。  
  
## <a name="remarks"></a>注释  
 若要使用此视图，你必须连接到**master**数据库。 使用`sys.dm_operation_status`中查看**master**数据库[!INCLUDE[ssSDS](../../includes/sssds-md.md)]服务器来跟踪上执行的以下操作的状态[!INCLUDE[ssSDS](../../includes/sssds-md.md)]:  
  
-   创建数据库  
  
-   复制数据库。 数据库副本在此视图中创建关于源服务器和目标服务器的记录。  
  
-   更改数据库  
  
-   更改服务层的性能级别  
  
-   更改数据库的服务层，例如从“基本”更改为“标准”。  
  
-   设置地理复制关系  
  
-   终止地理复制关系  
  
-   对话框的  
  
-   删除数据库  
  
## <a name="example"></a>示例  
 显示与数据库 mydb 的最新异地复制操作。  
  
```  
SELECT * FROM sys.dm_ operation_status   
   WHERE major_resource_id = ‘myddb’   
   ORDER BY start_time DESC;  
```  
  
## <a name="see-also"></a>另请参阅  
 [地域复制动态管理视图和函数 &#40;Azure SQL Database &#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status &#40;Azure SQL Database &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [sys.geo_replication_links &#40;Azure SQL Database &#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [ALTER DATABASE &#40;Azure SQL Database &#41;](../../t-sql/statements/alter-database-azure-sql-database.md)  
  
  