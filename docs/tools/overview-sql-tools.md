---
title: "SQL 工具和公用程式 SQL Server、 Azure SQL Database 和 SQL 資料倉儲 |Microsoft 文件"
ms.custom: 
ms.date: 08/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 0
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: eccbe54c561e009858f6192126abc57e3399082c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="tools-and-utilities-for-azure-sql-database-sql-server-and-sql-data-warehouse"></a>工具和公用程式，Azure SQL Database、 SQL Server 和 SQL 資料倉儲

[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]  

![](../includes/media/sql-database-tools.png)本文章會提供一份可用的工具，使用 SQL Server、 Azure SQL Database、 SQL 資料倉儲和 SQL Server 為基礎的應用程式。 

如果您想要跳中的權限和建立資料表，開始執行的查詢時，基本上設計和管理您的資料庫，然後[ **SQL Server Management Studio (SSMS)** ](../ssms/download-sql-server-management-studio-ssms.md)最有可能是您移至的工具。 SSMS 是免費的並在 Windows 上執行。

如果您執行 Linux 或 macOS，請嘗試[Visual Studio Code](https://code.visualstudio.com/)與[ **Visual Studio 程式碼的 mssql** ](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)延伸模組。 這些工具的一組豐富的功能，以開發 Microsoft SQL Server、 Azure SQL Database 和 SQL 資料倉儲，還有可用。 請參閱[使用 Visual Studio 程式碼來建立和執行 SQL Server 的 TRANSACT-SQL 指令碼](../linux/sql-server-linux-develop-use-vscode.md)。


## <a name="sql-tools"></a>SQL 工具 
 
| 工具 | Description |
|:--|:--|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | 您可以使用 SQL Server Management Studio (SSMS) 來查詢、 設計和管理 SQL Server、 Azure SQL Database 和 Azure SQL 資料倉儲。 |
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | 開啟 Visual Studio 強大的開發環境中 SQL Server、 Azure SQL Database 和 Azure SQL 資料倉儲。 |
| [Visual Studio 程式碼](https://code.visualstudio.com/)| Visual Studio 程式碼適用於 Linux、 macOS 和 Windows。 安裝 Visual Studio 程式碼之後, 安裝[mssql 延伸](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)開發 Microsoft SQL Server、 Azure SQL Database 和 SQL 資料倉儲。 |
| [組態管理員](../tools/configuration-manager/sql-server-configuration-manager-help.md) | 使用 SQL Server 組態管理員來設定 SQL Server 服務和設定網路連接性。|
| [SQL Server 移轉小幫手](../ssma/sql-server-migration-assistant.md) | 使用 SQL Server 移轉小幫手來自動化資料庫移轉至 SQL Server 從 Microsoft Access、 DB2、 MySQL、 Oracle 和 Sybase。|
| [Distributed 的 Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | 使用 Distributed Replay 功能可協助您評估未來的 SQL Server 升級的影響。 也可以使用 Distributed Replay 協助評估硬體和作業系統升級與 SQL Server 微調的影響。 |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Ssbdiagnose 公用程式會報告 Service Broker 交談中的 Service Broker 服務之組態的問題。 |


## <a name="sql-command-prompt-utilities"></a>SQL 命令提示字元公用程式

  命令提示字元公用程式可編寫 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 作業指令碼。 下表列出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]隨附的命令提示字元公用程式清單。  
  
|**公用程式**|**描述**|**安裝位置**|  
|-----------------|---------------------|----------------------|  
|[bcp 公用程式](../tools/bcp-utility.md)|在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體和使用者指定之格式的資料檔案之間，用來複製資料。|\<*磁碟機*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[dta 公用程式](../tools/dta/dta-utility.md)|用來分析工作負載和建議實體設計結構，以最佳化這項工作負載的伺服器效能。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[dtexec 公用程式](../integration-services/packages/dtexec-utility.md)|用以設定及執行 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。 此命令提示字元公用程式的使用者介面版本稱為 **DTExecUI**，它會啟動「執行封裝公用程式」。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[dtutil 公用程式](../integration-services/dtutil-utility.md)|用來管理 SSIS 封裝。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[使用部署公用程式的部署模型方案](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|用以將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的執行個體。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[mssql scripter （公開預覽）](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|用來產生 SQL Server、 Azure SQL Database 和 Azure SQL 資料倉儲中的資料庫物件的建立及插入 T-SQL 指令碼。|請參閱我們[GitHub 儲存機制](https://github.com/Microsoft/sql-xplat-cli)下載和使用方式資訊。| 
|[osql 公用程式](../tools/osql-utility.md)|可讓您在命令提示字元之下，輸入 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式、系統程序和指令碼檔案。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Profiler 公用程式](../tools/profiler-utility.md)|用來從命令提示字元啟動 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[RS.exe 公用程式 &#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|用以執行為了管理 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器而設計的指令碼。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rsconfig 公用程式 &#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|用來設定報表伺服器連接。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[rskeymgmt 公用程式 &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|用來管理報表伺服器的加密金鑰。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlagent90 應用程式](../tools/sqlagent90-application.md)|用來從命令提示字元啟動 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent。|\<磁碟機 >: SQL Server \Program Files\Microsoft\\<*instance_name*> \MSSQL\Binn|  
|[sqlcmd 公用程式](../tools/sqlcmd-utility.md)|可讓您在命令提示字元之下，輸入 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式、系統程序和指令碼檔案。|\<*磁碟機*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[SQLdiag 公用程式](../tools/sqldiag-utility.md)|用以收集可供 [!INCLUDE[msCoName](../includes/msconame-md.md)] 客戶服務與支援部門使用的診斷資訊。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqllogship 應用程式](../tools/sqllogship-application.md)|應用程式用來對記錄傳送組態執行備份、複製和還原作業以及相關的清除工作，而無須執行備份、複製和還原作業。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[SqlLocalDB 公用程式](../tools/sqllocaldb-utility.md)|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行模式，專供程式開發人員使用。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[sqlmaint 公用程式](../tools/sqlmaint-utility.md)|用來執行舊版 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]所建立的資料庫維護計畫。|\<磁碟機 >: \Program Files\Microsoft SQL Server\MSSQL13。MSSQLSERVER\MSSQL\Binn|  
|[sqlps 公用程式](../tools/sqlps-utility.md)|用來執行 PowerShell 命令和指令碼。 載入並註冊 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 提供者和 cmdlet。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlservr 應用程式](../tools/sqlservr-application.md)|用來從命令提示字元啟動和停止 [!INCLUDE[ssDE](../includes/ssde-md.md)] 執行個體，以進行疑難排解。|\<磁碟機 >: \Program Files\Microsoft SQL Server\MSSQL13。MSSQLSERVER\MSSQL\Binn|  
|[Ssms 公用程式](../tools/sql-server-management-studio/ssms-utility.md)|用來從命令提示字元啟動 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[tablediff 公用程式](../tools/tablediff-utility.md)|用來比較兩份資料表，以找出非聚合狀況，當進行複寫拓撲的疑難排解時，它尤其有用。|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>SQL 命令提示字元公用程式語法慣例  
  
|**慣例**|**用於**|  
|--------------------|------------------|  
|大寫|作業系統層級所用的陳述式和詞彙。|  
|`monospace`|命令和程式碼範例。|  
|*斜體*|使用者提供的參數。|  
|**粗體字**|必須完全依照顯示狀況來輸入的命令、參數和其他語法。|  


