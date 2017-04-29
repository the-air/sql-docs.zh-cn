---
title: "在表设计器中保存工作 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tables [SQL Server], saving
- Table Designer, saving work
- saving tables
ms.assetid: 676e4a9a-be75-44d2-b011-6e7fb921de4a
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5643c68421bd731f9615a7e54e3e24d9f5237b37
ms.lasthandoff: 04/11/2017

---
# <a name="save-your-work-in-table-designer-visual-database-tools"></a>在表设计器中保存您的工作 (Visual Database Tools)
可以保存对表设计器中打开的表所做的更改。  
  
### <a name="to-save-a-table"></a>保存表  
  
1.  单击表设计器中的任意位置。  
  
2.  从“文件”菜单中，选择“保存 tablename”。  
  
3.  在“保存”对话框中，单击“是”以更新数据库。  
  
> [!NOTE]  
> 如果所保存的更改不影响其他表，则不会显示此对话框。  
  
> [!NOTE]  
> “保存”对话框中的表列表可能包含未修改的表。 例如，如果更改了某列的数据类型，而该列参与了与另一个表的关系，那么这两个表都将包括在此列表中。  
  
> [!NOTE]  
> 若要保存对所有打开的项（如表、视图、存储过程）的更改，请在“文件”菜单中，选择“全部保存”。  
  
## <a name="see-also"></a>另请参阅  
[表属性 (Visual Database Tools)](../../ssms/visual-db-tools/table-properties-visual-database-tools.md)  
  
