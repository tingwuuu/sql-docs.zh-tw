---
title: sys.fulltext_stopwords & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_stopwords_TSQL
- fulltext_stopwords
- sys.fulltext_stopwords
- sys.fulltext_stopwords_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stopwords
- sys.fulltext_stopwords catalog view
- stopwords [full-text search]
ms.assetid: 79787bb7-d729-448e-b56a-0a467bbb304f
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8395d9fe246d70843415079cdf188ac00817f51f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832046"
---
# <a name="sysfulltextstopwords-transact-sql"></a>sys.fulltext_stopwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  針對資料庫中所有停用字詞表的每個停用字詞，各包含一個資料列。  
 
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**stoplist_id**|**int**|**stopword** 所屬之停用字詞表的識別碼。 此識別碼在資料庫中是唯一的。|  
|**stopword**|**nvarchar(64)**|要針對停用字詞比對進行考量的詞彙。|  
|**語言**|**sysname**|不是值中的別名[sys.fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)地區設定識別碼值對應 (**LCID**)，或是數值 LCID 的字串表示法。|  
|**language_id**|**int**|用於斷詞的 LCID。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [物件目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [設定及管理全文檢索搜尋的停用字詞與停用字詞表](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_system_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)  
  
  
