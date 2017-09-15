---
title: "建立伺服器角色 (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SERVER_ROLE_TSQL
- CREATE SERVER ROLE
- SERVER ROLE
- CREATE_SERVER_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE
- SERVER ROLE, CREATE
- CREATE SERVER ROLE statement
- ROLE
- user-defined server roles [SQL Server]
- roles, server
ms.assetid: 30c92f80-f7f6-4a84-ae89-16e69add0de6
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 445c44ad009ff9bd6509d077f5f579d0f7f42855
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="create-server-role-transact-sql"></a>CREATE SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

  建立新的使用者定義伺服器角色。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server and Parallel Data Warehouse  
  
CREATE SERVER ROLE role_name [ AUTHORIZATION server_principal ]  
```  
  
## <a name="arguments"></a>引數  
 *role_name*  
 這是即將建立的伺服器角色名稱。  
  
 授權*server_principal*  
 這是即將擁有新伺服器角色的登入。 如果未指定任何登入，該伺服器角色便由執行 CREATE SERVER ROLE 的登入所擁有。  
  
## <a name="remarks"></a>備註  
 伺服器角色是伺服器層級安全性實體。 當您建立伺服器角色之後，請利用 GRANT、DENY 和 REVOKE，設定角色的伺服器層級權限。 若要新增登入，或從伺服器角色移除登入，使用[ALTER SERVER ROLE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-server-role-transact-sql.md). 若要卸除伺服器角色，使用[DROP SERVER ROLE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-server-role-transact-sql.md). 如需詳細資訊，請參閱 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)。  
  
 您可以檢視伺服器角色，藉由查詢[sys.server_role_members](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)和[sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)目錄檢視。  
  
 不能將資料庫層級安全性實體授與伺服器角色。 若要建立資料庫角色，請參閱 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)。  
  
 如需設計權限系統的資訊，請參閱 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)。  
  
## <a name="permissions"></a>Permissions  
 需要 CREATE SERVER ROLE 權限或系統管理員 (sysadmin) 固定伺服器角色中的成員資格。  
  
 此外，也需要登入之 *server_principal* 的 IMPERSONATE、作為 *server_principal*之伺服器角色的 ALTER 權限，或作為 server_principal 之 Windows 群組中的成員資格。  
  
 這會引發 Audit Server Principal Management 事件與要加入的物件類型設定為伺服器角色和事件類型。  
  
 當您使用 AUTHORIZATION 選項指派伺服器角色擁有權時，也必須具備下列權限：  
  
-   若要指派伺服器角色擁有權給另一個登入，則需要該登入的 IMPERSONATE 權限。  
  
-   若要指派伺服器角色擁有權給另一個伺服器角色，則需要收件者伺服器角色中的成員資格，或該伺服器角色的 ALTER 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-creating-a-server-role-that-is-owned-by-a-login"></a>A. 建立登入所擁有的伺服器角色  
 下列範例會建立登入 `buyers` 所擁有的伺服器角色 `BenMiller`。  
  
```  
USE master;  
CREATE SERVER ROLE buyers AUTHORIZATION BenMiller;  
GO  
```  
  
### <a name="b-creating-a-server-role-that-is-owned-by-a-fixed-server-role"></a>B. 建立固定伺服器角色所擁有的伺服器角色  
 下列範例會建立固定伺服器角色 `auditors` 所擁有的伺服器角色 `securityadmin`。  
  
```  
USE master;  
CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [DROP SERVER ROLE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [主體 &#40;Database Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [資料庫引擎權限使用者入門](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
  
