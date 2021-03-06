---
title: SQLExecDirect （Visual FoxPro ODBC 驱动程序） |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0086dc41e34ac543cf0cd560332454b0024de48e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect （Visual FoxPro ODBC 驱动程序）
> [!NOTE]  
>  本主题包含 Visual FoxPro ODBC 驱动程序相关的信息。 有关此函数的常规信息，请参阅下的相应主题[ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支持： 完整  
  
 ODBC API 一致性： 核心级别  
  
 执行一个新的[preparable SQL 语句](../../odbc/microsoft/visual-foxpro-terminology.md)。 如果语句中存在任何参数，则 Visual FoxPro ODBC 驱动程序使用的参数标记变量的当前值。  
  
 若要创建批处理命令提交一次的多个 SQL 语句，请使用分号 （;） 分隔批处理中的每个 SQL 语句。  
  
 如果你的表、 视图或字段名称包含空格，将名称括在返回引号标记。 例如，如果你的数据库包含名为我的表和字段 My Field 的表，将包含标识符的每个元素，如下所示：  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 有关详细信息，请参阅[SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md)中*ODBC 程序员参考*。
