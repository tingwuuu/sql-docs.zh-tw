---
title: sp_help_spatial_geography_index_xml (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index_xml_TSQL
- sp_help_spatial_geography_index_xml
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index_xml procedure
ms.assetid: 821d4127-3ce5-4474-8561-043404a20d81
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ed44f70a49c1cf221a9ef74b19030512273b1480
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671537"
---
# <a name="sphelpspatialgeographyindexxml-transact-sql"></a>sp_help_spatial_geography_index_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  傳回有關的名稱和一組指定的屬性值**地理區**空間索引。 您可以選擇傳回核心屬性集或索引的所有屬性。  
  
 結果會以 XML 片段傳回，該片段會顯示所選取屬性的名稱和值。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_help_spatial_geography_index_xml [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>引數  
 請參閱[引數和屬性的空間索引預存程序](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)。  
  
## <a name="properties"></a>屬性  
 請參閱[引數和屬性的空間索引預存程序](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md)。  
  
## <a name="permissions"></a>Permissions  
 必須為使用者指派 PUBLIC 角色才能存取此程序。 需要在伺服器和物件上具有 READ ACCESS 權限。  
  
## <a name="remarks"></a>備註  
 包含 NULL 值的屬性不會包含在傳回集合中。  
  
## <a name="example"></a>範例  
 下列範例會使用`sp_help_spatial_geography_index_xml`來調查空間索引**SIndx_SpatialTable_geography_col2**資料表上定義**geography_col&lt**給定的查詢範例**@qs**. 此範例以 XML 片段傳回指定索引的核心屬性，該片段會顯示所選取屬性的名稱和值。  
  
 [XQuery](../../xquery/xquery-basics.md)接著會在結果集，傳回特定的屬性上執行。  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
declare @x xml;  
exec sp_help_spatial_geography_index_xml 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs, @x output;  
select @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 類似於[sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)，此預存程序提供更簡單的屬性以程式設計方式存取**geography**空間索引，並報告中 XML 的結果集。  
  
 週框方塊**地理區**是整個地球。  
  
## <a name="requirements"></a>需求  
  
## <a name="see-also"></a>另請參閱  
 [空間索引預存程序](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [空間索引概觀](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [空間資料 &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [XQuery 基本概念](../../xquery/xquery-basics.md)   
 [XQuery 語言參考](../../xquery/xquery-language-reference-sql-server.md)  
  
  
