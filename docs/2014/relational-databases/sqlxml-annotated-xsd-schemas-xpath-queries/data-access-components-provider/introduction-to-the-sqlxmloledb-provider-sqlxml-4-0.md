---
title: SQLXMLOLEDB 提供者 (SQLXML 4.0) 簡介 |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, properties
- adExecuteStream flag
- SQLXMLOLEDB Provider, about SQLXMLOLEDB Provider
ms.assetid: 2e3f3817-4209-4bf4-9f46-248c95bc6f1b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1ec13acbaa0025b871475675140e83363eb64b81
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52759070"
---
# <a name="introduction-to-the-sqlxmloledb-provider-sqlxml-40"></a>SQLXMLOLEDB 提供者簡介 (SQLXML 4.0)
  SQLXMLOLEDB 提供者是一種 OLE DB 提供者，可透過 ActiveX Data Objects (ADO) 來公開 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 功能。 但是，此提供者只能在 ADO 的「寫入到輸出資料流」模式中執行命令。 SQLXMLOLEDB 提供者不是資料列集提供者。 當您執行命令時，您必須指定 adExecuteStream 旗標，它會指引 ADO 使用您指定的輸出資料流。  
  
 下列範例會顯示在指定 adExecuteStream 旗標時執行命令的語法：  
  
```  
Dim oTestCommand As New ADODB.Command  
...  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Execute , , adExecuteStream  
...  
```  
  
## <a name="sqlxmloledb-provider-specific-properties"></a>SQLXMLOLEDB 提供者特有的屬性  
 SQLXMLOLEDB 提供者會公開以下提供者特有的連接屬性。  
  
|連接<br /><br /> 屬性|預設<br /><br /> (如果有的話)|描述|  
|-----------------------------|----------------------------|-----------------|  
|資料提供者||提供 OLE DB 提供者的 PROGID，SQLXMLOLEDB 會透過它來執行命令。 從 SQLXML 4.0 和 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 開始，這個提供者就會包含在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 中；因此，這個屬性值受限為 "SQLNCLI11"。 如需詳細資訊，請參閱 [SQL Server Native Client 程式設計](../../native-client/sql-server-native-client-programming.md)。|  
  
 SQLXMLOLEDB 提供者會公開以下提供者特有的命令屬性。  
  
