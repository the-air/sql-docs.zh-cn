---
title: CREATE TRIGGER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|statements
ms.reviewer: mathoma
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE TRIGGER
- TRIGGER
- CREATE_TRIGGER_TSQL
- TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- recursive DML triggers [SQL Server]
- CREATE TRIGGER statement
- multiple triggers
- deferred name resolution, DML triggers
- DML triggers, creating
- nested triggers
- server-scoped triggers
- DDL triggers, creating
- triggers [SQL Server], creating
- database-scoped triggers [SQL Server]
ms.assetid: edeced03-decd-44c3-8c74-2c02f801d3e7
caps.latest.revision: 140
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 26721a416b9e3da167a438ea2609679d08481237
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="create-trigger-transact-sql"></a>CREATE TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  创建 DML、DDL 或登录触发器。 触发器是数据库服务器中发生事件时自动执行的一种特殊存储过程。 如果用户要通过数据操作语言 (DML) 事件编辑数据，则执行 DML 触发器。 DML 事件是针对表或视图的 INSERT、UPDATE 或 DELETE 语句。 在激发任何有效的事件时，将会激发这些触发器，而无论是否会影响任何表行。 有关详细信息，请参阅 [DML Triggers](../../relational-databases/triggers/dml-triggers.md)。  
  
 DDL 触发器用于响应各种数据定义语言 (DDL) 事件。 这些事件主要对应于 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE、ALTER 和 DROP 语句，以及执行类似 DDL 操作的某些系统存储过程。 登录触发器在遇到 LOGON 事件时触发，该事件是在建立用户会话时引发的。 触发器可以由 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句直接创建，也可以由程序集方法创建，这些方法在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 公共语言运行时 (CLR) 中创建并上载到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许为任何特定语句创建多个触发器。  
  
> [!IMPORTANT]  
>  触发器内部的恶意代码可以在升级后的权限下运行。 有关如何缓解此威胁的详细信息，请参阅[管理触发器安全](../../relational-databases/triggers/manage-trigger-security.md)。  
  
> [!NOTE]  
>  本主题讨论 .NET Framework CLR 与 SQL Server 的集成。 CLR 集成不适用于 Azure SQL 数据库。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```sql  
-- SQL Server Syntax  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  
  
CREATE [ OR ALTER ] TRIGGER [ schema_name . ]trigger_name   
ON { table | view }   
[ WITH <dml_trigger_option> [ ,...n ] ]  
{ FOR | AFTER | INSTEAD OF }   
{ [ INSERT ] [ , ] [ UPDATE ] [ , ] [ DELETE ] }   
[ WITH APPEND ]  
[ NOT FOR REPLICATION ]   
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME <method specifier [ ; ] > }  
  
<dml_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
  
```  
  
```sql  
-- SQL Server Syntax  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a 
-- table (DML Trigger on memory-optimized tables)  
  
CREATE [ OR ALTER ] TRIGGER [ schema_name . ]trigger_name   
ON { table }   
[ WITH <dml_trigger_option> [ ,...n ] ]  
{ FOR | AFTER }   
{ [ INSERT ] [ , ] [ UPDATE ] [ , ] [ DELETE ] }   
AS { sql_statement  [ ; ] [ ,...n ] }  
  
<dml_trigger_option> ::=  
    [ NATIVE_COMPILATION ]  
    [ SCHEMABINDING ]  
    [ EXECUTE AS Clause ]  
  
```  
  
```sql  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, 
-- REVOKE or UPDATE statement (DDL Trigger)  
  
CREATE [ OR ALTER ] TRIGGER trigger_name   
ON { ALL SERVER | DATABASE }   
[ WITH <ddl_trigger_option> [ ,...n ] ]  
{ FOR | AFTER } { event_type | event_group } [ ,...n ]  
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME < method specifier >  [ ; ] }  
  
<ddl_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
```  
  
```sql  
-- Trigger on a LOGON event (Logon Trigger)  
  
CREATE [ OR ALTER ] TRIGGER trigger_name   
ON ALL SERVER   
[ WITH <logon_trigger_option> [ ,...n ] ]  
{ FOR| AFTER } LOGON    
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME < method specifier >  [ ; ] }  
  
<logon_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
```  
  
## <a name="syntax"></a>语法  
  
```sql  
-- Windows Azure SQL Database Syntax   
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  
  
CREATE [ OR ALTER ] TRIGGER [ schema_name . ]trigger_name   
ON { table | view }   
 [ WITH <dml_trigger_option> [ ,...n ] ]   
{ FOR | AFTER | INSTEAD OF }   
{ [ INSERT ] [ , ] [ UPDATE ] [ , ] [ DELETE ] }   
  AS { sql_statement  [ ; ] [ ,...n ] [ ; ] > }  
  
<dml_trigger_option> ::=   
        [ EXECUTE AS Clause ]  
  
```  
  
