---
title: "SET 语句 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET
- SET_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ISO SET statements
- queries [SQL Server], executing
- dates [SQL Server], SET statements
- time [SQL Server], SET statements
- SET statement, about SET statement
- SET statement
- statistical information [SQL Server], SET statements
- locking [SQL Server], SET statements
ms.assetid: f7e107f8-0fcf-408b-b30f-da2323eeb714
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f0426730b33f0b70fda11a8cb07242a365d10fae
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="set-statements-transact-sql"></a>SET 语句 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] 编程语言提供了一些 SET 语句，这些语句可以更改特定信息的当前会话处理。 SET 语句可分为下表中列出的几个类别。  
  
 有关使用 SET 语句设置本地变量的信息，请参阅[设置@local_variable&#40;Transact SQL &#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md).  
  
|类别|语句|  
|--------------|----------------|  
|日期和时间语句|[SET DATEFIRST](../../t-sql/statements/set-datefirst-transact-sql.md)<br /><br /> [集 DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md)|  
|锁定语句|[集 DEADLOCK_PRIORITY](../../t-sql/statements/set-deadlock-priority-transact-sql.md)<br /><br /> [集 LOCK_TIMEOUT](../../t-sql/statements/set-lock-timeout-transact-sql.md)|  
|杂项语句|[集 CONCAT_NULL_YIELDS_NULL](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)<br /><br /> [集 CURSOR_CLOSE_ON_COMMIT](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)<br /><br /> [集 FIPS_FLAGGER](../../t-sql/statements/set-fips-flagger-transact-sql.md)<br /><br /> [集 IDENTITY_INSERT](../../t-sql/statements/set-identity-insert-transact-sql.md)<br /><br /> [设置语言](../../t-sql/statements/set-language-transact-sql.md)<br /><br /> [组偏移量](../../t-sql/statements/set-offsets-transact-sql.md)<br /><br /> [集 QUOTED_IDENTIFIER](../../t-sql/statements/set-quoted-identifier-transact-sql.md)|  
|查询执行语句|[集 ARITHABORT](../../t-sql/statements/set-arithabort-transact-sql.md)<br /><br /> [集 ARITHIGNORE](../../t-sql/statements/set-arithignore-transact-sql.md)<br /><br /> [集 FMTONLY](../../t-sql/statements/set-fmtonly-transact-sql.md)<br /><br /> 注意：[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br /><br /> [集 NOCOUNT](../../t-sql/statements/set-nocount-transact-sql.md)<br /><br /> [集 NOEXEC](../../t-sql/statements/set-noexec-transact-sql.md)<br /><br /> [集 NUMERIC_ROUNDABORT](../../t-sql/statements/set-numeric-roundabort-transact-sql.md)<br /><br /> [集 PARSEONLY](../../t-sql/statements/set-parseonly-transact-sql.md)<br /><br /> [集 QUERY_GOVERNOR_COST_LIMIT](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md)<br /><br /> [组行计数](../../t-sql/statements/set-rowcount-transact-sql.md)<br /><br /> [集 TEXTSIZE](../../t-sql/statements/set-textsize-transact-sql.md)|  
|ISO 设置语句|[SET ANSI_DEFAULTS](../../t-sql/statements/set-ansi-defaults-transact-sql.md)<br /><br /> [集 ANSI_NULL_DFLT_OFF](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)<br /><br /> [集 ANSI_NULL_DFLT_ON](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)<br /><br /> [设置 ANSI_NULLS](../../t-sql/statements/set-ansi-nulls-transact-sql.md)<br /><br /> [集 ANSI_PADDING](../../t-sql/statements/set-ansi-padding-transact-sql.md)<br /><br /> [集 ANSI_WARNINGS](../../t-sql/statements/set-ansi-warnings-transact-sql.md)|  
|统计语句|[集 FORCEPLAN](../../t-sql/statements/set-forceplan-transact-sql.md)<br /><br /> [集 SHOWPLAN_ALL](../../t-sql/statements/set-showplan-all-transact-sql.md)<br /><br /> [集 SHOWPLAN_TEXT](../../t-sql/statements/set-showplan-text-transact-sql.md)<br /><br /> [集 SHOWPLAN_XML](../../t-sql/statements/set-showplan-xml-transact-sql.md)<br /><br /> [集 STATISTICS IO](../../t-sql/statements/set-statistics-io-transact-sql.md)<br /><br /> [组统计信息 XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)<br /><br /> [组统计信息配置文件](../../t-sql/statements/set-statistics-profile-transact-sql.md)<br /><br /> [设置统计信息时间](../../t-sql/statements/set-statistics-time-transact-sql.md)|  
|事务语句|[SET IMPLICIT_TRANSACTIONS](../../t-sql/statements/set-implicit-transactions-transact-sql.md)<br /><br /> [集 REMOTE_PROC_TRANSACTIONS](../../t-sql/statements/set-remote-proc-transactions-transact-sql.md)<br /><br /> [将事务隔离级别设置](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md)<br /><br /> [集 XACT_ABORT](../../t-sql/statements/set-xact-abort-transact-sql.md)|  
  
## <a name="considerations-when-you-use-the-set-statements"></a>使用 SET 语句时的注意事项  
  
-   除了 SET FIPS_FLAGGER、SET OFFSETS、SET PARSEONLY 和 SET QUOTED_IDENTIFIER 以外，所有 SET 语句均在执行或运行时实现。 而这些语句在分析时实现。  
  
-   如果是在存储过程或触发器中运行 SET 语句，则从存储过程或触发器返回控制后，将恢复 SET 选项的值。 此外，如果在运行通过使用动态 SQL 字符串中指定一个 SET 语句**sp_executesql**或完成控制权返回从动态 SQL 字符串中指定的批次后恢复执行，SET 选项的值。  
  
-   存储过程使用执行时指定的 SET 设置执行，但 SET ANSI_NULLS 和 SET QUOTED_IDENTIFIER 除外。 指定 SET ANSI_NULLS 或 SET QUOTED_IDENTIFIER 的存储过程使用创建存储过程时指定的设置。 如果在存储过程内使用任何 SET 设置，则该设置将被忽略。  
  
-   **用户选项**设置**sp_configure**允许服务器级设置，可以跨多个数据库工作。 此设置的行为还类似于显式 SET 语句，只是后者发生在登录时。  
  
-   使用 ALTER DATABASE 设置的数据库设置仅在数据库级有效，并且仅在显式设置时有效。 数据库设置将替代通过使用设置的实例选项设置**sp_configure**。  
  
-   对于任何带 ON 和 OFF 设置的 SET 语句，可以为多个 SET 选项指定 ON 或 OFF 设置。  
  
    > [!NOTE]  
    >  这不适用与统计相关的 SET 选项。  
  
     例如， `SET QUOTED_IDENTIFIER, ANSI_NULLS ON` QUOTED_IDENTIFIER 和 ANSI_NULLS 设置为 ON。  
  
-   SET 语句设置优先于使用 ALTER DATABASE 设置的等价数据库选项设置。 例如，SET ANSI_NULLS 语句中指定的值将覆盖 ANSI_NULL 的数据库设置。 此外，某些连接自动上设置的设置用户连接到数据库根据放入效果通过以前使用的值时**sp_configure 用户选项**设置或适用于所有 ODBC 值和OLE/DB 连接。  
  
-   ALTER、CREATE 和 DROP DATABASE 语句不提供 SET LOCK_TIMEOUT 设置。  
  
-   当全局或快捷 SET 语句（如 SET ANSI_DEFAULTS）设置多个设置时，发出快捷 SET 语句后，将重设所有受该快捷 SET 语句影响的选项的先前设置。 如果在发出快捷 SET 语句后显式设置了受快捷 SET 语句影响的单个 SET 选项，则该单个 SET 语句将覆盖相应的快捷设置。  
  
-   使用批处理时，数据库上下文由使用 USE 语句建立的批处理决定。 在存储过程的外部执行的以及批处理中的即席查询和所有其他语句，将继承通过 USE 语句建立的数据库和连接的选项设置。  
  
-   多个活动的结果集 (MARS) 请求共享一个全局状态，该状态包含最新会话 SET 选项设置。 每个请求执行时都可以修改 SET 选项。 更改特定于设置这些更改所在的请求上下文，不影响其他并发 MARS 请求。 但是，请求执行完成后，新的 SET 选项会被复制到全局会话状态。 在此更改之后，同一会话中执行的新请求将使用这些新的 SET 选项设置。  
  
-   当从批处理或其他存储过程执行某个存储过程时，执行该存储过程时使用的选项值，就是当前在包含该存储过程的数据库中设置的选项值。 例如，当存储过程**db1.dbo.sp1**调用存储的过程**db2.dbo.sp2**，存储过程**sp1**在当前兼容级别下执行设置数据库**db1**，存储过程和**sp2**下的数据库的当前兼容性级别设置执行**db2**。  
  
-   如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句引用的对象驻留在多个数据库中，则将对该语句应用当前数据库上下文和当前连接上下文。 在这种情况下，如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句在批处理中，则当前连接上下文是 USE 语句定义的数据库；如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句在存储过程中，则连接上下文是包含该存储过程的数据库。  
  
-   如果要对计算列或索引视图创建和操作索引，则必须将 SET 选项 ARITHABORT、CONCAT_NULL_YIELDS_NULL、QUOTED_IDENTIFIER、ANSI_NULLS、ANSI_PADDING 和 ANSI_WARNINGS 设置为 ON。 必须将选项 NUMERIC_ROUNDABORT 设置为 OFF。  
  
     如果以上任一选项没有设置为要求的值，则对索引视图或带计算列索引的表进行 INSERT、UPDATE、DELETE、DBCC CHECKDB 和 DBCC CHECKTABLE 操作时将失败。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将发出一个错误，并列出所有设置不正确的选项。 同时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将对这些表或索引视图运行 SELECT 语句，就好像计算列或视图中不存在索引。  
  
  