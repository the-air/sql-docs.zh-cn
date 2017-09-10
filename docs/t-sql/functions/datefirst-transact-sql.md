---
title: "@@DATEFIRST (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATE_FORMAT_TSQL
- DATE FORMAT
- '@@DATEFIRST_TSQL'
- '@@DATEFIRST'
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- date and time [SQL Server], SET DATEFIRST
- first day of week [SQL Server]
- dates [SQL Server], first day of week
- day of week [SQL Server]
- SET DATEFIRST option [SQL Server]
- date and time [SQL Server], DATEFIRST
- DATEFIRST option [SQL Server]
- date and time [SQL Server], @@DATEFIRST
- weekdays [SQL Server]
- '@@DATEFIRST function [SQL Server]'
- functions [SQL Server], date and time
- options [SQL Server], date
ms.assetid: a178868e-49d5-4bd5-a5e2-1283409c8ce6
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 951628293157784f522a262a1017b5b8b7f4bd83
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="datefirst-transact-sql"></a>@@DATEFIRST (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

返回当前值，适用于会话的[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)。
  
有关的所有概述[!INCLUDE[tsql](../../includes/tsql-md.md)]日期和时间数据类型和函数，请参阅[日期和时间数据类型和函数 &#40;Transact SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
@@DATEFIRST  
```  
  
## <a name="return-type"></a>返回类型  
**tinyint**
  
## <a name="remarks"></a>注释  
SET DATEFIRST 指定一周中的第一天。 美国英语中默认 7 对应星期日。
  
该语言设置会在字符串转换为用于存储在数据库中的日期值时影响字符串的解释，并会影响存储在数据库中的日期值的显示。 该设置不会影响日期数据的存储格式。 在下例中，语言首先设置为 `Italian`。 语句 `SELECT @@DATEFIRST;` 返回 `1`。 然后将语言设置为 `us_english`。 语句 `SELECT @@DATEFIRST;` 返回 `7`。
  
```sql
SET LANGUAGE Italian;  
GO  
SELECT @@DATEFIRST;  
GO  
SET LANGUAGE us_english;  
GO  
SELECT @@DATEFIRST;  
```  
  
## <a name="examples"></a>示例  
以下示例将每周的第一天设为 `5`（星期五），并假定当天（`Today`）是星期六。 该 `SELECT` 语句返回 `DATEFIRST` 值和当天是此周的第几天。
  
```sql
SET DATEFIRST 5;  
SELECT @@DATEFIRST AS 'First Day'  
    ,DATEPART(dw, SYSDATETIME()) AS 'Today';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
First Day         Today  
----------------  --------------  
5                 2  
```  
  
## <a name="example"></a>示例
 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT @@DATEFIRST;  
```  
  
## <a name="see-also"></a>另请参阅
[配置函数 &#40;Transact SQL &#41;](../../t-sql/functions/configuration-functions-transact-sql.md)
  
  