```sql  
-- Windows Azure SQL Database Syntax  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, 
-- REVOKE, or UPDATE STATISTICS statement (DDL Trigger)   
  
CREATE [ OR ALTER ] TRIGGER trigger_name   
ON { DATABASE }   
 [ WITH <ddl_trigger_option> [ ,...n ] ]   
{ FOR | AFTER } { event_type | event_group } [ ,...n ]   
AS { sql_statement  [ ; ] [ ,...n ]  [ ; ] }  
  
<ddl_trigger_option> ::=   
    [ EXECUTE AS Clause ]  
```  
  
## <a name="arguments"></a>参数
OR ALTER  
 适用范围：Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]（从 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 开始）。 
  
 只有在触发器已存在时才对其进行有条件地更改。 
  
 *schema_name*  
 DML 触发器所属架构的名称。 DML 触发器的作用域是为其创建该触发器的表或视图的架构。 不能为 DDL 或登录触发器指定 schema_name。  
  
 *trigger_name*  
 触发器的名称。 *trigger_name* 必须符合[标识符](../../relational-databases/databases/database-identifiers.md)规则，但 *trigger_name* 不能以 # 或 ## 开头。  
  
 table | view  
 对其执行 DML 触发器的表或视图，有时称为触发器表或触发器视图。 可以根据需要指定表或视图的完全限定名称。 视图只能被 INSTEAD OF 触发器引用。 不能对局部或全局临时表定义 DML 触发器。  
  
 DATABASE  
 将 DDL 触发器的作用域应用于当前数据库。 如果指定了此参数，则只要当前数据库中出现 event_type 或 event_group，就会激发该触发器。  
  
 ALL SERVER  
 **适用范围**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 将 DDL 或登录触发器的作用域应用于当前服务器。 如果指定了此参数，则只要当前服务器中的任何位置出现 event_type 或 event_group，就会激发该触发器。  
  
 WITH ENCRYPTION  
 **适用范围**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 对 CREATE TRIGGER 语句的文本进行模糊处理。 使用 WITH ENCRYPTION 可以防止将触发器作为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 复制的一部分进行发布。 不能为 CLR 触发器指定 WITH ENCRYPTION。  
  
 EXECUTE AS  
 指定用于执行该触发器的安全上下文。 允许您控制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例用于验证被触发器引用的任意数据库对象的权限的用户帐户。  
  
 内存优化表上的触发器需要使用此选项。  
  
 有关详细信息，请参阅 [EXECUTE AS 子句 (Transact-SQL)](../../t-sql/statements/execute-as-clause-transact-sql.md)。  
  
 NATIVE_COMPILATION  
 指示触发器已本机编译。  
  
 内存优化表上的触发器需要使用此选项。  
  
 SCHEMABINDING  
 确保不能删除或更改触发器引用的表。  
  
 内存优化表上的触发器需要使用此选项，但此选项不支持传统表上的触发器。  
  
 FOR | AFTER  
 AFTER 指定 DML 触发器仅在触发 SQL 语句中指定的所有操作都已成功执行时才被触发。 所有的引用级联操作和约束检查也必须在激发此触发器之前成功完成。  
  
 如果仅指定 FOR 关键字，则 AFTER 为默认值。  
  
 不能对视图定义 AFTER 触发器。  
  
 INSTEAD OF  
 指定执行 DML 触发器*而不是*触发 SQL 语句，因此，其优先级高于触发语句的操作。 不能为 DDL 或登录触发器指定 INSTEAD OF。  
  
 对于表或视图，每个 INSERT、UPDATE 或 DELETE 语句最多可定义一个 INSTEAD OF 触发器。 但是，可以为具有自己的 INSTEAD OF 触发器的多个视图定义视图。  
  
 INSTEAD OF 触发器不可以用于使用 WITH CHECK OPTION 的可更新视图。 如果将 INSTEAD OF 触发器添加到指定了 WITH CHECK OPTION 的可更新视图中，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将引发错误。 用户须用 ALTER VIEW 删除该选项后才能定义 INSTEAD OF 触发器。  
  
 { [DELETE] [,] [INSERT] [,] [UPDATE] }  
 指定数据修改语句，这些语句可在 DML 触发器对此表或视图进行尝试时激活该触发器。 必须至少指定一个选项。 在触发器定义中允许使用上述选项的任意顺序组合。  
  
 对于 INSTEAD OF 触发器，不允许对具有指定级联操作 ON DELETE 的引用关系的表使用 DELETE 选项。 同样，也不允许对具有指定级联操作 ON UPDATE 的引用关系的表使用 UPDATE 选项。  
  
 WITH APPEND  
 **适用范围**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]。  
  
 指定应该再添加一个现有类型的触发器。 WITH APPEND 不能与 INSTEAD OF 触发器一起使用。如果显式声明了 AFTER 触发器，则也不能使用该子句。 仅当为了向后兼容而指定了 FOR 时（但没有 INSTEAD OF 或 AFTER）时，才能使用 WITH APPEND。 如果指定了 EXTERNAL NAME（即触发器为 CLR 触发器），则不能指定 WITH APPEND。  
  
 event_type  
 执行之后将导致激发 DDL 触发器的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语言事件的名称。 [DDL 事件](../../relational-databases/triggers/ddl-events.md)中列出了 DDL 触发器的有效事件。  
  
 event_group  
 预定义的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语言事件分组的名称。 执行任何属于 event_group 的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语言事件之后，都将激发 DDL 触发器。 [DDL 事件组](../../relational-databases/triggers/ddl-event-groups.md)中列出了 DDL 触发器的有效事件组。  
  
 CREATE TRIGGER 运行完成后，*event_group* 还将充当宏，将它涉及的事件类型添加到 sys.trigger_events 目录视图中。  
  
 NOT FOR REPLICATION  
 **适用范围**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 指示当复制代理修改涉及到触发器的表时，不应执行触发器。  
  
 sql_statement  
 触发条件和操作。 触发器条件指定其他标准，用于确定尝试的 DML、DDL 或 logon 事件是否导致执行触发器操作。  
  
 尝试上述操作时，将执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句中指定的触发器操作。  
  
 触发器可以包含任意数量和类型的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句，但也有例外。 有关详细信息，请参阅“备注”。 触发器的用途是根据数据修改或定义语句来检查或更改数据；它不应向用户返回数据。 触发器中的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句常常包含[控制流语言](~/t-sql/language-elements/control-of-flow.md)。  
  
 DML 触发器使用 deleted 和 inserted 逻辑（概念）表。 它们在结构上类似于定义了触发器的表，即对其尝试执行了用户操作的表。 deleted 和 inserted 表保存了可能会被用户更改的行的旧值或新值。 例如，若要检索 `deleted` 表中的所有值，则使用：  
  
