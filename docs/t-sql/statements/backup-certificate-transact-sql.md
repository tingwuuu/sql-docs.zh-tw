---
title: "備份憑證 (TRANSACT-SQL) |Microsoft 文件"
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
- DUMP_CERTIFICATE_TSQL
- BACKUP CERTIFICATE
- sql13.swb.exportcertificate.f1
- DUMP CERTIFICATE
- BACKUP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], certificates
- decryption [SQL Server], certificates
- exporting certificates
- certificates [SQL Server], exporting
- BACKUP CERTIFICATE statement
- backing up certificates [SQL Server]
- decryption [SQL Server]
- cryptography [SQL Server], certificates
ms.assetid: 509b9462-819b-4c45-baae-3d2d90d14a1c
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0711d429f689fa0aaf0d4332ff2243835d231338
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="backup-certificate-transact-sql"></a>BACKUP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  將憑證匯出至檔案。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server  
  
BACKUP CERTIFICATE certname TO FILE = 'path_to_file'  
    [ WITH PRIVATE KEY   
      (   
        FILE = 'path_to_private_key_file' ,  
        ENCRYPTION BY PASSWORD = 'encryption_password'   
        [ , DECRYPTION BY PASSWORD = 'decryption_password' ]   
      )   
    ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
BACKUP CERTIFICATE certname TO FILE ='path_to_file'  
      WITH PRIVATE KEY   
      (   
        FILE ='path_to_private_key_file',  
        ENCRYPTION BY PASSWORD ='encryption_password'   
      )   
```  
  
## <a name="arguments"></a>引數  
 *path_to_file*  
 指定儲存憑證的檔案之完整路徑，包括檔案名稱。 這可以是本機路徑或通往網路位置的 UNC 路徑。 預設值是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DATA 資料夾的路徑。  
  
 *path_to_private_key_file*  
 指定儲存私密金鑰的檔案之完整路徑，包括檔案名稱。 這可以是本機路徑或通往網路位置的 UNC 路徑。 預設值是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DATA 資料夾的路徑。  
  
 *encryption_password*  
 這是將私密金鑰寫入備份檔之前用來加密該金鑰的密碼。 這個密碼必須遵守複雜性檢查。  
  
 *decryption_password*  
 這是備份私密金鑰之前用來解密該金鑰的密碼。  
  
## <a name="remarks"></a>備註  
 如果是在資料庫中利用密碼加密私密金鑰，則必須指定解密密碼。  
  
 將私密金鑰備份至檔案時，需要加密。 用以保護備份憑證的密碼與用以加密憑證之私密金鑰的密碼並不相同。  
  
 若要還原備份的憑證，使用[CREATE CERTIFICATE](../../t-sql/statements/create-certificate-transact-sql.md)陳述式。  
  
## <a name="permissions"></a>Permissions  
 需要憑證的 CONTROL 權限，且必須知道用來加密私密金鑰的密碼。 如果只備份憑證的公開部份，則需要憑證的某項權限，且未對呼叫端拒絕憑證的 VIEW 權限。  
  
## <a name="examples"></a>範例  
  
### <a name="a-exporting-a-certificate-to-a-file"></a>A. 將憑證匯出至檔案  
 下列範例將憑證匯出至檔案。  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert';  
GO  
```  
  
### <a name="b-exporting-a-certificate-and-a-private-key"></a>B. 匯出憑證和私密金鑰  
 在下列範例中，會利用密碼 `997jkhUbhk$w4ez0876hKHJH5gh` 加密所備份的憑證私密金鑰。  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = 'c:\storedcerts\sales05cert'  
    WITH PRIVATE KEY ( FILE = 'c:\storedkeys\sales05key' ,   
    ENCRYPTION BY PASSWORD = '997jkhUbhk$w4ez0876hKHJH5gh' );  
GO  
```  
  
### <a name="c-exporting-a-certificate-that-has-an-encrypted-private-key"></a>C. 匯出含有加密私密金鑰的憑證  
 在下列範例中，憑證的私密金鑰是在資料庫中加密的。 必須利用密碼 `9875t6#6rfid7vble7r` 來解密私密金鑰。 當憑證儲存至備份檔時，會利用密碼 `9n34khUbhk$w4ecJH5gh` 加密私密金鑰。  
  
```  
BACKUP CERTIFICATE sales09 TO FILE = 'c:\storedcerts\sales09cert'   
    WITH PRIVATE KEY ( DECRYPTION BY PASSWORD = '9875t6#6rfid7vble7r' ,  
    FILE = 'c:\storedkeys\sales09key' ,   
    ENCRYPTION BY PASSWORD = '9n34khUbhk$w4ecJH5gh' );  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-exporting-a-certificate-and-a-private-key"></a>D. 匯出憑證和私密金鑰  
 在下列範例中，會利用密碼 `997jkhUbhk$w4ez0876hKHJH5gh` 加密所備份的憑證私密金鑰。  
  
```  
BACKUP CERTIFICATE sales05 TO FILE = '\\ServerA7\storedcerts\sales05cert'  
    WITH PRIVATE KEY ( FILE = '\\ServerA7\storedkeys\sales05key' ,   
    ENCRYPTION BY PASSWORD = '997jkhUbhk$w4ez0876hKHJH5gh' );  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;TRANSACT-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [卸除憑證 &#40;TRANSACT-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)  
  
  

