---
title: "自动初始化 AlwaysOn 可用性组 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67c6a601-677a-402b-b3d1-8c65494e9e96
caps.latest.revision: 18
ms.author: "v-saume"
manager: "jhubbard"
---
# 自动初始化 Always On 可用性组
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


 SQL Server 2016 推出了可用性组的自动种子设定。 创建具有自动种子设定的可用性组时，SQL Server 将自动为该组中每个数据库创建次要副本。 使用自动种子设定，你不再需要手动备份和还原次要副本。 若要启用自动种子设定，请使用 T-SQL 创建可用性组。
 
## 先决条件

自动种子设定要求数据和日志文件路径在参与可用性组的每个 SQL Server 实例上均相同。 

可用性组种子设定通过数据库镜像端点进行通信。 打开每台服务器上镜像终结点端口的入站防火墙规则。

可用性组中的数据库必须处于完整恢复模式。 数据库需要具有最新的完整备份和事务日志备份。 这些备份文件不用于自动种子设定，但需要这些文件才可将数据库包含到可用性组中。 
 
## 创建具有自动种子设定的可用性组

若要创建具有自动种子设定的可用性组，请设置 `SEEDING_MODE=AUTOMATIC`。 

下面的示例将在两个节点的 Windows Server 故障转移群集上创建一个可用性组。 运行脚本前，请先更新环境的值。

1. 创建终结点。 每个服务器需要一个终结点。 以下脚本创建将 TCP 端口 5022 用于侦听器的终结点。 设置 `<endpoint_name>` 和 `LISTENER_PORT` 以匹配你的环境并运行脚本：

    ```
    --Create the endpoint on both servers
    -- Run this script twice, once on each server. 
    CREATE ENDPOINT [<endpoint_name>] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)
    FOR DATA_MIRRORING (ROLE = ALL, AUTHENTICATION = WINDOWS NEGOTIATE, ENCRYPTION = REQUIRED ALGORITHM AES)
    GO
    ```

1. 创建可用性组。 下面的脚本将创建可用性组。 更新组名称、服务器名称和域名的值并在 SQL Server 的主实例上运行它。  

    ```
    ---Run On Primary
    CREATE AVAILABILITY GROUP [<availability_group_name>]
    FOR DATABASE db1
    REPLICA ON'<*primary_server*>'
    WITH (ENDPOINT_URL = N'TCP://<primary_server>.<fully_qualified_domain_name>:5022', 
    FAILOVER_MODE = AUTOMATIC, 
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
    BACKUP_PRIORITY = 50, 
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO), 
    SEEDING_MODE = AUTOMATIC),
    N'<secondary_server>' WITH (ENDPOINT_URL = N'TCP://<secondary_server>.<fully_qualified_domain_name>:5022', 
    FAILOVER_MODE = AUTOMATIC, 
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
    BACKUP_PRIORITY = 50, 
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO), 
    SEEDING_MODE = AUTOMATIC);
    GO
    ``` 

1. 将辅助服务器联接到可用性组，并向可用性组授予创建数据库的权限。 在 SQL Server 辅助实例上运行以下脚本： 
 
    ```
    --Run on Secondary Replica to join to the availability group
    ALTER AVAILABILITY GROUP [<availability_group_name>] JOIN
    GO  
    ALTER AVAILABILITY GROUP [<availability_group_name>] GRANT CREATE ANY DATABASE
    GO
    ```

SQL Server 将在辅助服务器上自动创建数据库副本。 如果数据库较大，则可能需要一些时间才能完成数据库同步。 如果数据库在为自动种子设定配置的可用性组中，你可以查询 `sys.dm_hadr_automatic_seeding` 系统视图来监视种子设定进度。 对于处于为自动种子设定配置的可用性组中的每个数据库，以下查询都返回一行。

```
 SELECT start_time,
       ag.name,
       db.database_name,
       current_state,
       performed_seeding,
       failure_state,
       failure_state_desc
 FROM sys.dm_hadr_automatic_seeding autos 
    JOIN sys.availability_databases_cluster db ON autos.ag_db_id = db.group_database_id
    JOIN sys.availability_groups ag ON autos.ag_id = ag.group_id
```

