---
title: 查看 Windows 应用程序日志 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2a1154f65a9fa5cc03f9fe9d964d864092250370
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/19/2018
---
# <a name="view-the-windows-application-log-windows-10"></a>查看 Windows 应用程序日志 (Windows 10)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置为使用 Windows 应用程序日志后，每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会话都将新事件写入该日志。 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志不同，不是每次启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例时都创建新的应用程序日志。  
  
## <a name="view-the-windows-application-log"></a>查看 Windows 应用程序日志  
  
1. 在“搜索栏”中，键入“事件查看器”，然后选择“事件查看器”桌面应用。
  
2. 在“事件查看器”中，打开“应用程序和服务日志”。

3. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件由“源”列中的 MSSQLSERVER 项（命名实例以 MSSQL$<instance_name> 标识）标识。 SQL Server 代理事件由 SQLSERVERAGENT 项标识（对于已命名的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理事件由 **SQLAgent$**\<*instance_name*> 标识）。 Microsoft Search 服务事件由 **Microsoft Search**项标识。  
  
4. 若要查看另一台计算机的日志，右键单击“事件查看器（本地）”。 选择“连接到另一台计算机”，并填写字段以完成“选择计算机”对话框。  
  
5. 或是希望只显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件，请在“查看”菜单中选择“筛选器”。 在“事件源”列表中，选择“MSSQLSERVER”。 若要仅查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理事件，请在 **“事件源”** 列表中选择 **SQLSERVERAGENT** 。  
  
6. 若要查看有关某事件的详细信息，请双击该事件。  
  
## <a name="see-also"></a>另请参阅  
 [查看 SQL Server 错误日志 (SQL Server Management Studio)](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)  
  
  
