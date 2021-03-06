---
title: 接收结果 |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving results [ADO]
- Recordset object [ADO], receiving results
ms.assetid: 791aa26e-7aae-477e-9f05-5cd46e1de095
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3330d2989f5662693ff7aca720d2bf6e07e16e33
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="receiving-results"></a>接收结果
在 ADO 大多数命令会返回到调用方的一些信息。 返回行集的命令，请在收到的结果**记录集**对象，它是可能最常用的 ADO 对象。  
  
 有几种方法来接收中的数据**记录集**从数据源，包括调用以下对象：  
  
-   [Connection.Execute 方法](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Command.Execute 方法](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Recordset.Open 方法](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Connection.NamedCommand](../../../ado/guide/data/named-commands.md)  
  
-   [Connection.StoredProcedure](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
 接收数据中的**记录集**对象结束获取数据的参与的过程**连接**对象和一个**命令**对象时，隐式或显式。 在典型的客户端/服务器应用程序系统中，获取数据的整个过程需要一次往返过程通过网络为每个填充**记录集**。  
  
 若要接收多个结果集意味着你将需要进行多次往返通过网络，另一个用于封装在每个数据集**记录集**对象。 对于缓慢或堵塞的网络，减少往返次数可能有助于提高应用程序的性能。 因此，某些提供商提供支持，以获得多个**记录集**在单个往返过程。 以下主题中讨论了这是：  
  
-   [接收多个记录集](../../../ado/guide/data/receiving-multiple-recordsets.md)