## 阻止可用性组后的自动种子设定

若要暂时阻止主副本将更多的数据库种子设定到次要副本，你可拒绝可用性组创建数据库的权限。 若要拒绝可用性组创建副本数据库的权限，请在托管次要副本的实例上运行以下查询。

```
ALTER AVAILABILITY GROUP [<availability_group_name>] DENY CREATE ANY DATABASE
GO
```


## 在现有可用性组上启用自动种子设定

你可在现有数据库中设置自动种子设定。 下面的命令将更改一个要使用自动种子设定的可用性组。 

```
ALTER AVAILABILITY GROUP [<availability_group_name>] 
MODIFY REPLICA ON '<primary_node>' WITH (SEEDING_MODE = AUTOMATIC)
GO
```

这将强制数据库在必要时重启种子设定。 例如，如果种子设定因次要副本磁盘空间不足而失败，你可在添加可用空间后运行 `ALTER AVAILABILITY GROUP ... WITH (SEEDING_MODE=AUTOMATIC)` 来重启种子设定。

## 停止自动种子设定

若要停止可用性组的自动种子设定，请在托管主要副本的实例上运行以下脚本：

```
ALTER AVAILABILITY GROUP [<availability_group_name>] 
    MODIFY REPLICA ON '<primary_node>'   
    WITH (SEEDING_MODE = MANUAL)
GO
```

这将取消当前正在进行种子设定的任何副本，并阻止 SQL Server 自动初始化此可用性组中的任何副本。 这不会停止任何已初始化的副本的同步。 


## 监视可用性组的自动种子设定

### 使用系统动态管理视图监视种子设定

以下系统视图显示 SQL Server 自动种子设定的状态。

**sys.dm_hadr_automatic_seeding** 

在主要副本上，查询 `sys.dm_hadr_automatic_seeding` 以检查自动种子设定过程的状态。 对于每个种子设定过程，该视图都将返回一行。 例如：

``` 
SELECT start_time, 
        completion_time
        is_source,
        current_state,
        failure_state,
        failure_state_desc
FROM sys.dm_hadr_automatic_seeding
```
 
**sys.dm_hadr_physical_seeding_stats** 

在主要副本上，查询 `sys.dm_hadr_physical_seeding_stats` DMV 以查看当前运行的每个种子设定过程的物理统计信息。 种子设定正在运行时，以下查询将返回多行：

```
SELECT * FROM sys.dm_hadr_physical_seeding_stats;
```

### 在错误日志中使用自动种子设定来诊断数据库初始化

将数据库添加到为自动种子设定配置的可用性组时，SQL Server 将通过可用性组终结点执行 VDI 备份。 完成备份并同步次要副本后查看 SQL Server 错误日志了解相关信息。

### 使用扩展事件诊断数据库级别运行状况

自动种子设定具有新的扩展事件，用于在初始化过程中跟踪状态更改、故障和性能统计信息。 

例如，此脚本会创建用于捕获自动种子设定相关事件的扩展事件会话： 

```
CREATE EVENT SESSION [AlwaysOn_autoseed] ON SERVER 
    ADD EVENT sqlserver.hadr_automatic_seeding_state_transition,
    ADD EVENT sqlserver.hadr_automatic_seeding_timeout,
    ADD EVENT sqlserver.hadr_db_manager_seeding_request_msg,
    ADD EVENT sqlserver.hadr_physical_seeding_backup_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_failure,
    ADD EVENT sqlserver.hadr_physical_seeding_forwarder_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_forwarder_target_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_progress,
    ADD EVENT sqlserver.hadr_physical_seeding_restore_state_change,
    ADD EVENT sqlserver.hadr_physical_seeding_submit_callback
    ADD TARGET package0.event_file(SET filename=N’autoseed.xel’,max_file_size=(5),max_rollover_files=(4))
WITH (MAX_MEMORY=4096 KB,EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,MAX_DISPATCH_LATENCY=30 SECONDS,MAX_EVENT_SIZE=0 KB,MEMORY_PARTITION_MODE=NONE,TRACK_CAUSALITY=OFF,STARTUP_STATE=ON)
GO 

ALTER EVENT SESSION AlwaysOn_autoseed ON SERVER STATE=START
GO 
```


