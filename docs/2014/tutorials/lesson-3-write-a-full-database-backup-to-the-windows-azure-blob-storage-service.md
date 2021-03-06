---
title: 第 3 課：完整資料庫備份寫入 Windows Azure Blob 儲存體服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 242e32b08ec6346c39e149628e773b33554c95d4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029789"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>第 3 課：完整資料庫備份寫入 Windows Azure Blob 儲存體服務
  這一課將示範如何使用 tsql 陳述式來執行 Windows Azure Blob 儲存體服務的完整資料庫備份。  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>執行 Windows Azure Blob 儲存體服務的完整資料庫備份  
 若要建立完整資料庫備份，請使用下列步驟：  
  
1.  連接到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。  
  
2.  在 **[物件總管]** 中，連接到 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]的執行個體。  
  
3.  在 [標準] 功能表列上，按一下 **[新增查詢]**。  
  
4.  將下列範例複製並貼入查詢視窗中、視需要修改，然後按一下 **[執行]**。  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  在 [物件總管] 中，連接到 Azure 儲存體。 瀏覽並尋找容器以及新建立的備份檔案。  
  
## <a name="next-lesson"></a>下一課  
 [第 4 課：從完整資料庫備份執行還原](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)。  
  
  
