---
title: 表值构造函数 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- inserting multiple rows
- row value expression
- row constructor [SQL Server]
- table value constructor [SQL Server]
ms.assetid: e57cd31d-140e-422f-8178-2761c27b9deb
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6c9980312429ca621da04953f6428e61119f2515
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="table-value-constructor-transact-sql"></a>表值构造函数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定要构建到某一表中的一组行值表达式。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表值构造函数允许在单个 DML 语句中指定多行数据。 该表值构造函数可以在 INSERT 语句的 VALUES 子句中指定，在 MERGE 语句的 USING \<源表> 子句中指定，以及在 FROM 子句的派生表定义中指定。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
VALUES ( <row value expression list> ) [ ,...n ]   
  
<row value expression list> ::=  
    {<row value expression> } [ ,...n ]  
  
<row value expression> ::=  
    { DEFAULT | NULL | expression }  
```  
  
## <a name="arguments"></a>参数  
 VALUES  
 介绍行值表达式列表。 每个列表都必须用括号括起来并由逗号分隔。  
  
 在每个列表中指定的值的数目必须相同，并且值必须采用与表中的列相同的顺序。 表中每个列的值必须指定，或者列列表必须显式为每个传入值指定列。  
  
 DEFAULT  
 强制[!INCLUDE[ssDE](../../includes/ssde-md.md)]插入为列定义的默认值。 如果某列并不存在默认值，并且该列允许 Null 值，则插入 NULL。 DEFAULT 对标识列无效。 当在表值构造函数中指定时，只在 INSERT 语句中允许 DEFAULT。  
  
 *expression*  
 一个常量、变量或表达式。 表达式不能包含 EXECUTE 语句。  
  
## <a name="limitations-and-restrictions"></a>限制和局限  
 表值构造函数可以用以下两种方式之一进行使用：直接用在 INSERT … VALUES 语句的 VALUES 列表中， 或在任何允许派生表的位置用作派生表。 如果行数超过最大值，则返回错误 10738。 若要插入超过限制所允许的行数，请使用下列方法之一：  
  
-   创建多个 INSERT 语句  
  
-   使用派生表  
  
-   通过使用 bcp 实用工具或 BULK INSERT 语句批量导入数据  
  
 只允许单个标量值作为行值表达式。 涉及多列的子查询不允许作为行值表达式。 例如，以下代码导致语法错误，因为第三个行值表达式列表包含具有多列的子查询。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE dbo.MyProducts (Name varchar(50), ListPrice money);  
GO  
-- This statement fails because the third values list contains multiple columns in the subquery.  
INSERT INTO dbo.MyProducts (Name, ListPrice)  
VALUES ('Helmet', 25.50),  
       ('Wheel', 30.00),  
       (SELECT Name, ListPrice FROM Production.Product WHERE ProductID = 720);  
GO  
  
```  
  
 但是，可以通过单独在子查询中指定每一列，重新编写该语句。 下面的示例成功地将三行插入 `MyProducts` 表中。  
  
```  
INSERT INTO dbo.MyProducts (Name, ListPrice)  
VALUES ('Helmet', 25.50),  
       ('Wheel', 30.00),  
       ((SELECT Name FROM Production.Product WHERE ProductID = 720),  
        (SELECT ListPrice FROM Production.Product WHERE ProductID = 720));  
GO  
  
```  
  
## <a name="data-types"></a>数据类型  
 在多行 INSERT 语句中指定的值遵循 UNION ALL 语法的数据类型约定属性。 这会导致不匹配类型隐式转换到更高[优先级](../../t-sql/data-types/data-type-precedence-transact-sql.md)的类型。 如果此转换不是所支持的隐式转换，则返回错误。 例如，以下语句将整数值和字符值插入到类型为 char 的列中。  
  
```  
CREATE TABLE dbo.t (a int, b char);  
GO  
INSERT INTO dbo.t VALUES (1,'a'), (2, 1);  
GO  
```  
  
 运行 INSERT 语句时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 尝试将 'a' 转换为整数，因为数据类型优先级指示整数类型的优先级高于字符。 转换失败，并且返回错误。 您可以根据需要显式转换值，从而避免发生此错误。 例如，前面的语句可以编写为：  
  