```sql  
SELECT * FROM deleted;  
```  
  
 有关详细信息，请参阅[使用插入的和删除的表](../../relational-databases/triggers/use-the-inserted-and-deleted-tables.md)。  
  
 DDL 和登录触发器使用 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md) 函数来捕获有关触发事件的信息。 有关详细信息，请参阅[使用 EVENTDATA 函数](../../relational-databases/triggers/use-the-eventdata-function.md)。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许通过表或视图的 INSTEAD OF 触发器来更新 **text**、**ntext** 或 **image** 列。  
  
> [!IMPORTANT]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的未来版本中将删除 **ntext**、**text** 和 **image** 数据类型。 请避免在新开发工作中使用这些数据类型，并考虑修改当前使用这些数据类型的应用程序。 请改用 [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)、 [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)和 [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) 。 AFTER 和 INSTEAD OF 触发器均支持插入和删除的表中的 **varchar(MAX)**、**nvarchar(MAX)** 和 **varbinary(MAX)** 数据。  
  
 对于内存优化表中的触发器，顶层允许的唯一 sql_statement 是 ATOMIC 块。 ATOMIC 块内允许的 T-SQL 由本地进程内允许的 T-SQL 决定。  
  
 \< method_specifier > **适用于**：[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 对于 CLR 触发器，指定程序集与触发器绑定的方法。 该方法不能带有任何参数，并且必须返回空值。 class_name 必须是有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 标识符，并且它必须作为类存在于可见程序集中。 如果该类有一个使用“.”来分隔命名空间部分的命名空间限定名称，则类名必须用 [] 或“ ”分隔符分隔。 该类不能为嵌套类。  
  
> [!NOTE]  
>  默认情况下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法运行 CLR 代码。 你可以创建、修改和删除引用托管代码模块的数据库对象，但是，除非使用 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) 启用了 [clr enabled 选项](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)，否则不会在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中执行这些引用。  
  
