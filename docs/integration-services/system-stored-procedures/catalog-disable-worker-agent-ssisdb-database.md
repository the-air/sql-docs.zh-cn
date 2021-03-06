---
title: catalog.disable_worker_agent（SSISDB 数据库）| Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3f19dc4c-a000-4318-8fe1-e80d56720e66
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 77dbfb829c7c9148d8d27735c070b7ad9f187145
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="catalogdisableworkeragent-ssisdb-database"></a>catalog.disable_worker_agent（SSISDB 数据库）
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

为使用此 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目录的 Scale Out Master 禁用 Scale Out Worker。

## <a name="syntax"></a>语法

```sql
catalog.disable_worker_agent [@WorkerAgentId =] WorkerAgentId
```
## <a name="arguments"></a>参数
[@WorkerAgentId =] WorkerAgentId Scale Out Worker 的辅助角色代理 ID。 WorkerAgentId 为 uniqueidentifier。

## <a name="example"></a>示例
此示例在 MachineA 上禁用 Scale Out Worker。

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    MachineA    --

EXEC [catalog].[disable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="return-code-value"></a>返回代码值  
 0（成功）  
  
## <a name="result-sets"></a>结果集  
 InclusionThresholdSetting  

## <a name="permissions"></a>权限  
 此存储过程需要下列权限之一：  
  
-   ssis_admin 数据库角色的成员资格  
  
-   sysadmin 服务器角色的成员资格 

## <a name="errors-and-warnings"></a>错误和警告
如果辅助角色代理 ID 无效，则存储过程返回错误。
