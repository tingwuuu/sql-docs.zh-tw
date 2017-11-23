---
title: "sys.crypt_properties (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- crypt_properties
- crypt_properties_TSQL
- sys.crypt_properties_TSQL
- sys.crypt_properties
dev_langs: TSQL
helpviewer_keywords: sys.crypt_properties catalog view
ms.assetid: d5684f5a-30b1-418e-ae4d-ab040db9257e
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ded0c42bbfd7c16b30ab93c9212c6c69b0e2a587
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="syscryptproperties-transact-sql"></a>sys.crypt_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  針對每一個與安全性實體相關聯的密碼編譯屬性，各傳回一個資料列。  
  
||  
|-|  
|**適用於**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]透過[新版](http://go.microsoft.com/fwlink/p/?LinkId=299658))， [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] ([某些區域處於預覽](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag))。|  
  
|資料行名稱|資料類型|Description|  
|-----------------|---------------|-----------------|  
|**類別**|**tinyint**|識別屬性所在的項目類別。<br /><br /> 1 = 物件或資料行|  
|**class_desc**|**nvarchar （60)**|屬性所在項目類別的描述。<br /><br /> OBJECT_OR_COLUMN|  
|**則 major_id 就**|**int**|屬性所在項目的識別碼，根據類別加以解譯|  
|**憑證指紋**|**varbinary(32)**|所用憑證或非對稱金鑰的 SHA-1 雜湊。|  
|**crypt_type**|**char(4)**|加密類型。<br /><br /> SPVC = 以憑證私密金鑰加密<br /><br /> SPVA = 以非對稱私密金鑰加密<br /><br /> CPVC = 以憑證私密金鑰簽署的計數器簽章<br /><br /> CPVA = 以非對稱金鑰簽署的計數器簽章|  
|**crypt_type_desc**|**nvarchar （60)**|加密類型的描述。<br /><br /> SIGNATURE BY CERTIFICATE<br /><br /> SIGNATURE BY ASYMMETRIC KEY<br /><br /> COUNTER SIGNATURE BY CERTIFICATE<br /><br /> COUNTER SIGNATURE BY ASYMMETRIC KEY|  
|**crypt_property**|**varbinary(max)**|簽署或加密的位元。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 如需相關資訊，請參閱 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>請參閱＜  
 [安全性目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [加密階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [安全性實體](../../relational-databases/security/securables.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  