---
title: PDW 防火墙配置-分析平台系统 |Microsoft 文档
description: SQL Server PDW 配置管理器中的防火墙页，可启用或禁用防火墙规则来允许或阻止对分析平台系统设备上的特定端口的访问。
aauthor: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8ccfd60aee7647c2421870a09ab5fa9b2653b99d
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>分析平台系统中的并行数据仓库防火墙配置
**防火墙**页的 SQL Server PDW 配置管理器使你可以启用或禁用防火墙规则来允许或阻止对分析平台系统设备上的特定端口的访问。  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>为设备节点管理端口和防火墙规则  
  
1.  启动 Configuration Manager。 有关详细信息，请参阅[启动配置管理器&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)。  
  
2.  在配置管理器的左窗格中，展开**并行数据仓库拓扑**，然后单击**防火墙**。  
  
3.  找到端口或防火墙规则，以更新中的配置列表中，然后选择或清除该项旁边的框。 只有 SQL Server PDW 管理员可配置选项都显示在此列表，包括开始标记与结束面向外部的节点上的端口。  
  
4.  单击**应用**以保存所做的更改。  
  
![DWConfig 设备 PDW 防火墙](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>外部端口  
以下端口已打开进行外部 PDW 来自的客户端连接。  
  
|用途|端口 #|节点|  
|-----------|-----------|---------|  
|SQL 客户端访问 PDW (TDS)|17001|CTL|  
|加载程序客户端访问 （dwloader 和 SSIS）|8001|CTL|  
|远程桌面访问|3389|CTL CMP|  
|SSIS BinaryLoaderDataChannel|16551|CTL|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL 加密连接 （对于内部通信，以便访问管理控制台中，从而访问 HDInsight 群集服务）|443|所有节点|  
|SQL Server PDW 负载控制流的 Windows 凭据|8002|CTL|  
|_Kerberos|88|AD01 和 AD02，|  
|_ldap|389|AD01 和 AD02|  
  
## <a name="internal-ports"></a>内部端口  
以下的端口由 PDW 用于内部通信，但为来自外部 PDW 设备的连接未打开。  
  
|用途|端口 #|节点|  
|-----------|-----------|---------|  
|DMS 控制通道流量|16450|CTL CMP|  
|DMS 数据通道流量|16550|CTL CMP|  
|内部诊断|16650|CTL CMP|  
|故障转移状态 (DMS)|15000|CTL CMP|  
|故障转移状态 （引擎）|15001|CMP|  
|动态 （临时） 端口范围|20000-65535|CTL CMP|  
|SQL Server 端口范围 (TDS)|1433, 1500-1508|CTL CMP|  
  
> [!NOTE]  
> 创建外部表或外部数据源使用 TCP 端口 8020 默认情况下。 这些语句可以配置为改为使用其他端口。 Hortonworks JOB_TRACKER_LOCATION 默认端口为 50300。 与其他系统和工具集成可能需要其他端口。  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)  -->  
  