## <a name="remarks-for-dml-triggers"></a>DML 触发器的注释  
 DML 触发器经常用于强制执行业务规则和数据完整性。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过 ALTER TABLE 和 CREATE TABLE 语句来提供声明性引用完整性 (DRI)。 但是，DRI 不提供跨数据库引用完整性。 引用完整性是指有关表的主键和外键之间的关系的规则。 若要强制实现引用完整性，请在 ALTER TABLE 和 CREATE TABLE 中使用 PRIMARY KEY 和 FOREIGN KEY 约束。 如果触发器表存在约束，则在 INSTEAD OF 触发器执行之后和 AFTER 触发器执行之前检查这些约束。 如果违反了约束，则将回滚 INSTEAD OF 触发器操作，并且不激活 AFTER 触发器。  
  
 可以使用 sp_settriggerorder 来指定要对表执行的第一个和最后一个 AFTER 触发器。 对于一个表，只能为每个 INSERT、UPDATE 和 DELETE 操作指定一个第一个和最后一个 AFTER 触发器。 如果在同一个表上还有其他 AFTER 触发器，这些触发器将随机执行。  
  
 如果 ALTER TRIGGER 语句更改了第一个或最后一个触发器，将删除所修改触发器上设置的第一个或最后一个属性，并且必须使用 sp_settriggerorder 重置顺序值。  
  
 只有在成功执行触发 SQL 语句之后，才会执行 AFTER 触发器。 判断执行成功的标准是：执行了所有与已更新对象或已删除对象相关联的引用级联操作和约束检查。 AFTER 触发器不会在同一个表中以递归方式触发 INSTEAD OF 触发器。  
  
 如果为表定义的 INSTEAD OF 触发器对表执行了一般会再次触发 INSTEAD OF 触发器的语句，该触发器不会被递归调用， 而是像表中没有 INSTEAD OF 触发器一样处理该语句，并启动一系列约束操作和 AFTER 触发器执行。 例如，如果触发器定义为表的 INSTEAD OF INSERT 触发器，并且触发器对同一个表执行 INSERT 语句，则由 INSTEAD OF 触发器执行的 INSERT 语句不会再次调用该触发器。 触发器执行的 INSERT 将启动执行约束操作的进程，并触发为表定义的任一 AFTER INSERT 触发器。  
  
 如果为视图定义的 INSTEAD OF 触发器对视图执行了一条通常会再次触发 INSTEAD OF 触发器的语句，该语句不会被递归调用， 而是将该语句解析为对视图所依存的基本表进行的修改。 在这种情况下，视图定义必须满足可更新视图的所有约束。 有关可更新视图的定义，请参阅[通过视图修改数据](../../relational-databases/views/modify-data-through-a-view.md)。  
  
 例如，如果触发器定义为视图的 INSTEAD OF UPDATE 触发器，并且触发器执行引用同一视图的 UPDATE 语句，则由 INSTEAD OF 触发器执行的 UPDATE 语句不会再次调用该触发器。 对视图处理由该触发器执行的 UPDATE 语句时，就像该视图没有 INSTEAD OF 触发器一样。 由 UPDATE 更改的列必须解析到一个基表。 对基表的每次修改都将应用约束并触发为该表定义的 AFTER 触发器。  
  
### <a name="testing-for-update-or-insert-actions-to-specific-columns"></a>测试对指定列的 UPDATE 或 INSERT 操作  
 您可以设计一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 触发器，根据对特定列的 UPDATE 或 INSERT 修改来执行某些操作。 可在触发器的主体中使用 [UPDATE()](../../t-sql/functions/update-trigger-functions-transact-sql.md) 或 [COLUMNS_UPDATED](../../t-sql/functions/columns-updated-transact-sql.md) 来达到此目的。 UPDATE() 可以测试对某个列的 UPDATE 或 INSERT 尝试。 COLUMNS_UPDATED 可以测试对多个列执行的 UPDATE 或 INSERT 操作，并返回一个位模式，指示插入或更新的列。  
  
