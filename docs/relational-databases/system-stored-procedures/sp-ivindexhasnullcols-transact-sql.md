---
title: sp_ivindexhasnullcols (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_ivindexhasnullcols
- sp_ivindexhasnullcols_TSQL
helpviewer_keywords:
- sp_ivindexhasnullcols
ms.assetid: ed2cde63-37e1-43cf-b6ba-3b6114a0f797
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 77a0e3f1795545e553347ae699e719af2ad506b4
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531573"
---
# <a name="spivindexhasnullcols-transact-sql"></a>sp_ivindexhasnullcols (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  驗證索引檢視的叢集索引是唯一的，且並未包含將利用索引檢視來建立交易式發行集時，可為 Null 值的任何資料行。 這個預存程序執行於發行集資料庫的發行者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_ivindexhasnullcols [ @viewname = ] 'view_name'  
        , [ @fhasnullcols= ] field_has_null_columns OUTPUT  
```  
  
## <a name="arguments"></a>引數  
`[ @viewname = ] 'view_name'` 是要驗證名稱。 *view_name*已**sysname**，沒有預設值。  
  
`[ @fhasnullcols = ] field_has_null_columns OUTPUT` 指定旗標，用來指示檢視索引是否有允許 NULL 的資料行。 *view_name*已**sysname**，沒有預設值。 傳回值**1**檢視索引是否允許 NULL 的資料行。 傳回值**0**如果檢視並未包含允許 null 值的資料行。  
  
> [!NOTE]  
>  如果預存程序本身會傳回傳回碼為**1**，這表示預存程序執行失敗，這個值是**0** ，應該予以忽略。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_ivindexhasnullcols**正由異動複寫。  
  
 依預設，發行集中的索引檢視發行項會建立成訂閱者端的資料表。 不過，當索引資料行允許 NULL 值時，會將索引檢視建立成在訂閱者端的索引檢視，而非資料表。 當執行這個預存程序時，它可以警示使用者目前的索引檢視有沒有這個問題。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_ivindexhasnullcols**。  
  
## <a name="see-also"></a>另請參閱  
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
