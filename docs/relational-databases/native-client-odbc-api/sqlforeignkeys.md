---
title: "SQLForeignKeys |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cba3db790f278964b190944198225ea6b0294cbd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援串聯更新，而且會透過外部索引鍵條件約束機制刪除。 如果在 FOREIGN KEY 條件約束的 ON UPDATE 和/或 ON DELETE 子句上指定 CASCADE 選項，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會針對 UPDATE_RULE 和/或 DELETE_RULE 資料行傳回 SQL_NO_ACTION。 如果在 FOREIGN KEY 條件約束的 ON UPDATE 和/或 ON DELETE 子句上指定 NO ACTION 選項，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會針對 UPDATE_RULE 和/或 DELETE_RULE 資料行傳回 SQL_NO_ACTION。  
  
 當無效的值會在任何**SQLForeignKeys**參數， **SQLForeignKeys**上執行都會傳回 SQL_SUCCESS。 **SQLFetch**這些參數中使用無效值時，傳回 sql_no_data 為止。  
  
 **SQLForeignKeys**可以在靜態伺服器資料指標上執行。 嘗試執行**SQLForeignKeys**可更新的 （動態或索引鍵集） 資料指標會傳回 SQL_SUCCESS_WITH_INFO，指出資料指標類型已變更。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式支援的報告資訊連結的伺服器上的資料表所接受的兩段式名稱*FKCatalogName*和*PKCatalogName*參數： *Linked_Server_Name.Catalog_Name*。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLForeignKeys 函數](http://go.microsoft.com/fwlink/?LinkId=59344)   
 [ODBC API 實作詳細資料](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  