---
title: sp_pdw_database_encryption （SQL 資料倉儲） |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: f5ccb424-7a95-4557-b774-c69de33c1545
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a2ab88ca9a65d65e80f715ff4f8eb13c31b2d903
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536400"
---
# <a name="sppdwdatabaseencryption-sql-data-warehouse"></a>sp_pdw_database_encryption （SQL 資料倉儲）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  使用**sp_pdw_database_encryption**上啟用透明資料加密，如[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]應用裝置。 當**sp_pdw_database_encryption**設定為 1，使用**ALTER DATABASE**使用 TDE 加密資料庫的陳述式。  
  
## <a name="syntax"></a>語法  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_database_encryption [ [ @enabled = ] enabled ] ;  
```  
  
#### <a name="parameters"></a>參數  
`[ @enabled = ] enabled` 判斷是否已啟用透明資料加密。 *已啟用*已**int**，而且可以是下列值之一：  
  
-   0 = 已停用  
  
-   1 = 已啟用  
  
 執行**sp_pdw_database_encryption**沒有參數傳回做為純量結果集的應用裝置上的 TDE 的目前狀態：啟用為停用，0 或 1。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 當使用啟用 TDE **sp_pdw_database_encryption**，tempdb 資料庫卸除、 重新建立並加密。 基於這個理由，TDE 時，無法啟用應用裝置上沒有其他作用中工作階段使用 tempdb。 啟用或停用應用裝置上的 TDE 是設備，在大部分情況下的狀態變更動作預期要執行一次在設備存留期，而且應用裝置上沒有流量時執行。  
  
## <a name="permissions"></a>Permissions  
 需要的成員資格**sysadmin**固定資料庫角色，或**CONTROL SERVER**權限。  
  
## <a name="example"></a>範例  
 下列範例會在應用裝置上啟用 TDE。  
  
```sql  
EXEC sys.sp_pdw_database_encryption 1;  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL 資料倉儲&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)   
 [sp_pdw_log_user_data_masking &#40;SQL 資料倉儲&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
  
