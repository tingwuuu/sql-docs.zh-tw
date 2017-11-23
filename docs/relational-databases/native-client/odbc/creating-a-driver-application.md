---
title: "建立 SQL Server Native Client ODBC 驅動程式應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
caps.latest.revision: "42"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 27f2495ef99f499e9e041f488f8effee328437f5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="creating-a-driver-application"></a>建立驅動程式應用程式
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC 架構包含四個執行下列函數的元件。  
  
|元件|函數|  
|---------------|--------------|  
|應用程式|呼叫 ODBC 函數與 ODBC 資料來源進行通訊、提交 SQL 陳述式，以及處理結果集。|  
|驅動程式管理員|管理應用程式與應用程式所使用之所有 ODBC 驅動程式之間的通訊。|  
|驅動程式|處理來自應用程式的所有 ODBC 函數呼叫、連接到資料來源、將 SQL 陳述式從應用程式傳遞到資料來源，以及將結果傳回到應用程式。 如果必要，取動程式會將 ODBC SQL 從應用程式轉譯成資料來源所使用的原生 SQL。|  
|資料來源|包含驅動程式在 DBMS 中存取特定資料執行個體所需的所有資訊。|  
  
 使用的應用程式[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式的執行個體與通訊[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]會執行下列工作：  
  
-   與資料來源連接  
  
-   將 SQL 陳述式傳送到資料來源  
  
-   從資料來源處理陳述式的結果  
  
-   處理錯誤與訊息  
  
-   結束資料來源的連接  
  
 針對所撰寫的更複雜應用程式[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式可能也會執行下列工作：  
  
-   使用資料指標控制結果集中的位置  
  
-   要求交易控制的認可或復原作業  
  
-   執行包含兩部或多部伺服器的分散式交易  
  
-   在遠端伺服器上執行預存程序  
  
-   呼叫目錄函數來查詢結果集的屬性  
  
-   執行大量複製作業  
  
-   管理大型資料 (**varchar （max)**， **nvarchar （max)**，和**varbinary （max)**資料行) 作業  
  
-   設定資料庫鏡像時，使用重新連接邏輯來簡化容錯移轉  
  
-   記錄效能資料和長時間執行的查詢  
  
 若要進行 ODBC 函數呼叫，C 或 C++ 應用程式必須包含 sql.h、sqlext.h 和 sqltypes.h 標頭檔。 若要呼叫 ODBC 安裝程式 API 函數，應用程式必須包含 odbcinst.h 標頭檔。 Unicode ODBC 應用程式必須包含 sqlucode.h 標頭檔。 ODBC 應用程式必須與 odbc32.lib 檔連結。 呼叫 ODBC 安裝程式 API 函數的 ODBC 應用程式必須與 odbccp32.lib 檔連結。 這些檔案包含在 Windows Platform SDK 中。  
  
 許多 ODBC 驅動程式，包括[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式，提供驅動程式專屬的 ODBC 延伸模組。 若要善用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式專屬延伸模組，應用程式應該包含 sqlncli.h 標頭檔。 這個標頭檔包含：  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式特有的連接屬性。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式特有的陳述式屬性。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式專屬的資料行屬性。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專屬的資料類型。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專屬的使用者定義資料類型。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式專屬[SQLGetInfo](../../../relational-databases/native-client-odbc-api/sqlgetinfo.md)型別。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式診斷欄位。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專屬的診斷動態函數程式碼。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專屬原生 C 資料類型的 C/C++ 類型定義 (當資料行繫結至 C 資料類型 SQL_C_BINARY 時傳回)。  
  
-   SQLPERF 資料結構的類型定義。  
  
-   支援透過 ODBC 連接使用大量複製 API 的大量複製巨集和原型。  
  
-   針對連結之伺服器及其目錄的清單，呼叫分散式查詢中繼資料 API 函數。  
  
 使用大量複製功能的任何 C 或 c + + ODBC 應用程式[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式必須與 sqlncli11.lib 檔連結。 呼叫分散式查詢中繼資料 API 函數的應用程式也必須與 sqlncli11.lib 連結。 Sqlncli.h 和 sqlncli11.lib 檔案會隨著發佈[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]開發人員工具。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的 Include 和 Lib 目錄應該位於編譯器的 INCLUDE 和 LIB 路徑，如下所示：  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 先前在建立應用程式的過程中所做的其中一個設計決策為：應用程式是否需要同時讓多個 ODBC 呼叫未完成。 有兩種方法可以支援同時呼叫多個 ODBC，本節其他主題將會有完整說明。 如需詳細資訊，請參閱[ODBC 程式設計人員參考](http://go.microsoft.com/fwlink/?LinkId=45250)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [非同步模式和 SQLCancel](../../../relational-databases/native-client/odbc/creating-a-driver-application-asynchronous-mode-and-sqlcancel.md)  
  
-   [多執行緒應用程式](../../../relational-databases/native-client/odbc/creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a>請參閱＜  
 [SQL Server Native Client &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  