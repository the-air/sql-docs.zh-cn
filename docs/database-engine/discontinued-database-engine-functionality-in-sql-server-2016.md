---
title: SQL Server 2016 中弃用的数据库引擎功能 | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
caps.latest.revision: 100
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 024986a082bee4e823d66fdb588e65fc6d4f4c88
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2016"></a>SQL Server 2016 中废止的数据库引擎功能
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  本主题介绍 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中不再可用的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]功能。  
  
## <a name="discontinued-features-in-includesssql15includessssql15-mdmd"></a>[!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] 是 64 位应用程序。 32 位安装已停止使用，不过，某些元素仍以 32 位组件运行。  
  
-   已不再使用兼容级别 90。 有关详细信息，请参阅 [ALTER DATABASE 兼容级别 (Transact-SQL)](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)。  

-   ActiveX 子系统已停止使用。 请改用命令行或 PowerShell 脚本。
  
## <a name="previous-versions"></a>先前版本  
  
-   [SQL Server 2014 中废止的数据库引擎功能](https://msdn.microsoft.com/library/ms144262\(v=sql.120\))  
  
-   [SQL Server 2012 中废止的数据库引擎功能](https://msdn.microsoft.com/library/ms144262\(v=sql.110\))  
  
-   [SQL Server 2008 中废止的数据库引擎功能](https://msdn.microsoft.com/library/ms144262\(v=sql.100\))  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server 2016 中不推荐使用的数据库引擎功能](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [SQL Server 复制中不推荐使用的功能](../relational-databases/replication/deprecated-features-in-sql-server-replication.md)  
  
 