|命令<br /><br /> 屬性|預設<br /><br /> (如果有的話)|描述|  
|--------------------------|----------------------------|-----------------|  
|基底路徑|""|指定基底檔案路徑。 基底檔案路徑是用來指定 XML 樣式表語言 (XSL) 或對應結構描述檔案的位置。 基底檔案路徑也會用來解析相對路徑的 XSL 或對應的 XSL 或對應結構描述屬性中所指定的結構描述檔案中。<br /><br /> 如需使用這個屬性的範例，請參閱[執行 XPath 查詢&#40;SQLXMLOLEDB 提供者&#41;](executing-xpath-queries-sqlxmloledb-provider.md)。|  
|ClientSideXML|False|如果您希望將資料列集轉換成 XML 的程序發生在用戶端而不是伺服器上，請將這個屬性設定為 True。 如果您想要將效能負載移到中介層，這個作法會很實用。<br /><br /> 如需使用這個屬性的範例，請參閱[執行 SQL 查詢&#40;SQLXMLOLEDB 提供者&#41;](executing-sql-queries-sqlxmloledb-provider.md)或是[執行範本，包含 SQL 查詢&#40;SQLXMLOLEDB 提供者&#41;](executing-templates-that-contain-sql-queries-sqlxmloledb-provider.md).|  
|內容類型||傳回輸出內容類型。 這是 READ ONLY 屬性。<br /><br /> 這個屬性會將有關內容類型 (如 TEXT/XML、TEXT/HTML、image/jpeg 等等) 的資訊提供給瀏覽器。 這個屬性的值會變成**內容類型**傳送至瀏覽器的 HTTP 標頭，其中包含 MIME 類型 （多用途網際網路郵件延伸標準） 做為主體所傳送的文件的一部分的欄位。|  
|對應結構描述|NULL|如果用戶端應用程式針對對應結構描述 (XDR 或 XSD) 執行 XPath 查詢，這個屬性會用來指定對應結構描述的名稱。<br /><br /> 指定的路徑可以是相對路徑 (xyz/abc/MySchema.xml) 或絕對路徑 (C:\MyFolder\abc\MySchema.xml)。<br /><br /> 如果指定的相對路徑，則基底路徑屬性所指定的基底路徑用來解析相對路徑。 如果已在基底路徑屬性不指定任何路徑，相對路徑是相對於目前的目錄。<br /><br /> 在指定的對應結構描述屬性的值，您可以指定本機目錄路徑或 URL (http://...)。如果您指定 URL，您必須透過 Proxy 伺服器來設定 WinHTTP 存取 HTTP 和 HTTPS 伺服器。 您可以執行 Proxycfg.exe 公用程式來進行這項處理。 如需詳細資訊，請參閱 MSDN Library 中的＜使用 WinHTTP Proxy 組態公用程式＞(英文)。<br /><br /> 如需使用這個屬性的範例，請參閱[執行 XPath 查詢&#40;SQLXMLOLEDB 提供者&#41;](executing-xpath-queries-sqlxmloledb-provider.md)。|  
|命名空間||這個屬性會讓使用命名空間的 XPath 查詢得以執行。 如需使用這個屬性的範例，請參閱[執行含有命名空間的 XPath 查詢&#40;SQLXMLOLEDB 提供者&#41;](executing-xpath-queries-with-namespaces-sqlxmloledb-provider.md)。|  
|ss 資料流旗標||這個屬性是用來指定特定類型的安全性限制。 例如，您可能不想允許指向檔案的 URL 參考或是指向檔案的絕對路徑 (如外部網站)。 或者，您可能不想允許範本中有查詢存在。<br /><br /> 下面的值可以指派給這個屬性：<br /><br /> 1 = STREAM_FLAGS_DISALLOW_URL 2 = STREAM_FLAGS_DISALLOW_ABSOLUTE_PATH 4 = STREAM_FLAGS_DISALLOW_QUERY 8 = STREAM_FLAGS_ DONTCACHEMAPPINGSCHEMA 16 = STREAM_FLAGS_DONTCACHETEMPLATE 32 = STREAM_FLAGS_DONTCACHEXSL<br /><br /> 下一個表格中將提供有關這些值的其他資訊。|  
|xml root||這個屬性是用來定義產生之 XML 的根標記。 例如，如果您針對資料庫執行 SQL 查詢，而且產生的 XML 文件沒有單一根元素，此屬性的值可用來將單一根元素加入到文件中。<br /><br /> 如需使用這個屬性的範例，請參閱[執行 SQL 查詢&#40;SQLXMLOLEDB 提供者&#41;](executing-sql-queries-sqlxmloledb-provider.md)。|  
|xsl||當您想要將 XSL 轉換套用到查詢所傳回的 XML 文件時，可使用這個屬性來指定 XSL 檔案名稱。<br /><br /> 指定的路徑可以是相對路徑 (xyz/abc/MyXSL.xsl) 或絕對路徑 (C:\MyFolder\abc\MyXSL.xsl)。<br /><br /> 如果指定的相對路徑，則基底路徑屬性所指定的基底路徑用來解析相對路徑。 如果已在基底路徑屬性不指定任何路徑，相對路徑是相對於目前的目錄。<br /><br /> 如需使用這個屬性的範例，請參閱套用 XSL 轉換 （SQLXMLOLEDB 提供者）。|  
  
 下表包含 ss Stream 旗標屬性值的描述。  
  
|屬性值|描述|  
|--------------------|-----------------|  
|STREAM_FLAGS_DISALLOW_URL|對應結構描述或 XSL 不接受 URL。|  
|STREAM_FLAGS_DISALLOW_ABSOLTE_PATH|針對對應結構描述或 XSL 指定的路徑必須相對於範本本身的基底路徑。|  
|STREAM_FLAGS_DISALLOW_QUERY|範本中不允許查詢。|  
|STREAM_FLAGS_DONTCACHEMAPPINGSCHEMA|不會快取對應結構描述。 這個屬性值在資料庫開發階段很實用，此時可更改資料庫結構描述。|  
|STREAM_FLAGS_DONTCACHETEMPLATE|不會快取範本。|  
|STREAM_FLAGS_DONTCACHEXSL|不會快取 XSL。|  
  
  