### <a name="trigger-limitations"></a>触发器限制  
 CREATE TRIGGER 必须是批处理中的第一条语句，并且只能应用于一个表。  
  
 触发器只能在当前的数据库中创建，但是可以引用当前数据库的外部对象。  
  
 如果指定了触发器架构名称来限定触发器，则将以相同的方式限定表名称。  
  
 在同一条 CREATE TRIGGER 语句中，可以为多种用户操作（如 INSERT 和 UPDATE）定义相同的触发器操作。  
  
 如果一个表的外键包含对定义的 DELETE/UPDATE 操作的级联，则不能对为表上定义 INSTEAD OF DELETE/UPDATE 触发器。  
  
 在触发器内可以指定任意的 SET 语句。 选择的 SET 选项在触发器执行期间保持有效，然后恢复为原来的设置。  
  
 如果触发了一个触发器，结果将返回给执行调用的应用程序，就像使用存储过程一样。 若要避免由于触发器触发而向应用程序返回结果，请不要包含返回结果的 SELECT 语句，也不要包含在触发器中执行变量赋值的语句。 包含向用户返回结果的 SELECT 语句或进行变量赋值的语句的触发器需要特殊处理；这些返回的结果必须写入允许修改触发器表的每个应用程序中。 如果必须在触发器中进行变量赋值，则应该在触发器的开头使用 SET NOCOUNT 语句以避免返回任何结果集。  
  
 虽然 TRUNCATE TABLE 语句实际上就是 DELETE 语句，但是它不会激活触发器，因为该操作不记录各个行删除。 然而，仅那些具有执行 TRUNCATE TABLE 语句的权限的用户才需要考虑是否无意中因为此方式而导致没有使用 DELETE 触发器。  
  
 无论有日志记录还是无日志记录，WRITETEXT 语句都不触发触发器。  
  
 在 DML 触发器中不允许使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。  
  
||||  
|-|-|-|  
|ALTER DATABASE|CREATE DATABASE|DROP DATABASE|  
|RESTORE DATABASE|RESTORE LOG|RECONFIGURE|  
  
 另外，如果对作为触发操作目标的表或视图使用 DML 触发器，则不允许在该触发器的主体中使用下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。  
  
||||  
|-|-|-|  
|CREATE INDEX（包括 CREATE SPATIAL INDEX 和 CREATE XML INDEX）|ALTER INDEX|DROP INDEX|  
|DBCC DBREINDEX|ALTER PARTITION FUNCTION|DROP TABLE|  
|用于执行以下操作的 ALTER TABLE：<br /><br /> 添加、修改或删除列。<br /><br /> 切换分区。<br /><br /> 添加或删除 PRIMARY KEY 或 UNIQUE 约束。|||  
  
> [!NOTE]  
>  因为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支持针对系统表的用户定义的触发器，因此我们建议不要为系统表创建用户定义触发器。 

### <a name="optimizing-dml-triggers"></a>优化 DML 触发器
 触发器在事务中工作（隐式的或非隐式的），开启后，它们会锁定资源。 除非确认（使用 COMMIT）或拒绝（使用 ROLLBACK）事务，否则，锁定将保持不变。 触发器运行时间越长，另一进程被锁定的可能性就越高。 因此，触发器应以尽可能减少持续时间的方式写入。 一种实现方法是，在 DML 语句更改 0 行时发布触发器。 

要发布不更改任何行的触发器命令，可使用系统变量 [ROWCOUNT_BIG](https://docs.microsoft.com/it-it/sql/t-sql/functions/rowcount-big-transact-sql)。 

以下 T-SQL 代码片段将完成此目标，并应显示在每个 DML 触发器的开头：

```sql
IF (@@ROWCOUNT_BIG = 0)
RETURN;
```
  
  
## <a name="remarks-for-ddl-triggers"></a>DDL 触发器的注释  
 DDL 触发器像标准触发器一样，在响应事件时执行存储过程。 但与标准触发器不同的是，它们并不在响应对表或视图的 UPDATE、INSERT 或 DELETE 语句时执行存储过程。 它们主要在响应数据定义语言 (DDL) 语句执行存储过程。 这些语句包括 CREATE、ALTER、DROP、GRANT、DENY、REVOKE 和 UPDATE STATISTICS 等语句。 执行 DDL 式操作的系统存储过程也可以激发 DDL 触发器。  
  
> [!IMPORTANT]  
>  测试 DDL 触发器，以确定它们对执行系统存储过程的响应。 例如，CREATE TYPE 语句以及 sp_addtype 和 sp_rename 存储过程都将激发针对 CREATE_TYPE 事件创建的 DDL 触发器。  
  
 有关 DDL 触发器的详细信息，请参阅 [DDL 触发器](../../relational-databases/triggers/ddl-triggers.md)。  
  
 对于影响局部或全局临时表和存储过程的事件，不会触发 DDL 触发器。  
  
 与 DML 触发器不同，DDL 触发器的作用域不是架构。 因此，不能将 OBJECT_ID、OBJECT_NAME、OBJECTPROPERTY 和 OBJECTPROPERTYEX 之类的函数用于查询有关 DDL 触发器的元数据。 请改用目录视图。 有关详细信息，请参阅[获取有关 DDL 触发器的信息](../../relational-databases/triggers/get-information-about-ddl-triggers.md)。  
  
> [!NOTE]  
>  服务器范围内的 DDL 触发器显示在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 对象资源管理器的“触发器”文件夹中。 此文件夹位于 **“服务器对象”** 文件夹下。 数据库范围内的 DDL 触发器显示在“数据库触发器”文件夹中。 此文件夹位于相应数据库的 **“可编程性”** 文件夹下。  
  
## <a name="logon-triggers"></a>登录触发器  
 登录触发器将为响应 LOGON 事件而执行存储过程。 与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例建立用户会话时将引发此事件。 登录触发器将在登录的身份验证阶段完成之后且用户会话实际建立之前激发。 因此，来自触发器内部且通常将到达用户的所有消息（例如错误消息和来自 PRINT 语句的消息）会传送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志。 有关详细信息，请参阅[登录触发器](../../relational-databases/triggers/logon-triggers.md)。  
  
 如果身份验证失败，将不激发登录触发器。  
  
 在登录触发器中不支持分布式事务。 在激发包含分布式事务的登录触发器时，将返回错误 3969。  
  
### <a name="disabling-a-logon-trigger"></a>禁用登录触发器  
 登录触发器可以有效地阻止所有用户（包括 [!INCLUDE[ssDE](../../includes/ssde-md.md)] sysadmin **固定服务器角色的成员）与** 的成功连接。 在登录触发器正在阻止连接时， **sysadmin** 固定服务器角色的成员可通过使用专用管理员连接，或者通过以最小配置模式 (-f) 启动 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，来进行连接。 有关详细信息，请参阅 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)。  
  
