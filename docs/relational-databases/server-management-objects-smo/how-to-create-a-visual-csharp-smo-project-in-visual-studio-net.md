---
title: "在 Visual Studio.NET 中创建 Visual C# SMO 项目 |Microsoft 文档"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2fb8a8bd7527a14df4447fd4c7a49e92647b9e09
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>如何在 Visual Studio.NET 中创建 Visual C# SMO 项目
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]本部分介绍如何构建一个简单的 SMO 控制台应用程序。  
  
 此示例导入命名空间，这样，程序即可以引用 SMO 类型。 在导入**代理**是可选的命名空间。 当编写使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的程序时使用此命名空间。 **常见**建立安全连接到的实例所需的命名空间[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 **SqlClient**命名空间用于处理 SQL 异常错误。  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>在 Visual Studio.NET 中创建 Visual C# SMO 项目  
  
1. 启动 Visual Studio
  
2. 上**文件**菜单上，单击**新建**然后**项目**。  此时将显示“新建项目”  对话框。   
  
3. 在[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]**已安装**窗格中，导航到**模板**\\**Visual C#**\\**Windows**然后选择**控制台应用程序**。  
  
4. （可选）在**名称**文本框中，键入新的应用程序的名称。  

5. 单击**确定**来加载控制台应用程序模板。  

6. 按照上的说明[安装 SMO](installing-smo.md)安装项目，以引用的包。
  
7. 在 **“视图”** 菜单上，单击 **“代码”**。
    
8. 在代码中之前的命名空间语句中，, 键入以下命令**使用**语句来限定 SMO 命名空间中的类型：
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO 在 Microsoft.SqlServer.Management.Smo 下具有各种命名空间，如 Microsoft.SqlServer.Management.Smo.Agent。 请根据需要添加这些命名空间。  
  
16. 您可以立即添加 SMO 代码。  
  
  