下表列出了与自动种子设定相关的扩展事件： 

| 名称 | 说明|
|------------ |---------------| 
|hadr_db_manager_seeding_request_msg |  种子设定请求消息。
|hadr_physical_seeding_backup_state_change |    物理种子设定备份端状态更改。
|hadr_physical_seeding_restore_state_change |物理种子设定还原端状态更改。
|hadr_physical_seeding_forwarder_state_change | 物理种子设定转发器端状态更改。
|hadr_physical_seeding_forwarder_target_state_change |  物理种子设定转发器目标端状态更改。
|hadr_physical_seeding_submit_callback  |物理种子设定提交回调事件。
|hadr_physical_seeding_failure  |物理种子设定失败事件。
|hadr_physical_seeding_progress |   物理种子设定进度事件。
|hadr_physical_seeding_schedule_long_task_failure   |物理种子设定计划长任务失败事件。
|hadr_automatic_seeding_start   |在提交自动种子设定操作时发生。
|hadr_automatic_seeding_state_transition    |在自动种子设定操作更改状态时发生。
|hadr_automatic_seeding_success |在自动种子设定操作成功时发生。
|hadr_automatic_seeding_failure |在自动种子设定操作失败时发生。
|hadr_automatic_seeding_timeout |在自动种子设定操作超时时发生。

### 其他故障排除注意事项

**监视将完成自动种子设定的时间**

对当前正在运行的自动种子设定过程查询 `sys.dm_hadr_physical_seeding_stats`。 对于每个数据库，该视图都将返回一行。 例如：

```
SELECT local_database_name, 
       role_desc, 
       internal_state_desc, 
       transfer_rate_bytes_per_second, 
       transferred_size_bytes, 
       database_size_bytes, 
       start_time_utc, 
       end_time_utc, estimate_time_complete_utc, 
       total_disk_io_wait_time_ms, 
       total_network_wait_time_ms, 
       is_compression_enabled 
FROM sys.dm_hadr_physical_seeding_stats
```

**解决导致数据库无法出现在为自动种子设定配置的可用性组中的问题**


如果数据库未能作为启用了自动种子设定的可用性组的一部分出现，那么自动种子设定可能失败。 这可防止在主要副本和次要副本上将数据库添加到可用性组中。 对主要副本和次要副本查询 `sys.dm_hadr_automatic_seeding`。 例如，运行以下查询以确定自动种子设定的失败状态。

```
SELECT start_time, 
       completion_time, 
       is_source, 
       current_state, 
       failure_state, 
       failure_state_desc, 
       error_code 
FROM sys.dm_hadr_automatic_seeding
```

## 自动种子设定和性能注意事项

SQL Server 使用固定数目的线程进行自动种子设定。 在主实例中，SQL Server 对每个 LUN 使用一个线程来读取更改。 在辅助实例中，SQL Server 对每个 LUN 使用一个线程来初始化数据库。

在次要副本上设置跟踪标志 9567，以在自动种子设定过程中启用数据流压缩。 这可以显著减少自动种子设定的传输时间，但也会增大 CPU 使用率。 有关详细信息，请参阅 [Tune compression for availability group](../../../database-engine/availability-groups/windows/tune-compression-for-availability-group.md)（调整可用性组的压缩）。 


## 何时不使用自动种子设定

在某些情况下，自动种子设定可能不是初始化次要副本的最优选择。 自动种子设定过程中，SQL Server 通过网络执行备份以进行初始化。 如果数据库非常大或者次要副本是远程副本，此过程会很缓慢。 在备份过程中，无法截断这些数据库的事务日志，因此，如果繁忙的数据库初始化过程耗时冗长，则可能导致事务日志大幅增加。
在将数据库添加到具有自动种子设定的可用性组之前，请先评估数据库大小、负载和副本之间的站点距离。

## Resources

[CREATE AVAILABILITY GROUP (Transact-SQL)
-](https://msdn.microsoft.com/library/ff878399.aspx)

[AlwaysOn 可用性组故障排除和监视指南](http://technet.microsoft.com/library/dn135328.aspx)
