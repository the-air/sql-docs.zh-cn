---
title: "了解管理控制台警报 (Analytics Platform System)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c4aa221-55c2-44cf-9eaa-3bf7bd55e51a
caps.latest.revision: "10"
ms.openlocfilehash: 4be7ff23e9d7bca299aa1bcf45d14c2d3d7a3c49
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="understanding-admin-console-alerts"></a>了解管理控制台警报
警报显示在设备**管理控制台**并在**System Center Operations Manager** (SCOM)。 使用警报的此列表可帮助确定哪些警报需要进一步研究。  
  
有关连接到**管理控制台**通过使用 Internet Explorer，请参阅[使用管理控制台 &#40; 监视设备分析平台系统 &#41;](monitor-the-appliance-by-using-the-admin-console.md). 璝惠**SCOM**，请参阅[监视通过使用 System Center Operations Manager &#40; 设备分析平台系统 &#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
有关使用 Transact 获取警报信息信息\-SQL，请参阅[监视通过使用系统视图 &#40; 设备分析平台系统 &#41;](monitor-the-appliance-by-using-system-views.md).  
  
## <a name="types-of-alerts"></a>类型的警报  
指示正常状态的警报名称通常不需要调查。 有时包含单词重大的警报名称需要操作。 调查是必需的所有其他类型的警报。  
  
## <a name="alert-list"></a>警报列表  
通过按字母顺序列出的警报**警报名称**。 所有可能的警报不在列表中。 所使用的某些警报文字会稍有不同为不同的供应商提供。  
  
|**警报名称**|**所需的操作？**|**State**|**Severity**|**Description**|**详细信息**|  
|------------------|------------------------|-------------|----------------|-------------------|------------------------|  
|Ambari 代理具有关键状态。|是|失败|错误|此 Ambari 代理资源已失败 (状态： 4) 或处于脱机状态 (状态： 3)。 包含其他脱机状态为时脱机处于挂起状态 (状态： 130)。 状态报告组件的"hadoop_service_status"属性中。|查看头和数据节点上的群集资源。|  
|Ambari 代理具有非关键状态。|是|降级|警告|此 Ambari 代理资源是在非严重状态由于以下原因之一:-资源处于继承状态 (状态： 0) 的资源处于挂起状态 (状态： 128)-资源处于联机挂起状态 (状态： 不得超过 129) 的资源正在执行初始ization (状态： 1) 在组件的"hadoop_service_status"属性中报告状态。|查看头和数据节点上的群集资源。|  
|Ambari 代理具有正常状态。|是|操作|信息性|正常运行 Ambari 代理 (状态： 运行)。 状态报告组件的"hadoop_service_status"属性中。||  
|Ambari 代理具有未知状态。|是|降级|警告|无法确定此 Ambari 代理资源的状态 (状态:-1)。 状态报告组件的"hadoop_service_status"属性中。|查看头和数据节点上的群集资源。|  
|应用程序检测信号具有正常状态。|是|操作|信息性|成功建立与应用程序的通信。|指示组件以前报告不同的状态，但由于返回至正常。|  
|应用程序检测信号引发严重警报。|是|非操作|错误|无法与应用程序进行通信。 应用程序可能正在重新启动。|应用程序检测信号处于意外状态。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|已发生群集故障转移事件。|是|操作|错误|主群集的节点不再处于活动状态，因此被动已占用作为主节点。 查看有关详细信息的故障的节点的 Windows 事件日志并查看 HST01 VM 上的故障转移群集管理器。|发生故障转移。 所需的故障排除。 查看 HST01 VM 和节点的系统事件日志上的故障转移群集管理器。|  
|群集资源组具有关键状态。|是|失败|错误|此群集资源组已失败并可能正在尝试重新启动，或者是正在脱机 HST01 VM。|资源组状态已失败，并且需要诊断。 查看 HST01 上的故障转移群集管理器 VM。|  
|群集资源组具有非关键状态。|是|降级|警告|此群集资源组是联机，但非严重状态由于以下原因之一： 资源组处于部分联机状态或资源组处于挂起状态。|资源组不完全处于预期的状态。 所需的故障排除。 查看 HST01 上的故障转移群集管理器 VM。|  
|群集资源组具有正常状态。|是|操作|信息性|此群集资源组处于联机状态|指示组件以前报告不同的状态，但由于返回至正常。|  
|群集资源组具有未知状态。|是|降级|警告|此群集资源组处于未知状态。|系统无法检索群集资源组的运行状况状态。 所需的故障排除。 查看 HST01 上的故障转移群集管理器 VM。|  
|群集资源也有严重状态。|是|失败|错误|此群集的资源已失败并可能会尝试重新启动，或处于脱机状态。|群集资源未处于预期的状态中。 所需的故障排除。 查看 HST01 上的故障转移群集管理器 VM。|  
|群集资源也有非关键状态。|是|降级|警告|此群集的资源是在非-严重状态由于以下原因之一： 资源处于继承状态、 资源处于挂起状态、 资源处于联机挂起状态，资源处于脱机挂起状态，或资源正在执行初始化。|群集资源未处于预期的状态中。 所需的故障排除。 查看 HST01 上的故障转移群集管理器 VM。|  
|群集资源具有正常状态。|是|操作|信息性|此群集的资源处于联机状态。|指示组件以前报告不同的状态，但由于返回至正常。|  
|群集资源具有未知状态。|是|降级|警告|无法确定此群集的资源的状态。|系统无法检索群集资源的运行状况状态。 所需的故障排除。 查看 HST01 上的故障转移群集管理器 VM。|  
|群集共享卷具有关键状态。|是|失败|错误|此群集共享的卷资源已失败 (状态： 4) 或处于脱机状态 (状态： 3)。 包含其他脱机状态为时脱机处于挂起状态 (状态： 130)。 状态报告组件的"csv_state"属性中。|查看 HST01 上的故障转移群集管理器 VM。|  
|群集共享卷具有非关键状态。|是|降级|警告|此群集共享的卷资源是在非严重状态由于以下原因之一:-资源处于继承状态 (状态： 0) 的资源处于挂起状态 (状态： 128)-资源处于联机挂起状态 (状态： 不得超过 129) 的执行资源ing 初始化 (状态： 1) 在组件的"csv_state"属性中报告状态。|查看 HST01 上的故障转移群集管理器 VM。|  
|群集共享卷具有正常状态。|是|操作|信息性|此群集共享的卷资源处于联机状态 (状态： 2)。 状态报告组件的"csv_state"属性中。||  
|群集共享卷具有未知状态。|是|降级|警告|无法确定此群集共享的卷资源的状态 (状态:-1)。 状态报告组件的"csv_state"属性中。|查看 HST01 上的故障转移群集管理器 VM。|  
|群集状态正常|是|操作|信息性|群集具有正常状态。|指示组件以前报告不同的状态，但由于返回至正常。|  
|控制器有严重状态。|是|失败|错误|PERC 磁盘指示严重错误，或在控制器已关闭。|本地的 RAID 控制器严重错误，可能需要更换。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|控制器有非关键状态。|如果问题仍然存在多个 7 小时或重复多次出现同一节点上不被绑定到预期的重新启动|降级|警告|PERC 磁盘报告了非关键问题，可能与电缆工作不正常。|这通常指示电池充电 PowerEdge RAID 控制器的电池供电高速缓存模块上的周期。 这可能是在计划的测试周期 (持续时间最多约 7 小时) 或它也可能会报告后重新启动或电源周期充电电池必须时。 重要说明： 这通常还指示控制器的策略暂时从写通式写回充电完成之前将本地存储区上具有性能影响已更改 (**tempdb**)。 查看有关详细信息的节点的 Windows 事件日志。|  
|控制器有不可恢复的状态。|是|失败|错误|PERC 磁盘状态为不可恢复。|本地的 RAID 控制器未正常运行和已进入不可恢复的状态可能需要更换。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|控制器具有正常状态。|是|操作|信息性|正常运行 PERC 磁盘|指示组件以前报告不同的状态，但由于返回至正常。|  
|控制器具有未知状态。|是|降级|警告|无法确定 PERC 磁盘的状态。|系统无法检索本地 RAID 控制器的运行状况状态。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|冷却设备具有关键状态。|是|失败|警告|冷却设备已达到严重阈值上限或下限|冷却设备可能需要更换。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|冷却设备具有非关键状态。|是|降级|警告|冷却设备已达到非关键的上限或下限阈值。|冷却设备尚未达到严重级别，但超出了预期的上限或下限范围。 查看有关详细信息的节点的 Windows 事件日志。|  
|冷却设备都有不可恢复的状态。|是|失败|警告|冷却设备已达到不可恢复的上限或下限阈值。|冷却设备可能需要更换。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|冷却设备具有正常状态。|是|操作|信息性|冷却设备运行正常。|指示组件以前报告不同的状态，但由于返回至正常。|  
|冷却设备具有未知状态。|是|降级|警告|无法确定冷却设备的状态|系统无法检索冷却设备的状态。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|磁盘阵列具有关键的总体状态。|是|失败|错误|磁盘阵列总体状态是关键。|可能表示磁盘阵列不再处于活动状态由于故障的驱动器或类似的问题。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|磁盘阵列具有非关键的总体状态。|是|降级|警告|磁盘阵列总体状态指示没有非关键警告，但系统仍正常运行。|磁盘阵列仍正常运行，但这可能表示磁盘故障或类似的问题。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|磁盘阵列具有不可恢复的总体状态。|是|失败|错误|磁盘阵列是不可恢复的总体状态。|磁盘阵列不再起作用。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|磁盘阵列具有正常的总体状态。|是|操作|信息性|磁盘阵列总体状态是正常的。|指示组件以前报告不同的状态，但由于返回至正常。|  
|磁盘阵列具有未知总体状态。|是|降级|警告|总体无法确定状态的磁盘阵列。|系统无法检索本地磁盘阵列的运行状况状态。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|外部存储阵列具有关键状态。|是|失败|错误|外部存储阵列指示失败 (供应商 OperationalStatus: 6、 16) ！ 供应商状态报告组件的"storage_global_status"属性中。 值： 6 错误、 16 支持实体时出错。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|外部存储阵列具有非关键状态。|是|降级|警告|报告非关键警告，外部存储阵列 (供应商 OperationalStatus: 3,4,5,11,14,15,17)。 供应商状态报告组件的"storage_global_status"属性中。 值： 3 降级、 4 强调、 预测 5 失败，11 签入服务，14 中止、 休眠 15、 17 完成操作。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|外部存储阵列了不可恢复的状态。|是|失败|错误|外部存储阵列指示存储阵列已关闭并且不可恢复 (供应商 OperationalStatus: 7)。 供应商状态报告组件的"storage_global_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|外部存储阵列具有正常状态。|是|操作|信息性|通常使用外部存储阵列 (供应商状态: 确定)。 供应商状态报告组件的"storage_global_status"属性中。||  
|外部存储阵列具有未知状态。|是|降级|警告|外部存储阵列的状态无法确定基于供应商状态 (供应商 OperationalStatus: 0,1,18)。 供应商状态报告组件的"storage_global_status"属性中。 值： 月 0-未知日，西班牙 1 其他接口，18 电源模式。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|外部存储阵列已无法访问的状态。|是|失败|错误|外部存储阵列指示是否无法访问存储阵列 (供应商 OperationalStatus: 8,9,10,12,13)。 供应商状态报告组件的"storage_global_status"属性中。 值： 8 启动、 停止 9、 10 停止、 12-无联系人、 13 丢失的通信。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|外部存储的关键状态。|是|失败|错误|外部存储指示失败。|所需的故障排除。 查看 Windows 事件日志和存储设备的事件日志中有详细信息。|  
|外部存储具有已降级状态。|是|降级|警告|存储系统已降级。 你需要检查的温度状态或此存储系统的电源状态。  此外，如果删除了存储系统的端面板，无线流的更改可能导致不正确冷却的驱动器，并影响温度状态。  供应商状态报告组件的"storage_global_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|外部存储的非关键状态。|是如果问题仍然存在超过 7 小时或频繁重复出现在同一设备上多个每隔 90 天|降级|警告|外部存储报告非严重警告。|此事件通常表示两个问题之一： 磁盘失败/转换事件或电池充电 raid 控制器电池供电高速缓存模块上的周期。 计费周期通常计划每隔 90 天，并可能需要花费 7 小时。 重要提示： 在此期间很可能控制器的写缓存策略暂时已从直写写回这可能会影响性能。 查看 Windows 事件日志和存储设备的事件日志中有详细信息。|  
|外部存储具有正常状态。|是|操作|信息性|外部存储工作正常。|指示组件以前报告不同的状态，但由于返回至正常。|  
|外部存储具有未知状态。|是|降级|警告|无法确定外部存储的状态。|系统无法检索服务器的外部存储的运行状况状态。 所需的故障排除。 查看该节点的 Windows 事件日志和存储设备的事件日志中有详细信息。|  
|风扇设备都有严重状态。|是|失败|警告|风扇设备已达到严重阈值上限或下限 (供应商状态： CriticalUpper 或 CriticalLower)。  供应商状态报告组件的"device_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|风扇设备都有非关键状态。|是|降级|警告|风扇设备已达到非关键的上限或下限阈值 (供应商状态： nonCriticalUpper 或 nonCriticalLower)。  供应商状态报告组件的"device_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|风扇设备都有不可恢复的状态。|是|失败|警告|风扇设备已达到不可恢复的上限或下限阈值 (供应商状态： nonRecoverableUpper 或 nonRecoverableLower 失败)。 供应商状态报告组件的"device_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|风扇设备具有正常状态。|是|操作|信息性|正常运行风扇设备 (供应商状态: 确定)。 供应商状态报告组件的"device_status"属性中。||  
|风扇设备具有未知状态。|是|降级|警告|无法确定风扇设备的状态 (供应商状态： 其他或未知)。 供应商状态报告组件的"device_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|光纤通道主控制器具有关键状态。|是|失败|警告|光纤通道主机控制器组件检测到下列条件之一:-主机控制器发生故障，且应替换为 (供应商状态： 失败) 的主机控制器已被关闭 (供应商状态： 关闭) 的光纤通道连接是失败的 （供应商状态： loopFailed) 供应商状态报告组件的"FC_device_rollup_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。  用户执行任何操作： 如果控制器状态为已失败，更换的控制器。|  
|光纤通道主控制器具有非关键状态。|是|降级|警告|光纤通道主机控制器报告以下条件之一:-光纤通道连接已降级 (供应商状态： loopDegraded)-光纤通道端口未连接或连接到该设备关闭 (供应商状态：组件的"FC_device_rollup_status"属性中会报告 notConnected) 供应商状态。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|光纤通道主控制器具有正常状态。|是|操作|信息性|光纤通道主机控制器是否运行正常 (供应商状态: 确定)。 供应商状态报告组件的"FC_device_rollup_status"属性中。||  
|光纤通道主机控制器具有未知状态。|是|降级|警告|无法确定光纤通道主机控制器状态或者控制器不存在 (供应商状态： 其他)。 供应商状态报告组件的"FC_device_rollup_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|Hadoop 服务都有严重状态。|是|非操作|错误|此服务将处于严重状态和已停止工作 (状态： 安装或已停止) 或正处于过渡状态要停止 (状态： 正在停止)。 状态报告组件的"hadoop_service_status"属性中。|查看详细信息的节点的 Windows 和 PDW 组件事件日志。|  
|Hadoop 服务都有非关键状态。|是|降级|警告|此服务将处于非严重状态由于以下原因之一:-服务正在启动 (状态： 正在启动) 的升级服务 (状态： 升级) 状态报告组件的"hadoop_service_status"属性中。|查看详细信息的节点的 Windows 和 PDW 组件事件日志。|  
|Hadoop 服务具有未知状态。|是|降级|警告|此服务报告它处于未知状态。 状态报告组件的"hadoop_service_status"属性中。|查看该节点的 Hadoop 日志，以及详细信息的 Windows 和 PDW 组件的事件日志。|  
|内存的设备有严重状态。|是|失败|警告|内存报告的严重问题。|DIMM 可能需要更换。 所需的故障排除。 服务器可能仍为活动状态，具有一些失败的 RAM，但性能可能会受到影响。 查看有关详细信息的节点的 Windows 事件日志。|  
|内存的设备有非关键状态。|是|降级|警告|内存报告非严重的问题。|无法将指向即将引发 DIMM 失败。 通常，这意味着 DIMM 已发现错误，但它未包含超过了阈值，以使其关键/失败状态。 服务器可能仍为活动状态，具有一些失败的 ram，但性能可能会受到影响。 若要清除该错误，必须清除硬件日志。 查看有关详细信息的节点的 Windows 事件日志。|  
|内存的设备有不可恢复的状态。|是|失败|警告|内存报告了不可恢复的问题。|DIMM 可能需要更换。 所需的故障排除。 服务器可能仍为活动状态，具有一些失败的 ram，但性能可能会受到影响。 查看有关详细信息的节点的 Windows 事件日志|  
|内存设备具有正常状态。|是|操作|信息性|内存正常|指示组件以前报告不同的状态，但由于返回至正常。|  
|内存设备具有未知状态。|是|降级|警告|无法确定状态的内存。|系统无法检索系统内存的运行状况状态。 DIMM 可能需要更换。 所需的故障排除。 服务器可能仍为活动状态，具有一些失败的 RAM，但性能可能会受到影响。 查看有关详细信息的节点的 Windows 事件日志|  
|网络适配器都具有关键状态。|是|降级|警告|网络适配器引发严重警报由于以下原因之一： 适配器处于脱机状态、 电源已关闭，适配器或适配器处于关闭税状态|网络适配器处于失败状态，并且可能需要更换 （这可能意味着主板替换）。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|网络适配器都具有非关键状态。|是|降级|警告|网络适配器指示没有非关键警告，但较仍正常运行，但可能会降低性能。|网络适配器具有某些错误，但不是处于严重状态。 因为这可能影响性能故障排除是必需的。 查看有关详细信息的节点的 Windows 事件日志。|  
|网络适配器有不可恢复的状态。|是|失败|警告|网络适配器就处于由于可能安装在错误不可恢复状态。|网络适配器处于失败状态，并且可能需要更换 （这可能意味着主板替换）。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|网络适配器都具有正常状态。|是|操作|信息性|网络适配器已联机并且正在运行正常。|指示组件以前报告不同的状态，但由于返回至正常。|  
|网络适配器具有未知状态。|是|降级|警告|无法确定网络适配器的状态。 此状态可能由于以下原因之一造成:-网络适配器处于节电模式： 尚未安装备用、 低的电源，警告，未知，或重启，网络适配器，网络适配器设备报告未知的状态，网络适配器可能正在测试状态。|系统无法检索网络适配器的运行状况状态。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|网络连接有严重状态。|是|降级|警告|网络连接引发严重警报由于以下原因之一： 网络断开连接、 硬件不存在、 已禁用硬件、 媒体已断开连接，-身份验证失败，已使用无效的地址，凭据必需的但不是提供|网络适配器将处于严重状态。 查看有关详细信息的节点的 Windows 事件日志。|  
|网络连接有非关键状态。|是|降级|警告|网络报告非严重的状态。 此状态可能是由于以下原因之一： 网络处于连接状态、 网络正在断开连接状态、 正在进行中的网络身份验证。|网络适配器处于意外状态。 如果此问题仍然存在，或出现多次，则需故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|网络连接具有正常状态。|是|操作|信息性|连接了网络并且能正常工作。|指示组件以前报告不同的状态，但由于返回至正常。|  
|网络连接配置文件是预期的配置文件上。|是|操作|信息性|网络连接和使用方式预期的配置文件。 配置文件中组件的"profile_category"属性当前日期为止。 域配置文件是 2，专用配置文件是 1。|有关详细信息中查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件。  镜像数据库的运行状况可能受到的单个磁盘丢失，因此其他警报可能引起的磁盘本身。|  
|网络连接配置文件显示在公共配置文件。|是|降级|警告|网络正在报告其为公共配置文件上。 配置文件中组件的"profile_category"属性当前日期为止。 公共配置文件被报告为 0。  这可能会导致此节点的通信问题。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|在群集中的节点都有严重状态。|是|失败|错误|群集的节点处于关闭状态。|群集中的服务器已关闭。 查看 HST01 上的故障转移群集管理器 VM。|  
|在群集中的节点都有非关键状态。|是|降级|警告|群集的节点引发非严重警报。 可能发生下列情况之一： 节点处于暂停状态或节点正在加入群集。|节点处于意外状态。 所需的故障排除。 查看 HST01 上的故障转移群集管理器 VM。|  
|在群集中的节点具有正常状态。|是|操作|信息性|群集的节点已启动并正在运行|指示组件以前报告不同的状态，但由于返回至正常。|  
|在群集中的节点具有未知状态。|是|降级|警告|群集的节点处于未知状态。|系统无法检索节点的运行状况状态。 所需的故障排除。 查看 HST01 上的故障转移群集管理器 VM。|  
|物理磁盘的关键状态。|是|失败|错误|磁盘状态至关重要 (供应商状态： 2 不正常) ！ 组件的"phys_disk_status"属性中报告的状态。  显示属性"phys_disk_oper_status"中的操作状态可能提供有关的问题的详细信息。 操作状态的值： 0 的物理磁盘的操作状态是未知的。 确定 2 3 降级 4 强调 5 预测失败 6 错误 7-不可恢复的错误 8 启动 9 停止停止 10 11-在服务 12-无联系人 13 丢失通信 15 休眠 18 电源模式下 0x8004 失败介质 0x8005 拆分 0x8006 过时元数据0x8007 IO 错误 0x8008 损坏元数据。||  
|物理磁盘的非关键状态。|是|降级|警告|磁盘状态指示没有非关键警告，但系统仍正常运行。 组件的"phys_disk_status"属性中报告的状态。  显示属性"phys_disk_oper_status"中的操作状态可能提供有关的问题的详细信息。 操作状态的值： 0 的物理磁盘的操作状态是未知的。 确定 2 3 降级 4 强调 5 预测失败 6 错误 7-不可恢复的错误 8 启动 9 停止停止 10 11-在服务 12-无联系人 13 丢失通信 15 休眠 18 电源模式下 0x8004 失败介质 0x8005 拆分 0x8006 过时元数据0x8007 IO 错误 0x8008 损坏元数据。|有关详细信息中查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件。  镜像数据库的运行状况可能受到的单个磁盘丢失，因此其他警报可能引起的磁盘本身。|  
|物理磁盘具有正常状态。|是|操作|信息性|磁盘状态为正常。 组件的"phys_disk_status"属性中报告的状态。||  
|物理磁盘具有未知状态。|是|降级|警告|无法确定磁盘状态 (状态： 5-未知)。 组件的"phys_disk_status"属性中报告的状态。  显示属性"phys_disk_oper_status"中的操作状态可能提供有关的问题的详细信息。 操作状态的值： 0 的物理磁盘的操作状态是未知的。 确定 2 3 降级 4 强调 5 预测失败 6 错误 7-不可恢复的错误 8 启动 9 停止停止 10 11-在服务 12-无联系人 13 丢失通信 15 休眠 18 电源模式下 0x8004 失败介质 0x8005 拆分 0x8006 过时元数据0x8007 IO 错误 0x8008 损坏元数据。|有关详细信息中查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件。|  
|电源具有关键状态。|是|失败|警告|电源指示存在一个严重错误。|电源可能需要更换。 所需的故障排除。 电源是冗余的因此服务器可能仍处于活动状态。 查看有关详细信息的节点的 Windows 事件日志。|  
|电源具有非关键状态。|是|操作|警告|电源报告了非关键问题。|电源已报告了一个问题，但并不处于失败状态。 这可能表示即将出现故障。 电源是冗余的因此故障可能不会创建服务器停机。 硬件错误可能需要清除要清除管理员控制台错误。 查看有关详细信息的节点的 Windows 事件日志。|  
|电源有不可恢复的状态。|是|失败|警告|电源处于不可恢复的状态。|电源可能需要更换。 所需的故障排除。 电源是冗余的因此服务器可能仍处于活动状态。 查看有关详细信息的节点的 Windows 事件日志。|  
|电源具有正常状态。|是|操作|信息性|电源运行正常。|指示组件以前报告不同的状态，但由于返回至正常。|  
|电源设备具有未知状态。|是|降级|警告|无法确定电源的状态。|系统无法检索电源的运行状况状态。 电源是冗余的因此服务器可能仍处于活动状态。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|处理器设备都有严重状态。|是|失败|警告|CPU 报告的严重问题。|CPU 可能需要更换。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|处理器设备都有非关键状态。|是|降级|警告|CPU 报告非严重的问题。|CPU 遇到错误，但尚未处于失败状态。 这可能表示即将引发失败。 查看有关详细信息的节点的 Windows 事件日志。|  
|处理器设备都有不可恢复的状态。|是|失败|警告|CPU 报告了不可恢复的问题。|类似于关键状态。 CPU 可能需要更换。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|处理器设备具有正常状态。|是|操作|信息性|CPU 工作正常。|指示组件以前报告不同的状态，但由于返回至正常。|  
|处理器设备具有未知状态。|是|降级|警告|无法确定 CPU 的状态。|系统无法检索的 cpu 的运行状况状态，则需要进一步调查。 查看有关详细信息的节点的 Windows 事件日志。|  
|SAS 主机总线适配器具有已降级条件。|是|降级|警告|已降级 HBA 的总体条件和由它控制的物理驱动器的所有报告 SAS 主机总线适配器 (供应商状态： 降级)。 供应商状态报告组件的"hba_device_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|SAS 主机总线适配器具有失败条件。|是|失败|警告|SAS 主机总线适配器正在报告 HBA 的总体条件为处于失败状态，包括所有由它控制的物理驱动器。 这将需要要替换的组件 (供应商状态： 失败)。 供应商状态报告组件的"hba_device_rollup_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|SAS 主机总线适配器具有正常状态。|是|操作|信息性|正常运行 SAS 主机总线适配器 (供应商状态: 确定)。 供应商状态报告组件的"hba_device_rollup_status"属性中。||  
|SAS 主机总线适配器具有未知状态。|是|降级|警告|无法确定 SAS 主机总线适配器状态 (供应商状态： 其他)。 供应商状态报告组件的"hba_device_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|SQL Server 具有关键状态。|是|保持非运行状态|错误|此服务将处于严重状态和已停止工作 (状态： 已停止) 或正处于过渡状态要停止 (状态： StopPending)。  状态报告组件的"sql_server_service_status"属性中。|查看有关详细信息的节点的 Windows 事件日志。|  
|SQL Server 具有正常状态。|是|操作|信息性|此服务未正常运行 (状态： 运行)。 状态报告组件的"sql_server_service_status"属性中。||  
|存储机箱风扇具有已降级状态。|是|降级|警告|存储机箱风扇报告它已降级 (供应商状态： 10，15)。 供应商状态报告组件的"storage_fan_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|存储机箱风扇已失败状态。|是|失败|警告|存储机箱风扇不报告它处于失败状态。 这将需要要替换的组件 (供应商状态： 20,25)。 供应商状态报告组件的"storage_fan_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|存储机箱风扇都有不可恢复的状态。|是|失败|警告|此风扇处于不可恢复状态报告存储机箱风扇。 这将需要要替换的组件 (供应商状态： 30)。 供应商状态报告组件的"storage_fan_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|存储机箱风扇具有未知状态。|是|降级|错误|无法确定存储机箱风扇状态 (供应商状态： 0-未知)。 供应商状态报告组件的"storage_fan_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|存储机箱风扇具有正常状态。|是|操作|信息性|存储机箱风扇是否正常运行 (供应商状态： 5)。 供应商状态报告组件的"storage_fan_status"属性中。||  
|存储机箱电源具有已降级状态。|是|降级|警告|存储机箱电源设备不报告了此电源已降级 (供应商状态： 10，15)。 供应商状态报告组件的"storage_power_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|存储机箱电源已失败状态。|是|失败|错误|存储机箱电源设备不报告了此电源处于失败状态。 这将需要一个组件来替换或还原到设备的电源 (供应商状态： 20,25)。 供应商状态报告组件的"storage_power_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|存储机箱电源出现不可恢复的状态。|是|失败|错误|此电源处于不可恢复状态报告存储机箱电源。 这将需要要替换的组件 (供应商状态： 30)。 供应商状态报告组件的"storage_power_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|存储机箱电源设备具有未知的状态。|是|降级|警告|无法确定存储机箱电源状态 (供应商状态： 0)。 供应商状态报告组件的"storage_power_status"属性中。|查看详细信息或联系设备制造商的节点的 Windows 事件日志。|  
|存储机箱电源具有正常状态。|是|操作|信息性|存储机箱电源设备是否正常运行 (供应商状态： 5)。 供应商状态报告组件的"storage_power_status"属性中。||  
|存储池没有关键状态。|是|失败||存储池状态至关重要 (供应商状态： 2 不正常) ！ 组件的"storage_pool_status"属性中报告的状态。  显示属性"storage_pool_oper_status"中的操作状态可能提供有关的问题的详细信息。|有关详细信息中查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件。  镜像数据库的运行状况可能受到的单个磁盘丢失，因此其他警报可能引起的磁盘本身。|  
|存储池没有非关键状态。|是|降级||存储池状态指示没有非关键警告，但系统仍正常运行 (状态： 1-警告)。 组件的"storage_pool_status"属性中报告的状态。  显示属性"storage_pool_oper_status"中的操作状态可能提供有关的问题的详细信息。|查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件以了解详细信息...  镜像数据库的运行状况可能受到的单个磁盘丢失，因此其他警报可能引起的磁盘本身。|  
|存储池没有正常的状态。|是|操作||存储池状态是正常 (状态： 0 正常)。 组件的"storage_pool_status"属性中报告的状态。||  
|存储池具有未知状态。|可选|操作||处于未知状态在此节点上的存储池状态 (状态： 5-未知)。 组件的"storage_pool_status"属性中报告的状态。  显示属性"storage_pool_oper_status"中的操作状态可能提供有关的问题的详细信息。  这通常发生在查询存储池状态的节点不是存储池的所有者。|有关详细信息中查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件。|  
|温度状态为严重。|是|失败|错误|温度已达到严重的上限或下限阈值。|过高或过低得的温度。 继续在此状态可能损坏或极大地缩短使用寿命的硬件。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|温度状态是非关键的。|可选|降级|警告|温度已达到非关键的上限或下限阈值|在更高级别上是报告服务器的温度或低于正常，但是未达到关键状态的阈值。 在阈值之外的温度缩短硬件寿命。 可能会影响温度的事项为工作负荷，数据中心温度/气流，布线限制服务器排气，等等。查看有关详细信息的节点的 Windows 事件日志。|  
|温度状态为不可恢复。|是|失败|警告|温度就处于不可恢复的状态。|温度传感器检测到无法恢复的错误。 这可能是温度或温度模块本身有问题。 查看有关详细信息的节点的 Windows 事件日志。|  
|温度状态是正常的。|是|操作|信息性|温度是正常|指示组件以前报告不同的状态，但由于返回至正常。|  
|温度状态为未知。|是|降级|警告|无法确定温度的状态。|系统无法检索服务器温度。 所需的故障排除。 查看有关详细信息的节点的 Windows 事件日志。|  
|虚拟磁盘具有的关键状态。|是|失败|错误|存储空间虚拟磁盘的状态是关键 (供应商状态： 2 不正常) ！ 组件的"virtual_disk_status"属性中报告的状态。  显示属性"virtual_disk_oper_status"中的操作状态可能提供有关的问题的详细信息。|有关详细信息中查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件。  镜像数据库的运行状况可能受到的单个磁盘丢失，因此其他警报可能引起的磁盘本身。|  
|虚拟磁盘的非关键状态。|是|降级|警告|存储空间虚拟磁盘状态指示没有非关键警告，但系统仍正常运行 (状态： 1-警告)。 组件的"virtual_disk_status"属性中报告的状态。  显示属性"virtual_disk_oper_status"中的操作状态可能提供有关的问题的详细信息。  如果虚拟磁盘已移动到另一个节点，然后查看共享卷组件和将磁盘移回到预期的所有者，指示群集的状态数后在名称 N 例如。 N01D01 所属 HSA01 上。|有关详细信息中查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件。  镜像数据库的运行状况可能受到的单个磁盘丢失，因此其他警报可能引起的磁盘本身。|  
|虚拟磁盘具有正常状态。|是|操作|信息性|存储空间虚拟磁盘的状态是正常 (状态： 0 正常)。 组件的"virtual_disk_status"属性中报告的状态。||  
|虚拟磁盘具有未知状态。|是|操作|警告|无法确定存储空间虚拟磁盘状态 (状态： 5-未知)。 组件的"virtual_disk_status"属性中报告的状态。  显示属性"virtual_disk_oper_status"中的操作状态可能提供有关的问题的详细信息。  如果虚拟磁盘已移动到另一个节点，然后查看共享卷组件和将磁盘移回到预期的所有者，指示群集的状态数后在名称 N 例如。 N01D01 所属 HSA01 上。|有关详细信息中查看日志应用程序和服务 logs\Microsoft\Windows\StorageSpaces Driver\Operational 中的节点的事件。|  
|卷可用空间状态为严重。|是|降级|错误|卷可用空间严重不足 ！ 当前使用的卷的磁盘空间超出了总容量的 90%。 清理以确保正常的设备操作的不必要的文件/数据。|管理控制台报表分配的空间并不一定已用空间。 DBCC PDW_SHOWSPACEUSED 可用于调查使用与分配的空间。 你还可以使用 DBCC SHRINKLOG < ！-缺失的链接[DBCC SHRINKLOG &#40;SQL Server PDW &#41;](../t-sql/statements/alter-database-parallel-data-warehouse.md)收缩数据库。|  
|卷可用空间状态为非关键。|可选|操作|警告|当前使用的卷的磁盘空间是 70%和 90%之间。 查看此卷上使用的磁盘空间并清理以确保正常的设备操作的不必要的文件/数据。|管理控制台报表分配的空间并不一定已用空间。 你可以使用[DBCC PDW_SHOWSPACEUSED](../t-sql/statements/alter-database-parallel-data-warehouse.md)以调查与使用已分配空间。 你还可以使用 DBCC SHRINKLOG < ！-缺失的链接[DBCC SHRINKLOG &#40;SQL Server PDW &#41;](../t-sql/statements/alter-database-parallel-data-warehouse.md)收缩数据库。|  
|卷可用空间状态为正常。|是|操作|信息性|此卷上没有足够的可用磁盘空间。 当前使用的卷的磁盘空间低于 70%。|指示组件以前报告不同的状态，但由于返回至正常。|  
  
<!-- MISSING LINKS ## See Also  
[Error Messages &#40;SQL Server PDW&#41;](../sqlpdw/error-messages-sql-server-pdw.md)  -->
  