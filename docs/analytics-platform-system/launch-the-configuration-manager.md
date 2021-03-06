---
title: 启动分析平台系统的配置管理器-|Microsoft 文档
description: 用于启动分析平台系统设备的配置管理器工具的说明。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d2e7a726386aa64d04f87f30cd22328900b1e5cd
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>在分析平台系统中启动 Configuration Manager
本主题提供用于启动说明**Configuration Manager**针对分析平台系统设备。  
  
## <a name="before-you-begin"></a>开始之前  
  
### <a name="prerequisites"></a>必要條件  
分析平台系统**Configuration Manager**只能由设备域管理员运行。 若要运行此工具，你需要设备域管理员密码。 若要创建 AP 的其他管理员，请参阅[创建 AP 域管理员&#40;AP&#41;](create-an-aps-domain-administrator-aps.md)。  
  
## <a name="Accessing"></a>启动配置管理器工具  
若要运行配置管理器，使用远程桌面连接到 PDW 控制节点 (***PDW_region *-CTL01**) 节点，并作为登录 * appliance_domain ***\Administrator**。 启动时**Configuration Manager**程序中，使用**以管理员身份运行**选项以确保使用你的管理员凭据。  
  
#### <a name="to-launch-from-a-browser-window"></a>若要在浏览器窗口中启动  
  
1.  打开浏览器并导航到目录`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`。  
  
2.  右键单击`dwconfig.exe`，然后单击**以管理员身份运行**。  
  
#### <a name="to-launch-from-a-command-prompt"></a>要从命令提示符下启动  
  
1.  在桌面上，打开**启动**菜单上，单击**程序**，单击**附件**，右键单击**命令提示符**，然后单击**以管理员身份运行**。  
  
2.  在命令提示符处，输入以下命令以将目录更改： `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"`。  
  
3.  在命令提示符处，输入`dwconfig.exe`。  
  
后**Configuration Manager**是开始，你将看到所有可用功能的左窗格中列出。 本部分的其余部分讨论如何执行该工具中提供每个操作。  
  
若要关闭并退出**Configuration Manager**，单击**退出**任何屏幕的右下角。  
  
![SQL_Server_PDW_DWConfig_ApplTop](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>另请参阅  
[通过使用管理控制台监视设备&#40;分析平台系统&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
