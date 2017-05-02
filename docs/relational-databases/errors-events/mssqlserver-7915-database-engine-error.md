---
title: MSSQLSERVER_7915 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fd2358d9fda87cfe7f1d25dc45ef475606165eb4
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver7915"></a>MSSQLSERVER_7915
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|7915|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|消息正文|修复: 对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）的 IAM 链已在页 P_ID 前截断，将重新生成该链。|  
  
## <a name="explanation"></a>解释  
这是 REPAIR 发送的信息性消息，指示修补了指定的索引分配映射 (IAM) 链，以便可以重新生成它。 此修补可能需要分配新的 IAM 链头或者删除错误页。  
  
## <a name="user-action"></a>用户操作  
InclusionThresholdSetting  
  