## <a name="general-trigger-considerations"></a>常规触发器注意事项  
  
### <a name="returning-results"></a>返回结果  
 SQL Server 的未来版本中将删除从触发器返回结果的功能。 返回结果集的触发器可能会导致应用程序出现意外的行为，而这些行为并不符合它们的设计意图。 避免在新的开发工作中从触发器返回结果集，并计划修改当前执行此操作的应用程序。 若要防止触发器返回结果集，请将 [disallow results from triggers 选项](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md)设置为 1。  
  
 登录触发器始终不允许返回结果集，并且这种行为不可配置。 如果登录触发器确实生成了结果集，则此触发器将无法执行，并且将拒绝触发此触发器的登录尝试。  
  
### <a name="multiple-triggers"></a>多个触发器  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许为每个 DML、DDL 或 LOGON 事件创建多个触发器。 例如，如果为已经有了 UPDATE 触发器的表执行 CREATE TRIGGER FOR UPDATE，则将再创建一个 UPDATE 触发器。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 早期版本中，对于每个表，每个 INSERT、UPDATE 或 DELETE 数据修改事件只允许有一个触发器。  
  
### <a name="recursive-triggers"></a>递归触发器  
 如果使用 ALTER DATABASE 启动了 RECURSIVE_TRIGGERS 设置，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 还允许递归调用触发器。  
  
 递归触发器可以采用下列递归类型：  
  
-   间接递归  
  
     在间接递归中，一个应用程序更新了表 T1。 这触发了触发器 TR1，从而更新了表 T2。 在这种情况下，将触发触发器 T2，从而更新 T1。  
  
-   直接递归  
  
     在直接递归中，应用程序更新了表 T1。 这触发了触发器 TR1，从而更新了表 T1。 由于表 T1 被更新，将再次触发触发器 TR1，依此类推。  
  
 以下示例同时使用了间接和直接触发器递归。假设对表 T1 定义了两个更新触发器 TR1 和 TR2。 触发器 TR1 以递归方式更新表 T1。 UPDATE 语句各执行 TR1 和 TR2 一次。 另外，执行 TR1 将触发执行 TR1（递归）和 TR2。 指定触发器的 inserted 和 deleted 表包含仅与调用触发器的 UPDATE 语句对应的行。  
  
> [!NOTE]  
>  仅当使用 ALTER DATABASE 启用了 RECURSIVE_TRIGGERS 设置时，才能发生前述行为。 执行为特定事件定义的多个触发器时，并没有确定的执行顺序。 每个触发器都应是自包含的。  
  
 禁用 RECURSIVE_TRIGGERS 的设置只能阻止直接递归。 若要同时禁用间接递归，请使用 sp_configure 将 nested triggers 服务器选项设置为 0。  
  
 如果任一触发器执行了 ROLLBACK TRANSACTION 语句，则无论嵌套级是多少，都不会再执行其他触发器。  
  
