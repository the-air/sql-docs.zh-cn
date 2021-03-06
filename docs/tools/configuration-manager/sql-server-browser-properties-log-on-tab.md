---
title: SQL Server 浏览器属性 （选项卡上的日志） |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c77871ec-c2f4-4e4a-9a10-5aeb4ae70507
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 814b8f9f6c94e0c0907ee662565fd5377455a5a9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-browser-properties-log-on-tab"></a>SQL Server 浏览器属性（“登录”选项卡）
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器程序以服务的形式在服务器上运行。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器侦听对 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 资源的传入请求，并提供计算机上安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的相关信息。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 浏览器使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 解析协议 (SSRP) 侦听 UDP 端口，并接受未经身份验证的请求。  
  
 对帐户密码的更改立即生效，无需重新启动服务。  
  
## <a name="options"></a>“常规”  
 **本地系统帐户**  
 在本地系统帐户的安全上下文中运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。 请尽可能使用低权限帐户。  
  
 **本帐户**  
 指定一个使用 Windows 身份验证的本地用户帐户或域用户帐户。 建议使用具有最低服务权限的域用户帐户。 有关选择帐户的信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“设置 Windows 服务帐户”。  
  
 **“浏览”**  
 浏览用户或内置安全主体。  
  
> [!IMPORTANT]  
>  使用低权限帐户。 有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务所需权限的信息，请参阅 [SQL Server Browser 服务](../../tools/configuration-manager/sql-server-browser-service.md)中的“安全性”部分。  
  
 **密码**  
 输入安全主体的密码。  
  
 **确认密码**  
 确认安全主体的密码。  
  
 **服务状态**  
 指示此服务是正在运行、已停止还是已禁用。 **“...”**指示状态更改被挂起。  
  
 **开始**  
 启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **停止**  
 停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **暂停**  
 暂停 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
 **恢复**  
 恢复暂停的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服务。  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server Browser 服务](../../tools/configuration-manager/sql-server-browser-service.md)  
  
  
