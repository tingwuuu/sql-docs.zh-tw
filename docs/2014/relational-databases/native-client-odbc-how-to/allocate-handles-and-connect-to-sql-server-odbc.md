---
title: 配置控制代碼並連接到 SQL Server (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 322120624c612371b56029c2cf29c9ab457c81b5
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376352"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>配置控制代碼並連接到 SQL Server (ODBC)
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>配置控制代碼並連接到 SQL Server  
  
1.  加入 ODBC 標頭檔 Sql.h、Sqlext.h、Sqltypes.h。  
  
2.  加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驅動程式專屬的標頭檔 Odbcss.h。  
  
3.  呼叫[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)使用`HandleType`SQL_HANDLE_ENV 來初始化 ODBC 並配置環境控制代碼。  
  
4.  呼叫[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)具有`Attribute`設定為 SQL_ATTR_ODBC_VERSION 並`ValuePtr`設定為 sql_ov_odbc3 時，表示應用程式會使用 ODBC 3.x 格式函式呼叫。  
  
5.  （選擇性） 呼叫[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)來設定其他環境選項或呼叫[SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403)來取得環境選項。  
  
6.  呼叫[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)使用`HandleType`配置連接控制代碼的利用 SQL_HANDLE_DBC。  
  
7.  （選擇性） 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)來設定連接選項或呼叫[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md)來取得連接選項。  
  
8.  呼叫，用以連接到現有的資料來源的 SQLConnect [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
     或  
  
     呼叫[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)若要使用的連接字串來連接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
     完整的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接字串至少擁有下列其中一種形式：  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     如果連接字串不完整，`SQLDriverConnect` 可以提示所需的資訊。 這由指定的值控制*DriverCompletion*參數。  
  
     \-或-  
  
     呼叫[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md)多次以反覆的方式來建置連接字串，並連接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
9. （選擇性） 呼叫[SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md)以取得驅動程式屬性和行為[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料來源。  
  
10. 配置與使用陳述式。  
  
11. 呼叫中斷 SQLDisconnect[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]並使連接控制代碼可供新的連接。  
  
12. 呼叫[SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md)與`HandleType`來釋放連接控制代碼的利用 SQL_HANDLE_DBC。  
  
13. 利用 SQL_HANDLE_ENV 的 `SQLFreeHandle` 呼叫 `HandleType` 來釋放環境控制代碼。  
  
> [!IMPORTANT]  
>  盡可能使用 Windows 驗證。 如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。 請避免將認證儲存在檔案中。 如果您必須保存認證，則應該用 [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) 加密這些認證。  
  
## <a name="example"></a>範例  
 此範例顯示呼叫 `SQLDriverConnect` 來連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，而不需要現有的 ODBC 資料來源。 將不完整的連接字串傳遞到 `SQLDriverConnect` 時，會使 ODBC 驅動程式提示使用者輸入遺漏的資訊。  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