### <a name="nested-triggers"></a>嵌套触发器  
 触发器最多可以嵌套 32 级。 如果一个触发器更改了包含另一个触发器的表，则第二个触发器将被触发，然后该触发器又可以调用第三个触发器，依此类推。 如果链中任意一个触发器引发了无限循环，则会超出嵌套级限制，从而导致取消触发器。 如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 触发器通过引用 CLR 例程、类型或聚合来执行托管代码，则此引用只算 32 级嵌套限制中的一级。 从托管代码内部调用的方法不根据此限制进行计数  
  
 若要禁用嵌套触发器，请用 sp_configure 将 nested triggers 选项设置为 0（关闭）。 默认配置允许嵌套触发器。 如果关闭嵌套触发器，则不管使用 ALTER DATABASE 设置的 RECURSIVE_TRIGGERS 设置如何，都将同时禁用递归触发器。  
  
 即使 **nested triggers** 服务器配置选项设置为 0，也会激发嵌套在 INSTEAD OF 触发器内的第一个 AFTER 触发器。 但是，在此设置下，不会激发以后的 AFTER 触发器。 建议你检查应用程序中的嵌套触发器，确定当 **nested triggers** 服务器配置选项设置为 0 时，应用程序是否遵循有关此行为的业务规则，然后进行适当的修改。  
  
### <a name="deferred-name-resolution"></a>延迟名称解析  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允许 [!INCLUDE[tsql](../../includes/tsql-md.md)] 存储过程、触发器和批处理引用编译时不存在的表。 这种功能称为延迟名称解析。  
  
## <a name="permissions"></a>权限  
 若要创建 DML 触发器，则需要对要创建触发器的表或视图具有 ALTER 权限。  
  
 若要创建具有服务器范围的 DDL 触发器 (ON ALL SERVER) 或登录触发器，则需要对服务器拥有 CONTROL SERVER 权限。 若要创建具有数据库范围的 DDL 触发器 (ON DATABASE)，则需要在当前数据库中有 ALTER ANY DATABASE DDL TRIGGER 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-a-dml-trigger-with-a-reminder-message"></a>A. 使用包含提醒消息的 DML 触发器  
 如果有人试图在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库的 `Customer` 表中添加或更改数据，下列 DML 触发器将向客户端显示一条消息。  
  
```sql  
CREATE TRIGGER reminder1  
ON Sales.Customer  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Customer Relations', 16, 10);  
GO  
```  
  
### <a name="b-using-a-dml-trigger-with-a-reminder-e-mail-message"></a>B. 使用包含提醒电子邮件的 DML 触发器  
 如果 `MaryM` 表发生更改，以下示例将向指定人员 (`Customer`) 发送电子邮件。  
  
```sql  
CREATE TRIGGER reminder2  
ON Sales.Customer  
AFTER INSERT, UPDATE, DELETE   
AS  
   EXEC msdb.dbo.sp_send_dbmail  
        @profile_name = 'AdventureWorks2012 Administrator',  
        @recipients = 'danw@Adventure-Works.com',  
        @body = 'Don''t forget to print a report for the sales force.',  
        @subject = 'Reminder';  
GO  
```  
  
### <a name="c-using-a-dml-after-trigger-to-enforce-a-business-rule-between-the-purchaseorderheader-and-vendor-tables"></a>C. 使用 DML AFTER 触发器在 PurchaseOrderHeader 和 Vendor 表之间强制实现业务规则  
 由于 CHECK 约束只能引用定义了列级或表级约束的列，表间的任何约束（在本例中是业务规则）都必须定义为触发器。  
  
 以下示例在 AdventureWorks2012 数据库中创建 DML 触发器。 如果有人试图将一个新采购订单插入到 `PurchaseOrderHeader` 表中，此触发器会进行检查以确保供应商具有良好的信用等级（不为 5）。 若要获取供应商的信用等级，必须引用 `Vendor` 表。 如果信用等级太低，则显示信息，并且不执行该插入操作。  
  
