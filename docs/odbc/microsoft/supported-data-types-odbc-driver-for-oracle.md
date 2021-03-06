---
title: 支持的数据类型 （适用于 Oracle 的 ODBC 驱动程序） |Microsoft 文档
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
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4f6e80b887659679992091a32faf2763d71d9f6f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>支持的数据类型 （适用于 Oracle 的 ODBC 驱动程序）
> [!IMPORTANT]  
>  将 Windows 的未来版本中删除该功能。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 相反，使用提供的 Oracle 的 ODBC 驱动程序。  
  
 适用于 Oracle 的 ODBC 驱动程序支持所有的 Oracle 7.3 数据类型;但是，它不支持任何此处列出的新 Oracle8 数据类型。  
  
|数据类型|Oracle 7.3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|不适用|不支持|  
|BLOB|不适用|不支持|  
|CHAR|Supported|Supported|  
|CLOB|不适用|不支持|  
|DATE|Supported|Supported|  
|FLOAT|Supported|Supported|  
|整数|Supported|Supported|  
|LONG|Supported|Supported|  
|LONG RAW|Supported|Supported|  
|NCHAR|不适用|不支持|  
|NCLOB|不适用|不支持|  
|NUMBER|Supported|Supported|  
|NVARCHAR2|不适用|不支持|  
|RAW|Supported|Supported|  
|VARCHAR2|Supported|Supported|  
|MLSLABEL|不提供支持。|不提供支持。|  
  
> [!NOTE]  
>  VARCHAR 列的允许大小的详细信息，请参阅[VARCHAR 列大小](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md)本指南中。
