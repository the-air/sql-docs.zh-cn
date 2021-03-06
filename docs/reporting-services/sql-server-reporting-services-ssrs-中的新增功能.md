---
title: "Reporting Services (SSRS) 中的新增功能 | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "新增功能 [Reporting Services]"
  - "Reporting Services, 新增功能"
  - "SQL Server Reporting Services, 新增功能"
  - "SSRS, 新增功能"
ms.assetid: bc909063-6b84-4b3a-80d2-e93fc04b4b9d
caps.latest.revision: 206
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# SQL Server Reporting Services (SSRS) 中的新增功能
了解 SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 中的新增功能。 这包括主要功能区域，在发布新项时进行更新。
  
  有关 SQL Server 其他领域的新增功能的信息，请参阅 [SQL Server vNext 中的新增功能](../sql-server/what-s-new-in-sql-server-vnext.md)或 [SQL Server 2016 中的新增功能](../sql-server/what-s-new-in-sql-server-2016.md)。
  
 **下载** ![download](../analysis-services/media/download.png "download")
 
- 若要下载 SQL Server Reporting Services 中 2017 年 1 月的 Power BI 技术预览版报表以及 Power BI Desktop 版本 (SQL Server Reporting Services)，请转到 **[Microsoft 下载中心](https://go.microsoft.com/fwlink/?linkid=839351)**。
  
-   若要下载 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]，请转到  **[评估中心](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**。  
  
-   是否拥有 Azure 帐户？  然后转到 **[此处](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016sp1enterprisewindowsserver2016/)** ，以加速已安装有 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的虚拟机。  
  
 ![注释](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "注释")有关当前的发行说明，请参阅 [SSRS 中的 Power BI 技术预览版报表 - 发行说明](../reporting-services/reporting-services-发行说明.md)或 [SQL Server 2016 发行说明](../sql-server/sql-server-2016-release-notes.md)。  

## <a name="whats-new-in-the-january-2017-technical-preview-of-power-bi-reports-in-sql-server-reporting-services"></a>SQL Server Reporting Services 中 2017 年 1 月的 Power BI 技术预览版报表的新增功能

### <a name="reporting-services-has-a-new-setup-experience"></a>Reporting Services 拥有全新的安装体验

现在可以不通过 SQL Server 安装程序来安装 Reporting Services。 安装体验步骤减少，安装过程更便捷。 安装程序将为 Reporting Services 安装文件。 然后你可以为报表服务器配置数据库。 这要求你在环境中拥有对 SQL Server 数据库引擎服务器的访问权限。

![ssrs-standalone-setup1](../reporting-services/media/ssrs-standalone-setup1.png)

有关详细信息，请参阅[安装 SQL Server Reporting Services 中 2017 年 1 月的 Power BI 技术预览版报表](Install%20the%20January%202017%20Technical%20Preview%20of%20Power%20BI%20reports%20in%20SQL%20Server%20Reporting%20Services.md)。

### <a name="host-power-bi-reports-within-the-web-portal"></a>在 Web 门户中托管 Power BI 报表

现在可以将 Power BI Desktop 文件上传到 Reporting Services，并直接在 Web 门户中查看报表。

![ssrs-powerbi-report-config-render](../reporting-services/media/ssrs-powerbi-report-config-render.png)

需下载 Power BI Desktop 版本 (SQL Server Reporting Services)。 目前，预览版仅支持在此 Power BI Desktop 版本中创建的报表。 Power BI Desktop (SQL Server Reporting Services) 可与 Power BI 服务的 Power BI Desktop 并存。 若要下载 Power BI Desktop (SQL Server Reporting Services)，请转到 Microsoft 下载中心。 

目前，你只能通过与 Analysis Services 的实时连接（表格或多维）创建 Power BI 报表。 我们计划在将来的预览版中添加对其他数据源和使用 Power Query 功能的支持。

有关详细信息，请参阅 [Reporting Services 中的 Power BI 报表](../reporting-services/power-bi-reports-in-reporting-services.md)。
 
## <a name="whats-new-in-sql-server-2016"></a>SQL Server 2016 中的新增功能
  
### <a name="reporting-services-includessrswebportal-non-markdowntokenssrswebportal-non-markdownmdmd"></a>Reporting Services [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]  
 新的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]已推出。 这是一个经过更新的新式门户，综合了 KPI、移动报表、分页报表、Excel 和 Power BI Desktop 文件。 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]取代了以前版本中的报表管理器。 你还可以从 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]下载移动报表发布服务器和报表生成器，无需使用 ClickOnce 技术。
 
 若要创建移动报表，则需使用 [!INCLUDE[SS_MobileReptPub_Short](../includes/ss-mobilereptpub-short-md.md)]。  
  
 有关 [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 的详细信息，请参阅 [Web 门户（SSRS 本机模式）](../reporting-services/web-portal-ssrs-native-mode.md)。  
  
 ![ssRSPortal](../reporting-services/media/ssrsportal.png "ssRSPortal")  
 
 #### <a name="custom-branding-for-the-includessrswebportal-non-markdowntokenssrswebportal-non-markdownmdmd"></a>[!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 的自定义品牌 
  你可以通过品牌包使用组织的徽标和颜色来自定义 [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]。  
  
  有关自定义品牌的详细信息，请参阅[设置 Web 门户的品牌](http://msdn.microsoft.com/zh-cn/6dac97f7-02a6-4711-81a3-e850a6b40bf1)
 
 #### <a name="key-performance-indicators-kpi-in-the-includessrswebportal-non-markdowntokenssrswebportal-non-markdownmdmd"></a>[!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 中的关键绩效指标 (KPI) 

你可以在 [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 中直接创建与你所在的文件夹有上下文关系的 KPI。 在创建 KPI 时，可以选择数据集字段并汇总这些值。 还可以选择相关内容以钻取到更多详细信息。
  
 ![ssrs-webportal-kpi](../reporting-services/media/ssrs-webportal-kpi.png)
 
 有关详细信息，请参阅[使用 Web 门户中的 KPI](http://msdn.microsoft.com/zh-cn/a28cf500-6d47-4268-a248-04837e7a09eb)
  
 
 ### <a name="mobile-reports"></a>移动报表
 
Reporting Services 移动报表是针对各种外形规格进行了优化的专用报表，可以在用户访问移动设备上的报表时为其提供最佳体验。 移动报表提供各式各样的可视化效果：从时间表、类别图表和比较图表，到树状图和自定义地图。 将移动报表连接到各种数据源，包括本地 SQL Server Analysis Services 多维数据和表格数据。 在网格行和列可调整且移动报表元素灵活的设计图面上设计移动报表，这些报表可轻松缩放至任何屏幕大小。 然后，将这些移动报表保存到 Reporting Service 服务器，并在 iPad、iPhone、Android 手机和 Windows 10 设备上的浏览器或 Power BI 移动应用中进行查看和交互。
  
#### <a name="mobile-report-publisher"></a>移动报表发布服务器  
 [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)]允许你创建 SQL Server 移动报表并将其发布到 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]。  
  
 ![SS_MRP_LayoutTabSmall](../reporting-services/media/ss-mrp-layouttabsm.png "SS_MRP_LayoutTabSmall")  
  
 有关详细信息，请参阅[使用 SQL Server 移动报表发布服务器创建移动报表](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)。  
  
#### <a name="sql-server-mobile-reports-hosted-in-reporting-services-available-in-power-bi-mobile-app"></a>在 Reporting Services 中托管的 SQL Server 移动报表可以在 Power BI 移动应用中使用  
 在 iPad 和 iPhone 上使用的 iOS 版 Power BI 移动应用现在可以显示在本地报表服务器上托管的 SQL Server 移动报表。  
  
 ![SS_MRP_iPad_HomeSm](../reporting-services/media/ss-mrp-ipad-homesm.png "SS_MRP_iPad_HomeSm")  
  
 默认情况下，如果没有进行某些配置更改，你将无法进行连接。 有关如何才能让 Power BI 移动应用连接到报表服务器的详细信息，请参阅 [Enable a report server for Power BI Mobile access](../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md)。
  
### <a name="support-of-sharepoint-mode-and-sharepoint-2016"></a>SharePoint 模式和 SharePoint 2016 的支持  
 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 支持与 SharePoint 2013 和 SharePoint 2016 集成。
 
有关详细信息，请参阅：  
  
-   [支持的 SharePoint 和 Reporting Services 服务器及外接程序的组合 (SQL Server 2016)](../reporting-services/install-windows/supported combinations of sharepoint and reporting services server.md)  
  
-   [在何处查找用于 SharePoint 产品的 Reporting Services 外接程序](../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  
  
-   [安装 Reporting Services SharePoint 模式](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  

### <a name="microsoft-net-framework-4-support"></a>Microsoft .NET Framework 4 支持  
 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 支持最新版本的 Microsoft .NET Framework 4。 包括 4.0 版和 4.5.1 版。 如果没有安装任何版本的 .Net Framework 4.x， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装程序会在功能安装步骤安装 .NET 4.0。  

### <a name="report-improvements"></a>报表改进

**HTML 5 呈现引擎：**新的 HTML5 呈现引擎，面向“完整”Web 标准模式和新式浏览器。  新的呈现引擎不再依赖于一些老式浏览器使用的 Quirks 模式。
  
 有关浏览器支持的详细信息，请参阅 [Reporting Services 和 Power View 的浏览器支持](../reporting-services/browser-support-for-reporting-services-and-power-view.md)。  

**新型分页报表：** 设计美观的新型分页报表，提供适用于图表、仪表、映射和其他数据可视化对象的各种新奇且现代的样式。
  
**树状图和旭日图：**通过树状图 ![ssrs_treemap_icon](../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon") 和旭日图 ![ssrs_sunburst_icon](../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon") 增强报表的功能，以更好的方式显示分层数据。 有关详细信息，请参阅 [Tree Map and Sunburst Charts in Reporting Services](../reporting-services/report-design/tree-map-and-sunburst-charts-in-reporting-services.md)。  

**报表嵌入：** 你现在可以使用 iframe 以及 URL 参数将移动报表和分页报表嵌入其他网页和应用程序中。  

**将报表项固定到 Power BI 仪表板：**在 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]中查看报表时，可以选择报表项并将其固定到 [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] 仪表板。   可以固定的项为图表、仪表面板、映射和映像。 可以 **(1)** 选择包含要固定到的仪表板的组，**(2)** 选择要将项固定到的仪表板，并 **(3)** 选择希望仪表板中的磁贴进行更新的频率。   ![注释](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "注释")刷新由 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 订阅管理，固定项之后，可编辑该订阅并配置不同的刷新计划。  
  
 ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png) 
  
 有关详细信息，请参阅 [Power BI 报表服务器集成 (Configuration Manager)](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)和[将 Reporting Services 项固定到 Power BI 仪表板](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)。  
 
 **PowerPoint 呈现和导出：**Microsoft PowerPoint (PPTX) 格式是一种新的 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 呈现扩展插件。 你可以采用 PPTX 格式从以下常用应用程序导出报表：报表生成器、报表设计器（在 SSDT 中）和 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]。 如需示例，请参阅下图，其中显示了 [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]中的导出菜单。 
  
 ![ssrs-export-powerpoint](../reporting-services/media/ssrs-export-powerpoint.png) 
  
 你还可以选择适用于订阅输出的 PPTX 格式，并使用 Report Server URL 访问权限来呈现和导出报表。 例如，浏览器中的以下 URL 命令从报表服务器的命名实例导出报表。  
  
```  
http://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 有关详细信息，请参阅 [Export a Report Using URL Access](../reporting-services/export-a-report-using-url-access.md)。  
 
 **PDF 替换 ActiveX 进行远程打印：**报表查看器工具栏 ActiveX 打印体验已被替换为新式的基于 PDF 的体验，后者适用于各种受支持的浏览器，包括 Microsoft Edge。 不需要下载 ActiveX 控件！ 根据你所使用的浏览器以及所安装的 PDF 查看应用程序和服务，[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 会打开一个打印报表所需的打印对话框，或者提示你下载报表的 .PDF 文件。  作为管理员，你仍然可以在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]中禁用客户端打印。 有关详细信息，请参阅[启用和禁用 Reporting Services 的客户端打印](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)。

![ssrs-pdf-printing](../reporting-services/media/ssrs-pdf-printing.png)

### <a name="subscription-improvements"></a>订阅改进  
 
|功能|支持的服务器模式|  
|-------------|---------------------------|  
|**启用和禁用订阅**。 新用户界面选项可以快速禁用和启用订阅。 已禁用的订阅将维持自身的其他配置属性（例如计划），并且可以轻松地启用。<br /><br /> ![ssrs-enable-disable-subscriptions](../reporting-services/media/ssrs-enable-disable-subscriptions.png)<br /><br /> 有关详细信息，请参阅 [Disable or Pause Report and Subscription Processing](../reporting-services/subscriptions/disable-or-pause-report-and-subscription-processing.md)。|本机模式|  
|**订阅说明**。 你现在可以在创建新订阅时提供报表说明，作为订阅属性的一部分。 说明在订阅摘要页中提供。|SharePoint 和本机模式|  
|**更改订阅所有者**。 增强的用户界面，可以快速更改订阅的所有者。 旧版 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 允许管理员使用脚本来更改订阅所有者。 从 [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] 版本开始，你可以使用用户界面或脚本更改订阅所有者。 当用户离开组织或者更改其在组织中的角色时，就需要更改订阅所有者，这是一项常规管理任务。|SharePoint 和本机模式|  
|**文件共享订阅的共享凭据**。 现在，两个工作流与 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 文件共享订阅共存：<br /><br /> 使用此版本中的新增功能， [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 管理员可以配置单个文件共享帐户，用于一到多个订阅。 文件共享帐户在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 本机模式配置管理器的“指定文件共享帐户”中配置，然后用户即可在订阅配置页中选择“用户文件共享帐户”。<br /><br /> 使用目标文件共享的特定凭据配置单独的订阅。<br /><br /> 你还可以混合使用这两种方法，使一些文件共享订阅使用中央文件共享帐户，而其他订阅使用特定的凭据。|本机模式|  

### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
 新版 SSDT 包括 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 的以下项目模板：报表服务器项目向导和报表服务器项目。 有关如何下载 SSDT 的信息，请参阅 [SQL Server Data Tools for Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkId=827542)（适用于 Visual Studio 2015 的 SQL Server Data Tools）。  

### <a name="report-builder-improvements"></a>报表生成器改进

**新的报表生成器用户界面：**核心[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)]用户界面现在使用简化的 UI 元素，给你一种现代化的观感。  
  
|||  
|-|-|  
|新建|Previous|  
|![ssrs_rbfacelift_new](../reporting-services/media/ssrs-rbfacelift-new.png "ssrs_rbfacelift_new")|![ssrs_rbfacelift_old](../reporting-services/media/ssrs-rbfacelift-old.png "ssrs_rbfacelift_old")|  

**自定义参数窗格：**现在可以自定义参数窗格。 利用报表生成器中的设计图面，可以将参数拖到参数窗格中的特定列和行。 你可以通过添加和删除列来更改窗格的布局。   有关详细信息，请参阅[自定义报表中的参数窗格（报表生成器）](../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)。  
  
 ![Parameter list in Report Data pane and in parameters pane](../reporting-services/media/ssrs-customizeparameter-parameterlist-reportdatapane.png "Parameter list in Report Data pane and in parameters pane")  

  
**高 DPI 支持：**用于 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 的[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)]支持高 DPI（每英寸点数）缩放功能和设备。  有关高 DPI 的详细信息，请参阅以下内容：  
  
-   [Windows 8.1 DPI 缩放增强功能](https://blogs.windows.com/windowsexperience/2013/07/15/windows-8-1-dpi-scaling-enhancements/)  
  
-   [高 DPI 和 Windows 8.1](http://technet.microsoft.com/library/dn528848.aspx)  
  
## <a name="see-also"></a>另请参阅  
 [Analysis Services 中的新增功能](http://msdn.microsoft.com/zh-cn/aa69c299-b8f4-4969-86d8-b3292fe13f08)  
 [SSRS 中的 Power BI 技术预览版报表 - 发行说明](../reporting-services/reporting-services-发行说明.md)  
 [SQL Server 2016 发行说明](../sql-server/sql-server-2016-release-notes.md)   
 [后向兼容性](http://msdn.microsoft.com/zh-cn/675b0e0e-cfee-4790-9675-80fc3ea6d30f)   
 [SQL Server 2016 各个版本支持的 Reporting Services 功能](http://msdn.microsoft.com/zh-cn/39f03d2d-6e48-4b34-a9d3-07f86313b937)   
 [升级和迁移 Reporting Services](../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 [Reporting Services (SSRS)](../reporting-services/reporting-services-ssrs.md)  
  
  