```sql  
-- This trigger prevents a row from being inserted in the Purchasing.PurchaseOrderHeader 
-- table when the credit rating of the specified vendor is set to 5 (below average).  
  
CREATE TRIGGER Purchasing.LowCredit ON Purchasing.PurchaseOrderHeader  
AFTER INSERT  
AS  
IF (@@ROWCOUNT_BIG  = 0)
RETURN;
IF EXISTS (SELECT *  
           FROM Purchasing.PurchaseOrderHeader AS p   
           JOIN inserted AS i   
           ON p.PurchaseOrderID = i.PurchaseOrderID   
           JOIN Purchasing.Vendor AS v   
           ON v.BusinessEntityID = p.VendorID  
           WHERE v.CreditRating = 5  
          )  
BEGIN  
RAISERROR ('A vendor''s credit rating is too low to accept new  
purchase orders.', 16, 1);  
ROLLBACK TRANSACTION;  
RETURN   
END;  
GO  
  
-- This statement attempts to insert a row into the PurchaseOrderHeader table  
-- for a vendor that has a below average credit rating.  
-- The AFTER INSERT trigger is fired and the INSERT transaction is rolled back.  
  
INSERT INTO Purchasing.PurchaseOrderHeader (RevisionNumber, Status, EmployeeID,  
VendorID, ShipMethodID, OrderDate, ShipDate, SubTotal, TaxAmt, Freight)  
VALUES (  
2  
,3  
,261  
,1652  
,4  
,GETDATE()  
,GETDATE()  
,44594.55  
,3567.564  
,1114.8638 );  
GO  
  
```  
  
### <a name="d-using-a-database-scoped-ddl-trigger"></a>D. 使用具有数据库范围的 DDL 触发器  
 下面的示例使用 DDL 触发器来防止从数据库中删除任何同义词。  
  
```sql  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_SYNONYM  
AS   
IF (@@ROWCOUNT = 0)
RETURN;
   RAISERROR ('You must disable Trigger "safety" to drop synonyms!',10, 1)  
   ROLLBACK  
GO  
DROP TRIGGER safety  
ON DATABASE;  
GO  
```  
  
### <a name="e-using-a-server-scoped-ddl-trigger"></a>E. 使用具有服务器范围的 DDL 触发器  
 在以下示例中，如果当前服务器实例上出现任何 CREATE DATABASE 事件，则使用 DDL 触发器输出一条消息，并使用 `EVENTDATA` 函数检索对应 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句的文本。 有关在 DDL 触发器中使用 EVENTDATA 的更多示例，请参阅[使用 EVENTDATA 函数](../../relational-databases/triggers/use-the-eventdata-function.md)。  
  
**适用范围**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
```sql  
CREATE TRIGGER ddl_trig_database   
ON ALL SERVER   
FOR CREATE_DATABASE   
AS   
    PRINT 'Database Created.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
GO  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
```  
  
### <a name="f-using-a-logon-trigger"></a>F. 使用登录触发器  
 下面的登录触发器示例拒绝了作为 *login_test* 登录名的成员登录 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的尝试（如果在此登录名下已运行三个用户会话）。  
  
**适用范围**： [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
```sql  
USE master;  
GO  
CREATE LOGIN login_test WITH PASSWORD = '3KHJ6dhx(0xVYsdf' MUST_CHANGE,  
    CHECK_EXPIRATION = ON;  
GO  
GRANT VIEW SERVER STATE TO login_test;  
GO  
CREATE TRIGGER connection_limit_trigger  
ON ALL SERVER WITH EXECUTE AS 'login_test'  
FOR LOGON  
AS  
BEGIN  
IF ORIGINAL_LOGIN()= 'login_test' AND  
    (SELECT COUNT(*) FROM sys.dm_exec_sessions  
            WHERE is_user_process = 1 AND  
                original_login_name = 'login_test') > 3  
    ROLLBACK;  
END;  
  
```  
  
### <a name="g-viewing-the-events-that-cause-a-trigger-to-fire"></a>G. 查看导致触发器触发的事件  
 以下示例将查询 `sys.triggers` 和 `sys.trigger_events` 目录视图，以确定是哪个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语言事件导致触发了 `safety`。 `safety` 是在前一个示例中创建的。  
  
```sql  
SELECT TE.*  
FROM sys.trigger_events AS TE  
JOIN sys.triggers AS T ON T.object_id = TE.object_id  
WHERE T.parent_class = 0 AND T.name = 'safety';  
GO  
```  

    

## <a name="see-also"></a>另请参阅  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [COLUMNS_UPDATED (Transact-SQL)](../../t-sql/functions/columns-updated-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DROP TRIGGER (Transact-SQL)](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER (Transact-SQL)](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER (Transact-SQL)](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [TRIGGER_NESTLEVEL (Transact-SQL)](../../t-sql/functions/trigger-nestlevel-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.dm_sql_referenced_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [sys.sql_expression_dependencies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sp_helptext (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_rename (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_settriggerorder (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql.md)   
 [UPDATE() (Transact-SQL)](../../t-sql/functions/update-trigger-functions-transact-sql.md)   
 [获取有关 DML 触发器的信息](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [获取有关 DDL 触发器的信息](../../relational-databases/triggers/get-information-about-ddl-triggers.md)   
 [sys.triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  