```  
INSERT INTO dbo.t VALUES (1,'a'), (2, CONVERT(CHAR,1));  
```  
  
## <a name="examples"></a>示例  
  
### <a name="a-inserting-multiple-rows-of-data"></a>A. 插入多行数据  
 下面的示例创建表 `dbo.Departments`，然后使用表值构造函数将五行数据插入到该表中。 由于提供了所有列的值并按表中各列的顺序列出这些值，因此不必在列列表中指定列名。  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO Production.UnitMeasure  
VALUES (N'FT2', N'Square Feet ', '20080923'), (N'Y', N'Yards', '20080923'), (N'Y3', N'Cubic Yards', '20080923');  
GO  
  
```  
  
### <a name="b-inserting-multiple-rows-with-default-and-null-values"></a>B. 使用 DEFAULT 和 NULL 值插入多行  
 下面的示例说明如何在使用表值构造函数向表中插入行时指定 DEFAULT 和 NULL。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE Sales.MySalesReason(  
SalesReasonID int IDENTITY(1,1) NOT NULL,  
Name dbo.Name NULL ,  
ReasonType dbo.Name NOT NULL DEFAULT 'Not Applicable' );  
GO  
INSERT INTO Sales.MySalesReason   
VALUES ('Recommendation','Other'), ('Advertisement', DEFAULT), (NULL, 'Promotion');  
  
SELECT * FROM Sales.MySalesReason;  
  
```  
  
### <a name="c-specifying-multiple-values-as-a-derived-table-in-a-from-clause"></a>C. 在 FROM 子句中将多个值指定为派生表  
 下面的示例在 SELECT 语句的 FROM 子句中使用表值构造函数指定多个值。  
  
```  
SELECT a, b FROM (VALUES (1, 2), (3, 4), (5, 6), (7, 8), (9, 10) ) AS MyTable(a, b);  
GO  
-- Used in an inner join to specify values to return.  
SELECT ProductID, a.Name, Color  
FROM Production.Product AS a  
INNER JOIN (VALUES ('Blade'), ('Crown Race'), ('AWC Logo Cap')) AS b(Name)   
ON a.Name = b.Name;  
  
```  
  
### <a name="d-specifying-multiple-values-as-a-derived-source-table-in-a-merge-statement"></a>D. 在 MERGE 语句中将多个值指定为派生源表  
 下面的示例使用 MERGE 以更新或插入行的方式来修改 `SalesReason` 表。 当源表中的 `NewName` 值与目标表 (`Name`) 的 `SalesReason` 列中的值匹配时，就会更新此目标表中的 `ReasonType` 列。 当 `NewName` 的值不匹配时，就会将源行插入到目标表中。 此源表是一个派生表，它使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 表值构造函数指定源表的多个行。  
  
```  
USE AdventureWorks2012;  
GO  
-- Create a temporary table variable to hold the output actions.  
DECLARE @SummaryOfChanges TABLE(Change VARCHAR(20));  
  
MERGE INTO Sales.SalesReason AS Target  
USING (VALUES ('Recommendation','Other'), ('Review', 'Marketing'), ('Internet', 'Promotion'))  
       AS Source (NewName, NewReasonType)  
ON Target.Name = Source.NewName  
WHEN MATCHED THEN  
UPDATE SET ReasonType = Source.NewReasonType  
WHEN NOT MATCHED BY TARGET THEN  
INSERT (Name, ReasonType) VALUES (NewName, NewReasonType)  
OUTPUT $action INTO @SummaryOfChanges;  
  
-- Query the results of the table variable.  
SELECT Change, COUNT(*) AS CountPerChange  
FROM @SummaryOfChanges  
GROUP BY Change;  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [MERGE (Transact-SQL)](../../t-sql/statements/merge-transact-sql.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)  
  
  
