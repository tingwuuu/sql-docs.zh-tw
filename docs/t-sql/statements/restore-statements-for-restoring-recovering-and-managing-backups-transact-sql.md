---
title: "RESTORE 陳述式，還原、 復原、 管理備份 (T-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- restoring files [SQL Server], RESTORE statement
- RESTORE statement, about restore operations
- database restores [SQL Server], RESTORE statement
- restoring databases [SQL Server], RESTORE statement
- database backups [SQL Server], RESTORE statement
- backing up databases [SQL Server], RESTORE statement
- file restores [SQL Server], RESTORE statement
- transaction log backups [SQL Server], RESTORE statement
ms.assetid: fb29a151-f312-4f85-b857-5deeca0de8ce
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 81443218a21a232248d3f237aba38cfc0d833b7e
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="restore-statements-for-restoring-recovering-and-managing-backups-transact-sql"></a>用來還原、復原和管理備份的 RESTORE 陳述式 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  此章節描述備份所用的 RESTORE 陳述式。 除了用來還原和復原備份的主要 RESTORE {DATABASE | LOG} 陳述式之外，還有許多輔助的 RESTORE 陳述式可協助您管理備份和計畫還原順序。 輔助的 RESTORE 命令包括：RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY、RESTORE REWINDONLY 和 RESTORE VERIFYONLY。  
  
> [!IMPORTANT]  
>  在舊版的 SQL Server 中，任何使用者都可以使用 RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY 和 RESTORE VERIFYONLY 等 Transact-SQL 陳述式來取得有關備份組及備份裝置的資訊。 因為這些陳述式會揭露有關備份檔案內容的資訊，所以在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更新的版本中，這些陳述式需要 CREATE DATABASE 權限。 與舊版相較，這項需求更能完整地保障備份檔案及備份資訊的安全。 如需這個權限的相關資訊，請參閱 [GRANT 資料庫權限 &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
|引數|Description|  
|---------------|-----------------|  
|[RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)|描述利用 BACKUP 命令從備份中還原和復原資料庫時，所用的 RESTORE DATABASE 和 RESTORE LOG Transact-SQL 陳述式。 在所有復原模式之下，資料庫都會使用 RESTORE DATABASE。 只有完整復原模式和大量記錄復原模式會使用 RESTORE LOG。 您也可以利用 RESTORE DATABASE，將資料庫回復為資料庫快照集。|  
|[RESTORE 引數 &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)|說明 RESTORE 陳述式及一組相關的輔助陳述式 (RESTORE FILELISTONLY、RESTORE HEADERONLY、RESTORE LABELONLY、RESTORE REWINDONLY 和 RESTORE VERIFYONLY) 之「語法」各章節所描述的引數。 大部份引數都只得到這六個引數其中一部份的支援。 在每個引數的描述中，都會指出引數所得到的支援。|  
|[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-filelistonly-transact-sql.md)|描述 RESTORE FILELISTONLY Transact-SQL 陳述式，這個陳述式用來傳回含有資料庫清單的結果集，以及備份組所包含的記錄檔。|  
|[RESTORE HEADERONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md)|描述 RESTORE HEADERONLY Transact-SQL 陳述式，這個陳述式用來傳回含有特定備份裝置上的所有備份組之所有備份標頭資訊的結果集。|  
|[RESTORE LABELONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-labelonly-transact-sql.md)|描述 RESTORE LABELONLY Transact-SQL 陳述式，這個陳述式用來傳回含有給定備份裝置所識別的備份媒體之相關資訊的結果集。|  
|[RESTORE REWINDONLY &#40;TRANSACT-SQL &#41;](../../t-sql/statements/restore-statements-rewindonly-transact-sql.md)|描述 RESTORE REWINDONLY Transact-SQL 陳述式，這個陳述式用來倒轉和關閉設定 NOREWIND 選項來執行的 BACKUP 或 RESTORE 陳述式，保留了其開啟狀態的磁帶裝置。|  
|[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-verifyonly-transact-sql.md)|描述 RESTORE VERIFYONLY Transact-SQL 陳述式，這個陳述式可用來驗證備份，但不進行還原，同時也會檢查備份組是否已完成，整個備份是否可讀取；它不會嘗試驗證資料的結構。|  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 資料庫的備份與還原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  