---
title: MSrepl_identity_range (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_identity_range_TSQL
- MSrepl_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_identity_range system table
ms.assetid: 6e92a8e8-7667-4c98-b1c4-46735bac50d8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4ba871571c3e5d82596e0ab252c9625ef645237
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52809240"
---
# <a name="msreplidentityrange-transact-sql"></a>MSrepl_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSrepl_identity_range**資料表提供識別範圍管理支援。 這份資料表儲存在發行集、散發和訂閱資料庫中。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**發行者**|**sysname**|發行者的名稱。|  
|**publisher_db**|**sysname**|發行集資料庫的名稱。|  
|**tablename**|**sysname**|資料表的名稱。|  
|**identity_support**|**int**|指定是否啟用自動識別範圍處理。 0 指定不啟用自動識別範圍處理。|  
|**next_seed**|**bigint**|如果啟用了自動識別範圍，便指出下一個範圍的起點。|  
|**pub_range**|**bigint**|發行者識別範圍大小。|  
|**範圍**|**bigint**|將在調整中指派給訂閱者的連續識別值大小。|  
|**max_identity**|**bigint**|識別範圍的上限。|  
|**threshold**|**int**|識別範圍臨界值百分比。|  
|**current_max**|**bigint**|可指派但不必然指派的目前最大值。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
