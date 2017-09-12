---
title: "ALTER APPLICATION ROLE (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_APPLICATION_ROLE_TSQL
- ALTER APPLICATION ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- modifying application roles
- passwords [SQL Server], application roles
- ALTER APPLICATION ROLE statement
- application roles [SQL Server], modifying
ms.assetid: c6cd5d0f-18f4-49be-b161-64d9c5569086
caps.latest.revision: 46
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d5205897f64dfb05d8903ed2f4197f35bd722224
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="alter-application-role-transact-sql"></a>ALTER APPLICATION ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  變更應用程式角色的名稱、密碼或預設結構描述。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
ALTER APPLICATION ROLE application_role_name   
    WITH <set_item> [ ,...n ]  
  
<set_item> ::=   
    NAME = new_application_role_name   
    | PASSWORD = 'password'  
    | DEFAULT_SCHEMA = schema_name  
```  
  
## <a name="arguments"></a>引數  
 *application_role_name*  
 這是要修改的應用程式角色名稱。  
  
 名稱 =*new_application_role_name*  
 指定應用程式角色的新名稱。 這個名稱必須尚未用來參考資料庫中的任何主體。  
  
 密碼 ='*密碼*'  
 指定應用程式角色的密碼。 *密碼*必須符合正在執行的執行個體之電腦的 Windows 密碼原則需求[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 您一定要使用增強式密碼。  
  
 DEFAULT_SCHEMA =*schema_name*  
 指定當伺服器解析物件名稱時，將搜尋的第一個結構描述。 *schema_name*可以是不存在於資料庫的結構描述。  
  
## <a name="remarks"></a>備註  
 如果資料庫中已存在新的應用程式角色名稱，則這個陳述式會失敗。 變更應用程式角色的名稱、密碼或預設結構描述時，與角色相關聯的識別碼不變。  
  
> [!IMPORTANT]  
>  密碼到期原則不適用於應用程式角色密碼。 因此，在選取增強式密碼時請特別小心。 叫用應用程式角色的應用程式必須儲存其密碼。  
  
 您可以在 sys.database_principals 目錄檢視中，看到應用程式角色。  
  
> [!CAUTION]  
>  在[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]從在舊版的行為變更結構描述的行為[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 假設結構描述相當於資料庫使用者的程式碼可能不會傳回正確的結果。 曾經使用下列任何一個 DDL 陳述式的資料庫中不應該使用舊的目錄檢視 (包括 sysobjects)：CREATE SCHEMA、ALTER SCHEMA、DROP SCHEMA、CREATE USER、ALTER USER、DROP USER、CREATE ROLE、ALTER ROLE、DROP ROLE、CREATE APPROLE、ALTER APPROLE、DROP APPROLE、ALTER AUTHORIZATION。 在曾經使用這些陳述式的任何一個資料庫中，您必須使用新的目錄檢視。 新的目錄檢視會考量 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中所導入的主體和結構描述的分隔。 如需目錄檢視的詳細資訊，請參閱[目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)。  
  
## <a name="permissions"></a>Permissions  
 需要資料庫的 ALTER ANY APPLICATION ROLE 權限。 若要變更預設的結構描述，使用者還需要在應用程式角色上具有 ALTER 權限。 應用程式角色可改變它自己的預設結構描述，但不能變更它的名稱或密碼。  
  
## <a name="examples"></a>範例  
  
### <a name="a-changing-the-name-of-application-role"></a>A. 變更應用程式角色的名稱  
 下列範例會將應用程式角色的名稱 `weekly_receipts` 變更為 `receipts_ledger`。  
  
```  
USE AdventureWorks2012;  
CREATE APPLICATION ROLE weekly_receipts   
    WITH PASSWORD = '987Gbv8$76sPYY5m23' ,   
    DEFAULT_SCHEMA = Sales;  
GO  
ALTER APPLICATION ROLE weekly_receipts   
    WITH NAME = receipts_ledger;  
GO  
```  
  
### <a name="b-changing-the-password-of-application-role"></a>B. 變更應用程式角色的密碼  
 下列範例會變更應用程式角色 `receipts_ledger` 的密碼。  
  
```  
ALTER APPLICATION ROLE receipts_ledger   
    WITH PASSWORD = '897yUUbv867y$200nk2i';  
GO  
```  
  
### <a name="c-changing-the-name-password-and-default-schema"></a>C. 變更名稱、密碼和預設結構描述  
 下列範例會同時變更應用程式角色 `receipts_ledger` 的名稱、密碼和預設結構描述。  
  
```  
ALTER APPLICATION ROLE receipts_ledger   
    WITH NAME = weekly_ledger,   
    PASSWORD = '897yUUbv77bsrEE00nk2i',   
    DEFAULT_SCHEMA = Production;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [應用程式角色](../../relational-databases/security/authentication-access/application-roles.md)   
 [建立應用程式角色 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  