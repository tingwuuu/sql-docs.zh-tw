---
title: "變更資源集區 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_RESOURCE_POOL_TSQL
- ALTER RESOURCE POOL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER RESOURCE POOL
ms.assetid: 9c1c4cfb-0e3b-4f01-bf57-3fce94c7d1d4
caps.latest.revision: 47
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 662686f08e370f3d3ee4dee3211f28df58e3b171
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="alter-resource-pool-transact-sql"></a>ALTER RESOURCE POOL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  變更 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中現有的資源管理員資源集區組態。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [TRANSACT-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>語法  
  
```  
ALTER RESOURCE POOL { pool_name | "default" }  
[WITH  
    ( [ MIN_CPU_PERCENT = value ]  
    [ [ , ] MAX_CPU_PERCENT = value ]   
    [ [ , ] CAP_CPU_PERCENT = value ]   
    [ [ , ] AFFINITY {
                        SCHEDULER = AUTO 
                      | ( <scheduler_range_spec> ) 
                      | NUMANODE = ( <NUMA_node_range_spec> )
                      }]   
    [ [ , ] MIN_MEMORY_PERCENT = value ]  
    [ [ , ] MAX_MEMORY_PERCENT = value ]   
    [ [ , ] MIN_IOPS_PER_VOLUME = value ]  
    [ [ , ] MAX_IOPS_PER_VOLUME = value ]  
)]   
[;]  
  
<scheduler_range_spec> ::=  
{SCHED_ID | SCHED_ID TO SCHED_ID}[,…n]  
  
<NUMA_node_range_spec> ::=  
{NUMA_node_ID | NUMA_node_ID TO NUMA_node_ID}[,…n]  
```  
  
## <a name="arguments"></a>引數  
 { *pool_name* | **「 預設 」** }  
 現有使用者定義之資源集區的名稱，或是安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時建立之預設資源集區的名稱。  
  
 搭配 ALTER RESOURCE POOL 使用時，"default" 必須加上引號 ("") 或方括號 ([]) 才能避免與系統保留字 DEFAULT 產生衝突。 如需詳細資訊，請參閱＜ [Database Identifiers](../../relational-databases/databases/database-identifiers.md)＞。  
  
> [!NOTE]  
>  預先定義的工作負載群組和資源集區都會使用小寫名稱，例如 "default"。 如果是使用區分大小寫之定序的伺服器，則應該將此列入考量。 具有不區分大小寫之定序 (如 SQL_Latin1_General_CP1_CI_AS) 的伺服器會將 "default" 和 "Default" 視為相同。  
  
 MIN_CPU_PERCENT =*值*  
 當 CPU 出現競爭時，為在資源集區中的所有要求，指定保證平均 CPU 頻寬。 *值*是預設值為 0 的整數。 允許的範圍*值*是從 0 到 100。  
  
 MAX_CPU_PERCENT =*值*  
 當出現 CPU 競爭時，指定所有要求在資源集區中將會接收的最大平均 CPU 頻寬。 *值*是預設值為 100 的整數。 允許的範圍*值*是從 1 到 100 之間。  
  
 CAP_CPU_PERCENT =*值*  
 **適用於**： [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 資源集區中指定的目標最大 CPU 容量的要求。 *值*是預設值為 100 的整數。 允許的範圍*值*是從 1 到 100 之間。  
  
> [!NOTE]  
>  由於統計 CPU 控管，您可能會注意到偶發的尖峰超過 CAP_CPU_PERCENT 中指定的值。  
  
 AFFINITY {SCHEDULER = AUTO | (Scheduler_range_spec) | NUMANODE = (NUMA_node_range_spec)}  
 **適用於**： [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 將資源集區附加至特定排程器。 預設值是 AUTO。  
  
 AFFINITY SCHEDULER = (Scheduler_range_spec) 會將資源集區對應至給定識別碼所識別的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排程。 這些識別碼對應至 scheduler_id 資料行中值[sys.dm_os_schedulers &#40;TRANSACT-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).  
  
 當您使用 AFFINITY NAMANODE = (NUMA_node_range_spec) 時，資源集區會與對應至對應給定 NUMA 節點或節點範圍之實體 CPU 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排程器相似化。 您可以使用下列 Transact-SQL 查詢探索實體 NUMA 組態與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 排程器識別碼之間的對應。  
  
```  
SELECT osn.memory_node_id AS [numa_node_id], sc.cpu_id, sc.scheduler_id  
FROM sys.dm_os_nodes AS osn  
INNER JOIN sys.dm_os_schedulers AS sc 
   ON osn.node_id = sc.parent_node_id 
      AND sc.scheduler_id < 1048576;  
```  
  
 MIN_MEMORY_PERCENT =*值*  
 指定為此資源集區所保留的最小記憶體數量 (不與其他資源集區共享)。 *值*是預設值為 0 的整數。 允許的範圍*值*是從 0 到 100。  
  
 MAX_MEMORY_PERCENT =*值*  
 指定在此資源集區中，可供要求所用的伺服器記憶體總量。 *值*是預設值為 100 的整數。 允許的範圍*值*是從 1 到 100 之間。  
  
 MIN_IOPS_PER_VOLUME =*值*  
 **適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 指定要為資源集區保留之每個磁碟區的每秒 I/O 作業數 (IOPS) 最小值。 允許的範圍*值*是從 0 到 2 ^31-1 (2147483647)。 指定 0 表示集區沒有最小臨界值。  
  
 MAX_IOPS_PER_VOLUME =*值*  
 **適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 指定要允許資源集區使用之每個磁碟區的每秒 I/O 作業數 (IOPS) 最大值。 允許的範圍*值*是從 0 到 2 ^31-1 (2147483647)。 指定 0 可為集區設定無限的臨界值。 預設值是 0。  
  
 如果集區的 MAX_IOPS_PER_VOLUME 設定為 0，則完全不會管制集區，且即使其他集區設定 MIN_IOPS_PER_VOLUME，該集區也會保留系統中的所有 IOPS。 在此情況下，如果您希望此集區受 IO 管制，建議您將此集區的 MAX_IOPS_PER_VOLUME 值設定為較高的數字 (例如最大值 2^31-1)。  
  
## <a name="remarks"></a>備註  
 MAX_CPU_PERCENT 和 MAX_MEMORY_PERCENT 必須分別大於或等於 MIN_CPU_PERCENT 和 MIN_MEMORY_PERCENT。  
  
 如果有的話，MAX_CPU_PERCENT 可以使用高於 MAX_CPU_PERCENT 值的 CPU 容量。 雖然可能會有週期峰值高於 CAP_CPU_PERCENT，工作負載不應該超過 CAP_CPU_PERCENT 很長的時間，甚至可以使用額外的 CPU 容量時。  
  
 每個相似化元件 (排程器或 NUMA 節點) 的 CPU 百分比總計不應該超過 100%。  
  
 當您要執行 DDL 陳述式時，建議您先熟悉資源管理員的狀態。 如需詳細資訊，請參閱[Resource Governor](../../relational-databases/resource-governor/resource-governor.md)。  
  
 當變更會影響設定的計劃，新設定才會生效先前快取計劃中執行 DBCC FREEPROCCACHE 之後 (*pool_name*)，其中*pool_name*是資源的名稱管理員資源集區。  
  
-   如果您要在單一的排程器，從多個排程器變更親和性，執行 DBCC FREEPROCCACHE 不需要因為平行計畫能以序列模式執行。 不過，它可能無法編譯為以序列計畫的計畫的效率。  
  
-   如果您會將相似性變更單一排程器的多個排程器，就不需要執行 DBCC FREEPROCCACHE。 不過，序列計畫無法以平行方式執行，所以清除個別的快取將會允許新計劃可能會進行編譯使用平行處理原則。  
  
> [!CAUTION]  
>  清除快取的計畫，從一個以上的工作負載群組相關聯的資源集區將會影響所有工作負載群組與使用者定義的資源集區識別*pool_name*。  
  
## <a name="permissions"></a>Permissions  
 需要 CONTROL SERVER 權限。  
  
## <a name="examples"></a>範例  
 下列範例會保留 `default` 集區上的所有預設資源集區設定，除了變更為 `MAX_CPU_PERCENT` 的 `25` 之外。  
  
```  
ALTER RESOURCE POOL "default"  
WITH  
     ( MAX_CPU_PERCENT = 25);  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
 在下列範例中，`CAP_CPU_PERCENT` 會將硬體上限設定為 80%，而且 `AFFINITY SCHEDULER` 會設定為個別值 8 以及 12 到 16 的範圍。  
  
**適用於**： [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
```  
ALTER RESOURCE POOL Pool25  
WITH(   
     MIN_CPU_PERCENT = 5,  
     MAX_CPU_PERCENT = 10,       
     CAP_CPU_PERCENT = 80,  
     AFFINITY SCHEDULER = (8, 12 TO 16),   
     MIN_MEMORY_PERCENT = 5,  
     MAX_MEMORY_PERCENT = 15  
);  
  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [資源管理員](../../relational-databases/resource-governor/resource-governor.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
