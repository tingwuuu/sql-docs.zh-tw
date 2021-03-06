---
title: sp_help_category (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_category
- sp_help_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_category
ms.assetid: 8cad1dcc-b43e-43bd-bea0-cb0055c84169
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 69f65ee2e299197504c4bd970a835a28c2f89b21
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58534140"
---
# <a name="sphelpcategory-transact-sql"></a>sp_help_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  提供指定的作業、警示或操作員的相關資訊。  
   
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_category [ [ @class = ] 'class' ]   
     [ , [ @type = ] 'type' ]   
     [ , [ @name = ] 'name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>引數  
`[ @class = ] 'class'` 了解哪種要求之資訊的類別。 *類別*已**varchar(8)**，預設值是**作業**。 *類別*可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**JOB**|提供作業類別目錄的相關資訊。|  
|**ALERT**|提供警示類別目錄的相關資訊。|  
|**運算子**|提供操作員類別目錄的相關資訊。|  
  
`[ @type = ] 'type'` 要求資訊的類別目錄的類型。 *型別*已**varchar(12)**，預設值是 NULL，而且可以是下列值之一。  
  
|值|描述|  
|-----------|-----------------|  
|**LOCAL**|本機作業類別目錄。|  
|**MULTI -SERVER**|多伺服器作業類別目錄。|  
|**NONE**|類別目錄以外的類別**作業**。|  
  
`[ @name = ] 'name'` 要求資訊的類別目錄名稱。 *名稱*已**sysname**，預設值是 NULL。  
  
`[ @suffix = ] suffix` 指定是否**category_type**結果集中的資料行是識別碼或名稱。 *後置詞*已**位元**，預設值是**0**。 **1**會顯示**category_type**做為名稱，以及**0**顯示做為識別碼。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="result-sets"></a>結果集  
 當**@suffix**是**0**， **sp_help_category**會傳回下列結果集：  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|類別目錄識別碼|  
|**category_type**|**tinyint**|類別目錄類型：<br /><br /> **1** = 本機<br /><br /> **2** = 多伺服器<br /><br /> **3** = 無|  
|**name**|**sysname**|類別目錄名稱|  
  
 當**@suffix**是**1**， **sp_help_category**會傳回下列結果集：  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|類別目錄識別碼|  
|**category_type**|**sysname**|類別目錄的類型。 其中一個**本機**， **MULTI-SERVER**，或**NONE**|  
|**name**|**sysname**|類別目錄名稱|  
  
## <a name="remarks"></a>備註  
 **sp_help_category**必須從執行**msdb**資料庫。  
  
 如果未指定任何參數，結果集會提供所有作業類別目錄的相關資訊。  
  
## <a name="permissions"></a>Permissions  
 依預設，只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員，才能夠執行這個預存程序。 其他使用者必須被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **資料庫的下列其中一個** Agent 固定資料庫角色。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 如需這些角色權限的詳細資訊，請參閱 [SQL Server Agent 固定資料庫角色](../../ssms/agent/sql-server-agent-fixed-database-roles.md)。  
  
## <a name="examples"></a>範例  
  
### <a name="a-returning-local-job-information"></a>A. 傳回本機作業資訊  
 下列範例會傳回本機環境所管理之作業的相關資訊。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @type = N'LOCAL' ;  
GO  
```  
  
### <a name="b-returning-alert-information"></a>B. 傳回警示資訊  
 下列範例會傳回「複寫警示」類別目錄的相關資訊。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @class = N'ALERT',  
    @name = N'Replication' ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
