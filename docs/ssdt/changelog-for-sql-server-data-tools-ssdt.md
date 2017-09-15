---
title: "SQL Server Data Tools (SSDT) 的變更記錄 | Microsoft Docs"
ms.custom: 
ms.date: 08/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b071f8b8-c8e5-44e0-bbb6-04804dd1863a
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 71a2cbf181c94c4c1aff877614aadf890b2496e0
ms.openlocfilehash: e4bc77e76190463864ecab75ae94e28b16624309
ms.contentlocale: zh-tw
ms.lasthandoff: 08/23/2017

---
# <a name="changelog-for-sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT) 的變更記錄
這是 [SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx) 的變更記錄。  
  
如需新功能和已變更功能的詳細文章，請參閱 [SSDT 小組部落格](https://blogs.msdn.microsoft.com/ssdt/)。

## <a name="ssdt-for-visual-studio-2017-1530-preview"></a>適用於 Visual Studio 2017 (15.3.0 預覽) 的 SSDT
組建編號︰14.0.16121.0
  
### <a name="whats-new"></a>新功能

此預覽為適用於 Visual Studio 2017 的第一個 SSDT 版本。 此版本加入了獨立式網頁安裝體驗，適用於 Visual Studio 2017 15.3 (或更新版本) 的 SQL Server Database、Analysis Services、Reporting Services 與 Integration Services 專案。


**已知問題**

- 安裝程式未當地語系化。
- SSIS 未當地語系化。
- 當 *ExecuteOutofProcess* 設定為 *True* 時，SSIS 執行封裝工作不支援偵錯。 此問題僅適用偵錯。 透過 DTExec.exe 或 SSIS 目錄進行的儲存、部署及執行則不受到影響。
- 如需變更的完整清單，請參閱[變更記錄](changelog-for-sql-server-data-tools-ssdt.md)。
- 在 [SSDT Connect 意見反應](https://connect.microsoft.com/SQLServer/Feedback)網站報告問題。
- 包含協力廠商延伸模組的 SSIS 套件無法切換，以將目標設為其他伺服器版本。


## <a name="ssdt-172-for-visual-studio-2015"></a>適用於 Visual Studio 2015 的 SSDT 17.2
組建編號︰14.0.61707.300

### <a name="whats-new"></a>新功能


**AS 專案：**
- 在 1400 相容性層級表格式模型中，現在可以在進階安全性的 [角色] 對話方塊中設定「物件層級安全性」。
- 在 VS2017 的 SSDT AS 專案中，AS Azure 模型中沒有電子郵件地址之使用者的新 AAD 角色成員選擇。
- SSDT AS 表格式專案中自訂 ADAL 認證快取行為的新 AS Azure [一律提示] 專案屬性。


### <a name="bug-fixes"></a>錯誤修正

**一般**
- SQL Server 2017 的已更新商標參考。

**AS 專案**
- 認可 DAX 量值變更和其他模型編輯時，對改善體驗所進行的大幅效能修正。
- 修正使用 1400 相容性層級表格式模型之 Analysis Services 專案中的一些 PowerQuery 整合問題。
- 修正 VS2017 的多維專案中可能無法載入設計彙總設計工具的問題。
- 修正拖曳 Analysis Services 多維 DSV 圖表中可能會讓 VS 2017 當機之項目時的問題。
- 修正 AS 專案中 [部署] 對話方塊不一定會在 Visual Studio 前景的問題。
- 因為已解除服務，所以移除從作為資料來源之 Data Marketplace 的 Analysis Services 匯入。
- 修正透過 [表格式模型檔案總管] 從現有資料來源 [匯入新資料表] 之後停用資料表設計工具的問題。
- 修正可能讓 [模型] 功能表項目 [從資料來源匯入]/[新增資料來源] 在錯誤內容中保持隱藏的問題。
- 改善從 [表格式模型檔案總管] 建立量值以避免將焦點切換回用來建立量值之資料行時的問題。
- 從 AS 表格式專案中的整合式工作區切換為明確工作空間伺服器時，會立即清除舊的資料庫檔案。
- 修正 [資料列層級安全性] 核取方塊 UI 狀態一開始顯示為未核取之 AS 表格式 1400 模型專案中的問題，而不論實際基礎物件狀態為何。
- 修正使用 Power Query 將文字檔或 Excel 檔案匯入至 1400 相容性模式表格式模型時可能發生的當機，以及擲回未處理的例外狀況。
- 修正 AS 表格式模型設計工具之 DAX 公式編輯控制項中捲軸縮圖可能發生的問題。
- 修正防止 PowerQuery 混搭資料來源在包含使用者名稱/密碼驗證時進行修改的問題。
- 修正可防止在連接字串中設定其他屬性時連接資料來源的問題。
- 修正多個 AS 表格式模型專案載入並關閉第二個模型設計工具時可能會讓 VS 當機的問題，而不需要先與設計工具中的任何項目互動。
- 修正在某些情況下持續保存對 KPI 格式化進行之編輯的問題。
- 修正顯示錯誤功能表已核取狀態指出是否顯示公式列之 PowerQuery UI 的問題。
- 修正 AS 表格式 1400 相容性層級專案中，從 [表格式模型檔案總管] 選取 [變更資料來源] 功能表時可以讓 VS 當機的 PowerQuery 資料來源問題。
- 修正載入 1400 表格式模型可能會顯示「無法載入檔案或組件 'Microsoft.ProBI.MashupLibrary'」錯誤的間歇性問題。

**RS 專案**
- 在工作階段之間，正確地記住 [RS 尺規和參數] 方塊設定選取狀態的使用者喜好設定。

**IS 專案**
- 修正未正確顯示 ADO/ADO.NET ForEachLoop 容器的問題
- 修正未當地語系化一些工作/元件/精靈的問題
- 已將最新的 *TargetServerVersion* 從 "SQL Server vNext" 變更為 "SQL Server 2017"


## <a name="ssdt-171-for-visual-studio-2015"></a>適用於 Visual Studio 2015 的 SSDT 17.1
組建編號︰14.0.61705.170

### <a name="whats-new"></a>新功能
**AS 專案：**
- 使用者可以在 1400 模型的 UI 資料行上設定編碼提示
- 非模型相關的 IntelliSense 目前可以在離線模式中使用
- [表格式模型檔案總管] 現在包含一個節點，代表模型 (1400 相容性層級表格式模型) 中可用的具名 M 運算式
- Azure Active Directory 人員選擇器類似於 Microsoft Azure 入口網站的 IAM，目前在表格式模型中設定角色成員時即可供使用

**資料庫專案：**
- 更新為 DacFx 17.1

### <a name="bug-fixes"></a>錯誤修正
- 修正在 VS2017 的 Visual Studio 選項中，商業智慧設計師群組名稱顯示不正確的問題
- 修正使用報表專案或 AS 專案產生方案的 Code Map 時，發生當機的問題
- 修正 Analysis Services 1400 相容性層級表格式模型的一些 PowerQuery 整合問題
- 修正新的 DAX 編輯器工具視窗中當定義量值時，指派運算子可能不是單獨一行的問題
- 修正在重新命名檢視方塊中的量值時，阻止更新表格式量值顯示畫面的問題
- 更新 Analysis Services 整合式工作區引擎和表格式物件模型，以修正造成包含翻譯的 1200 表格式專案在部署到 SQL Server 2016 Analysis Services 伺服器時失敗的迴歸
- 修正建立\刪除新的 1400 表格式資料來源非常緩慢的效能問題
- 修正在不同 DSV 之間快速變更速檢視時，多維模型中的 DSV 圖表無法停止呈現的問題

## <a name="dacfx-171"></a>DacFx 17.1
- 修正使用其他身分識別資料行為記憶體最佳化資料表的資料行加密的問題
- SQLDOM 支援 CREATE DATABASE 的CATALOG_COLLATION 選項

## <a name="dacfx-1701"></a>DacFx 17.0.1 
- 修正使用 HSM 的非對稱金鑰與 EKM 提供者[連接項目](https://connect.microsoft.com/SQLServer/feedback/details/3132749/sqlpackage-exe-fails-when-extracting-a-database-which-contains-an-asymmetric-key-using-an-ekm-provider) 的資料庫問題

## <a name="ssdt-170-for-visual-studio-2015-supports-up-to-sql-server-2017"></a>適用於 Visual Studio 2015 的 SSDT 17.0 (最高支援 SQL Server 2017)
組建編號：14.0.61704.140

### <a name="whats-new"></a>新功能
**資料庫專案：**
- 修改檢視上的叢集索引不會再封鎖部署
- 與資料行加密相關的結構描述比較字串會使用專有名稱，而不是執行個體名稱。   
- 新增命令列選項到 SqlPackage：ModelFilePath。  這可讓進階使用者選擇針對匯入、發佈和指令碼作業指定外部 model.xml 檔案   
- DacFx API 已擴充為支援 Azure AD 通用驗證和 Multi-Factor Authentication (MFA)

**IS 專案：**
- SSIS OData 來源和 OData 連線管理員現在支援連線到 Microsoft Dynamics AX Online 和 Microsoft Dynamics CRM Online 的 OData 摘要。
- SSIS 專案現在支援 "SQL Server 2017" 的目標伺服器版本 
- 以 SQL Server 2017 為目標時，支援 CDC 控制工作、CDC 分隔器和 CDC 來源。 

**AS 專案：**
- Analysis Services PowerQuery 整合 (1400 相容性層級表格式模型)：
    - 如果使用者已安裝協力廠商驅動程式，則 DirectQuery 適用於 SQL Oracle 和 Teradata
    - 在 PowerQuery 中透過範例新增資料行
    - 1400 模型 (M 引擎所使用的模型層級屬性) 中的資料存取選項
        - 啟用快速合併 (預設值為 false - 設定為 true 時，交互式 Web 應用程式引擎會在合併資料時忽略資料來源的隱私權等級)
        - 啟用舊版重新導向 (預設值為 false – 設為 true 時，交互式 Web 應用程式引擎會遵循可能不安全的 HTTP 重新導向。  例如，從 HTTPS 至 HTTP URI 的重新導向)  
        - 以 Null 傳回錯誤值 (預設值為 false – 設為 true 時，資料格層級的錯誤會以 null 傳回。 設為 false 時，將引發的例外狀況是資料格包含錯誤)  
    - 使用 PowerQuery 的額外資料來源 (檔案資料來源)
        - Excel 
        - 文字/CSV 
        - XML 
        - Json 
        - 資料夾 
        - Access 資料庫 
        - Azure Blob 儲存體 
    - 當地語系化的 PowerQuery 使用者介面
- DAX 編輯器工具視窗
    - 改善量值、導出資料行和詳細資料列運算式的 DAX 編輯體驗，可透過 SSDT 中的 [檢視]、其他 Windows 功能表存取
    - DAX 部析器\Intellisense 的增強功能


**RS 專案︰**
- 可內嵌的 RVC Control 現在可支援 SSRS 2016

### <a name="bug-fixes"></a>錯誤修正
**AS 專案：**
- 修正 BI 專案的範本優先順序，使它們不會顯示在 VS 的 [新專案] 類別頂端
- 修正開啟 SSIS、SSAS 或 SSRS 方案時 VS 可能會當機的罕見問題
- 表格式：DAX 剖析和資料編輯列的各種功能增強及效能修正。
- 表格式：如果未開啟任何 SSAS Tabular 專案，Tabular Model Explorer 就不會再顯示。
- 多維度：修正處理對話方塊在高 DPI 機器上無法使用的問題。
- 表格式：修正 SSDT 會在 SSMS 已開啟的情況下開啟任何 BI 專案時發生錯誤的問題。[Connect 項目](http://connect.microsoft.com/SQLServer/feedback/details/3100900/ssdt-faults-when-opening-any-bi-project-when-ssms-is-already-open)
- 表格式：修正階層未正確儲存到 1103 模型中 BIM 檔案的問題。[Connect 項目](http://connect.microsoft.com/SQLServer/feedback/details/3105222/vs-2015-ssdt)
- 表格式：修正即使不支援，但在 32 位元機器上仍允許整合式工作區模式的問題。
- 表格式：修正在半選取模式 (例如鍵入 DAX 運算式但按下量值) 下按一下任何項目都會造成損毀的問題。
- 表格式：修正部署精靈會將模型的 .Name 屬性重設回 "Model" 的問題。 [Connect 項目](http://connect.microsoft.com/SQLServer/feedback/details/3107018/ssas-deployment-wizard-resets-modelname-to-model)
- 表格式：修正即使未選取圖表檢視，在 TME 中選取階層也應顯示屬性的問題。
- 表格式：修正從特定應用程式貼入 DAX 資料編輯列時會貼上影像或其他內容，而非文字的問題。
- 表格式：修正 1103 中有些舊模型因為具有特定定義的量值存在而無法開啟的問題。
- 表格式：修正無法刪除 XEvent 工作階段的問題。
- 修正嘗試使用 devenv.com 建置 AS “smproj” 檔案會失敗的問題
- 修正在 AS 表格式模型工作表索引標籤標題中使用韓文輸入法時，會太頻繁地完成文字變更的問題
- 修正 DAX Related() 函數的 IntelliSense 無法正確顯示其他資料表之資料行的問題
- 透過針對 AS 資料庫清單進行排序，改進從資料庫對話方塊的 AS 表格式專案匯入
- 修正在 AS 表格式模型中建立導出資料表時，Tables 在陳述式中沒有列為建議物件的問題
- 修正預覽 1400 AS 模型在檢視程式碼之後嘗試使用整合式工作空間伺服器開啟的問題
- 修正在某些情況下防止 (不具有初始目錄支援的) 資料來源正常運作的問題 
- 部署精靈應該將變更套用到導出資料表分割區，即使已啟用保持分割區的選項也一樣
- 修正現有 AS 連線的 [進階屬性] 對話方塊要在重新選取後才會顯示完整清單的問題
- 修正一些裁剪的 UI 字串出現在某些當地語系化組建的問題
- 修正 1400 相容性層級 AS 表格式模型的一些 PowerQuery 整合問題
- 修正報表精靈樣式範本未正確顯示的問題
- 修正報表精靈在從 SQL 變更為 AS 時，可能會導致資料來源設定不正確的問題
- 修正導致從命令列 (devenv.com\exe) 執行 Analysis Services (表格式) 專案組建失敗的問題
- 修正 DAX 量值剖析器在以之前字母開頭時，要反白顯示並顯示正確的文字色彩的問題: =
- 修正路徑嘗試在整合式工作區模式下顯示表格式專案的所有檔案時，花費太長時間而觸發 ObjectRefException 的問題
- 修正 Compact 4.0 用戶端資料提供者的資料來源設計師無法使用的問題
- 修正嘗試在 VS2017 中瀏覽 AS 採礦模型時造成錯誤的問題
- 修正 VS2017 中 DSV 圖表在變更檢視之後停止轉譯，然後觸發例外狀況的 AS 多維模型問題
- 修正在 VS2017 中使用 AS 連線預覽報表失敗的問題
 

**RS 專案︰**
- 修正在 SSDT 中設計報表時，參數、資料來源及資料集的樹狀檢視會在做出大多數變更時折疊的問題 
- 修正 [儲存] 應儲存 RDL 版本而非最新版本的問題。
- 修正 SSDT RS 在備份關閉時仍備份檔案的問題，及其他數個問題。
- 修正報表產生器中，在按一下 [分割儲存格] 時會顯示錯誤的問題。 [Connect 項目](http://connect.microsoft.com/SQLServer/feedback/details/3101818/ssdt-2015-ssrs-designer-error-by-matrix-cell-split)
- 修正快取可能造成報表中資料不正確的問題。 [Connect 項目](http://connect.microsoft.com/SQLServer/feedback/details/3102158/ssdtbi-14-0-60812-report-preview-data-is-frequently-wrong-due-to-bad-caching)

**IS 專案：**
- 修正 run64bitruntime 設定無法固定的問題。
- 修正 DataViewer 不會儲存顯示的資料行的問題。
- 修正套件組件會隱藏註解的問題。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3106624/package-parts-hide-annotations)
- 修正套件組件會捨棄 [資料流程] 配置及註解的問題。 [Connect 項目](https://connect.microsoft.com/SQLServer/feedback/details/3109241/package-parts-discard-data-flow-layouts-and-annotations)
- 修正 SSDT 在從 SQL Server 匯入專案時損毀的問題。
- 修正在開啟已儲存的 SSIS 封裝之後以及執行階段時，Hadoop 檔案系統工作 TimeoutInMinutes 預設為 10 的問題。

**資料庫專案：**
- SSDT DACPAC 部署將設定加回 IgnoreColumnOrder [Connect 項目 (英文)](https://connect.microsoft.com/SQLServer/feedback/details/1221587/ssdt-dacpac-deploy-add-setting-back-in-for-ignorecolumnorder)
- 如果使用 STRING_SPLIT，SSDT 就無法編譯 [Connect 項目 (英文)](http://connect.microsoft.com/SQLServer/feedback/details/2906200/ssdt-failing-to-compile-if-string-split-is-used)
- 修正 DeploymentContributors 可以存取公開模型，但支援結構描述未初始化的問題 [Github 問題 (英文)](https://github.com/Microsoft/DACExtensions/issues/8)
- FILEGROUP 位置的 DacFx 暫時修正
- 外部同義字的「無法解析的參考」錯誤修正。 
- Always Encrypted：線上加密在取消時不會停用變更追蹤，且如果開始加密之前沒有清理變更追蹤，線上加密便無法正常運作


## <a name="ssdt-165-for-visual-studio-2015-supports-up-to-sql-server-2016"></a>適用於 Visual Studio 2015 的 SSDT 16.5 (最高支援 SQL Server 2016)
發行日期︰2016 年 10 月 20 日

組建編號：14.0.61021.0

**新功能**


### <a name="connection-improvements"></a>連線功能改進

* 在 [瀏覽] 索引標籤中的新搜尋方塊可協助您篩選您的本機伺服器、網路伺服器和 Azure SQL 資料庫。 如果您有大量伺服器或資料庫出現在這些清單中，此功能非常有用。
* [歷程記錄] 索引標籤有右鍵功能表選項可釘選/取消釘選 [我的最愛]，還有新選項可從歷程記錄移除連線。

### <a name="sqlpackage-and-dacfx-api-improvements"></a>SqlPackage 和 DacFx API 功能改進

您現在可以使用 SqlPackage.exe 和 DacFx API，只以一個動作就能產生部署報表、部署指令碼，並發行至資料庫。 這對於想要保留部署期間發行內容報表的任何人來說非常節省時間。 另一個好處是在 Azure 的案例中，會針對主要資料庫與部署目標資料庫建立不同的指令碼。 在此之前只會建立單一指令碼，對於重複的部署不是很有用。

針對 SqlPackage 的 Publish 和 Script 動作，加入兩個新的引數。

* DeployScriptPath (簡短名稱︰dsp)。 這是要撰寫部署指令碼的選擇性路徑。 對於 Azure 部署，如果有 TSQL 命令要建立或修改資料庫，將會對主要指令碼寫入相同的路徑，但會使用 “Filename_Master.sql” 做為輸出檔案名稱。
* DeployReportPath (簡短名稱︰drp)。 這是要撰寫部署報表的選擇性路徑。

請注意，Script 動作應使用現有的「輸出路徑」引數或新的指令碼/報表特定引數，但不是同時使用兩者。

範例使用方式︰

**Publish 動作**

```Sqlpackage.exe /a:Publish /tsn:(localdb)\ProjectsV13 /tdn:MyDatabase /deployscriptpath:”My\DeployScript.sql” /deployreportpath:”My\DeployReport.xml”```

**Script 動作**

```Sqlpackage.exe /a:Script /tsn:(localdb)\ProjectsV13 /tdn:MyDatabase /deployscriptpath:”My\DeployScript.sql” /deployreportpath:”My\DeployReport.xml”```

DacFx 中已加入兩個新的 API：DacServices.Publish() 和 DacServices.Script()。 這些 API 也支援在單一作業中執行發行 + 編寫指令碼 + 報告的動作。 範例使用方式︰

```
DacServices service = new DacServices(connectionString);
using(DacPackage package = DacPackage.Load(@"C:\My\db.dacpac")) {
var options = new PublishOptions() {
    GenerateDeploymentScript = true, // Should a deployment script be created?
    GenerateDeploymentReport = true, // Should an xml deploy report be created?
    DatabaseScriptPath = @"C:\My\OutputScript.sql", // optional path to save script to
    MasterDbScriptPath = @"C:\My\OutputScript_Master.sql", // optional path to save master script to
    DeployOptions = new DacDeployOptions()
};

// Call publish and receive deployment script & report in the results
PublishResult result = service.Publish(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);

// Call script and receive deployment script & report in results
result = service.Script(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);
```

**Analysis Services 與 Reporting Services**

使用大型 DAX 運算式時，SSAS 表格式設計工具 DAX 剖析器已經改善效能。
如需詳細資訊，請參閱 [Analysis Services 部落格文章 (英文)](https://blogs.msdn.microsoft.com/analysisservices/2016/09/20/introducing-integrated-workspace-mode-for-sql-server-data-tools-for-analysis-services-tabular-projects-ssdt-tabular/)。

### <a name="fixed--improved-this-month"></a>本月份修正/改進內容

**資料庫工具**

* [連接錯誤 3055711](https://connect.microsoft.com/SQLServer/feedback/details/3055711/columns-cannot-be-selected-from-cross-apply-openjson-with-explicit-schema) – Columns cannot be selected from CROSS APPLY OPENJSON with explicit schema (無法從有明確結構描述的 CROSS APPLY OPENJSON 選取資料行)
* 已修正 - 在自動產生的歷程記錄資料表索引中，DacFx 在重新部署時會卸除索引的問題
* 已修正 - DacFx 批次剖析器未剖析逸出括號 ']' 字元而導致發行失敗的問題
* 已改進 - SqlPackage 現在在說明輸出中會包含每個動作的描述
* 已修正 - 編輯進階選項時，以及編輯「發行」、「結構描述比較」和其他檔案中儲存的連接字串時，沒有保留 [連接] 對話方塊的 [記住密碼] 選項
* 已修正 - 對於在 [歷程記錄] 索引標籤中 IntegratedAuthentication=true 所顯示的連接，連接屬性中的 [驗證] 欄位為空白。 現在這會如預期般顯示「Windows 驗證」
* 已修正 - 沒有保留 [工具] -> [選項] -> [文字編輯器] 下對 SQL Server 工具 Intellisense 設定的變更
* 已改進 - [連接] 對話方塊的 [歷程記錄] 索引標籤中的 [釘選]/[取消釘選] 按鈕現在更緊密，降低捲軸出現的可能性
* 已修正 - 已修正 [連接] 對話方塊中幾個協助工具問題。

**Analysis Services 與 Reporting Services**

* 已修正在某些情況下在 SSDT AS 表格式設計工具中按一下資料格中的捲軸指標會當機的問題
* 已修正沒有選項可將連線模擬為 SSDT AS 表格式中目前使用者的問題
* 已修正在 SSDT AS 表格式設計工具中將公式列展開太遠而無法重新開啟專案的問題
* 已修正在 SSDT AS 表格式設計工具中若已選取資料表索引標籤，按向下鍵可能會發生當機的問題
* 已修正在 SSDT AS 專案中 [在 Excel 中進行分析] 不會連線至下層 AS 伺服器版本的問題

**整合服務**

* 已修正連接錯誤 [1608896](https://connect.microsoft.com/SQLServer/feedback/details/1608896/move-multiple-integration-service-package-tasks)︰Move Multiple Integration Service Package Tasks (移動多個整合服務封裝工作)





## <a name="ssdt-164-for-visual-studio-2015-for-sql-server-2016"></a>適用於 Visual Studio 2015 的 SSDT 16.4 (適用於 SQL Server 2016)
發行日期︰2016 年 9 月 20 日

組建編號：14.0.60918

**新功能**

SqlPackage.exe 和 Data-Tier Application Framework (DacFx) API 現在支援結構描述比較。 如需詳細資訊，請參閱 [SqlPackage 和 Data-Tier Application Framework 中的結構描述比較 (英文)](https://blogs.msdn.microsoft.com/ssdt/2016/09/20/schema-compare-in-sqlpackage-and-the-data-tier-application-framework-dacfx/)。

**Analysis Services - SSDT 表格式 (SSAS) 的整合式工作區模式**

SSDT 表格式現在包含內部的 SSAS 執行個體，若啟用整合式工作區模式，則 SSDT 表格式會自動在背景啟動此執行個體，讓您可以在模型設計師中新增及檢視資料表、資料行和資料，無需提供外部工作區伺服器執行個體。 整合式工作區模式不會變更 SSDT 表格式與工作區伺服器及資料庫搭配運作的方式。 變更之處在於 SSDT 表格式裝載工作區資料庫的位置。 若要啟用整合式工作區模式，請在建立新的表格式專案時顯示的 [表格式模型設計師] 對話方塊中選取 [整合式工作區] 選項。 對於目前使用明確工作區伺服器的現有表格式專案，您可以在於 [方案總管] 中選取 Model.bim 檔案時顯示的 [屬性] 視窗中將 [整合式工作區模式] 參數設定為 True，切換到整合式工作區模式。 如需詳細資訊，請參閱 [Analysis Services 部落格文章 (英文)](https://blogs.msdn.microsoft.com/analysisservices/2016/09/20/introducing-integrated-workspace-mode-for-sql-server-data-tools-for-analysis-services-tabular-projects-ssdt-tabular/)。

**更新和修正**
**資料庫工具︰**

- [連接問題 3087775](https://connect.microsoft.com/SQLServer/feedback/details/3087775)︰Temporal tables broken in VS Data Tools July update 14.0.60629.0, "Value cannot be null. Parameter name: reportedElement" (VS 資料工具 7 月更新 14.0.60629.0 中的時態表損毀，「值不可以是 Null。參數名稱：reportedElement」)
- [連接問題 1026648](https://connect.microsoft.com/SQLServer/feedback/details/1026648)：IsPersistedNullable shows as different in SSDT Comparison (IsPersistedNullable 在 SSDT 比較中顯示為不同)
- [連接問題 2054735](https://connect.microsoft.com/SQLServer/feedback/details/2054735)︰Identity is reset when importing a BACPAC (匯入 BACPAC 時會重設識別)
- [連接問題 2900167](https://connect.microsoft.com/SQLServer/feedback/details/2900167)︰Running SSDT unit tests leaves temp files behind (執行 SSDT 單元測試留下暫存檔案)
- [連接問題 1807712](https://connect.microsoft.com/SQLServer/feedback/details/1807712)︰Backwards compatibility breakage – AppLocal and Nugetization (回溯相容性損毀 - AppLocal 和 Nugetization)

**Analysis Services 與 Reporting Services**

* 已修正在 SSDT 中當編輯 DirectQuery 導出資料行的 DAX 時會出現錯誤提示快顯視窗的問題。
* 已修正在 SSDT AS 表格式方格中當 Windows 縮放比例設定在高 DPI 200%+ 時，KPI 圖示未顯示在量值方格中中的問題。
* 已修正在 SSDT AS 中貼上大型資料表資料可能會讓表格式專案沒有回應的問題。
* 已修正在 SSDT AS 表格式模型編輯器中重新命名連線的易記名稱時，將模型標示為必須儲存變更的問題。
* 已修正在 SSDT AS 表格式專案中 [管理關聯性] 對話方塊中的資料行寬度無法調整大小的問題。
* 已修正在 SSDT AS 表格式 1200 層級的模型中，若地區設定為例如德文，從 Excel 貼上資料沒有正確將逗號視為小數分隔符號的問題。
* 已修正在設定某些 KPI 圖示集的 SSDT AS 專案中可能會產生「無法擷取此視覺物件的資料」錯誤的問題。
* 已修正 SSDT AS 專案屬性對話方塊在高 DPI 縮放比例調整大小時正確錨定的問題。
* 已修正在 SSDT AS 專案中升級內含貼上的資料表的特定模型時可能會造成錯誤的問題。
* 已修正在 SSDT AS 中從 Excel 貼上整個工作表資料列非常緩慢且建立許多不必要資料行的問題。
* 已修正在 SSDT AS 中大型靜態 DataTable 運算式的剖析和反白顯示非常緩慢或似乎停止回應的問題。
* 已修正在 SSDT AS 中將量值和 KPI 值新增至編輯器中目前所選檢視方塊的問題。
* 已修正在 SSDT 中從 SQL Azure 匯入 AS 專案的資料不支援除了 "dbo" 以外之結構描述類型的問題。



## <a name="ssdt-163-for-visual-studio-2015-for-sql-server-2016"></a>適用於 Visual Studio 2015 的 SSDT 16.3 (適用於 SQL Server 2016)
發行日期︰2016 年 8 月 15 日

組建編號：14.0.60812.0  

**新功能**

- **發行版本控制與編號︰**發行版本現在以數值標記而不是依月份標記。 這與新的 SSMS 原則一致，並簡化在一個月中有多個版本或 hotfix 時的情況。 此版本是 16.3，表示在 RTM 版本之後的第三個更新。 任何 hotfix 將是 16.3.1，依此類推，下一個更新 (下個月的計劃) 將是 16.4。
- **Analysis Services - 表格式模型總管：**表格式模型總管可讓您在模型中方便瀏覽各種中繼資料物件，例如資料來源、資料表、量值和關聯性。 它會實作為獨立的工具視窗，您可以在 Visual Studio 中開啟 [檢視] 功能表，指向 [其他視窗]，然後按一下 [表格式模型總管] 來顯示。 表格式模型總管預設會出現在方案總管區域的另一個索引標籤上。表格式模型總管會將中繼資料物件組織在與表格式 1200 模型結構描述十分類似的樹狀結構中，而且有更多新功能。
- **資料庫工具 - Always Encrypted**︰此版本提供新的[Always Encrypted 金鑰管理](https://msdn.microsoft.com/library/mt708953.aspx)對話方塊，可輕鬆地將資料行主要金鑰或資料行加密金鑰加入至資料庫專案或 SQL Server 物件總管中的即時資料庫。 此版本支援 Windows 憑證存放區中的憑證。 未來的版本將會支援 Azure 金鑰保存庫和 CNG 提供者。
    - 在建立資料行主要金鑰或資料行加密金鑰時，您可能會發現按一下 [更新資料庫] 之後，SQL Server 物件總管無法立即反映所做的變更。 若要解決這個問題，請重新整理 SQL Server 物件總管中的資料庫節點。
    - 如果您嘗試加密的資料表資料行含有來自 SQL Server 物件總管的資料，您可能會失敗。 目前只有在 SSDT 資料庫專案和 SSMS 中才支援這項功能。 未來版本中將會支援 SQL Server 物件總管。


**更新和修正**
* **資料庫工具︰**
    - **SSDT：**
        - 連接錯誤 1898001 [已修正資料行描述 128 個字元限制的問題](https://connect.microsoft.com/SQLServer/feedback/details/1898001/column-description-limited-to-128-characters)。
        - 已修正從 VS 發行資料庫並未在發行設定檔 xml 中套用 DatabaseServiceObjective 屬性的問題。
        - 連接錯誤 2900167 [已修正不正確保留暫存檔的單元測試問題](http://connect.microsoft.com/SQLServer/feedback/details/2900167/running-ssdt-unit-tests-leaves-temp-files-behind)。
        - 已修正 [資料庫設定] 的 [保留週期] 下拉式方塊被截斷的問題。
        - 已修正變更密碼時遺漏在 SQL CLR 專案屬性上驗證空白舊密碼的問題。
    - **DACFx：**
        - 已修正未針對 SqlAzureV12 錯誤更新 DACFx 相容性層級的問題。
        - 已修正不正確地從模型比較排除 IsAutoGeneratedHistoryTable 屬性的問題。

- **Analysis Services 與 Reporting Services**
    - **SSDT：**
        - 已修正伺服器連線中斷時，無法儲存表格式模型的問題。
        - 已修正 SSDT 因為 AS 中可能存在的無限迴圈問題而變成沒有回應的問題。
        - 已修正根據您如何認可運算式而造成不一致行為的 DAX 運算式問題。
        - 已修正建立 KPI 時的 VS 當機問題。
        - 已修正為 SQL Server 2008 R2、2012 和 2014 產生無效報表的問題。
        - 修正造成 .dwpro 專案無限迴圈錯誤的階層順序問題。
        - 已修正降級 RDL 需要完整重建而造成使用者混淆的 RS RDL 問題。
        - 已修正「在用戶端工具中隱藏」沒有作用的 KPI 問題。
        

 
  
## <a name="ssdt-july-for-visual-studio-2015-for-sql-server-2016"></a>適用於 Visual Studio 2015 的 SSDT 7 月 (適用於 SQL Server 2016)  
發行日期︰2016 年 6 月 30 日  
  
組建編號︰14.0.60629.0  
  
**新功能**  
* **Always Encrypted 支援︰**對於包含 Always Encrypted 資料行的資料庫，此版本透過我們的核心 API 和命令列工具 (SqlPackage.exe) 加入 Always Encrypted 的完整支援。 您可以利用所有完整支援的 Always Encrypted 功能，建置及發行資料庫專案。  
* **時態表增強支援︰**透過在改變之前取消連結時態表，然後在完成之後再重新連結來簡化體驗。 這表示時態表在支援的作業方面有其他資料表類型 (標準、記憶體內部) 的同位。 
* **SqlPackage.exe 和安裝變更︰**從 SQL Server 引擎隔離出 SSDT 的變更以及 SSMS 更新。 如需詳細資訊，請參閱 [SSDT 和 SqlPackage.exe 安裝和更新的變更 (英文)](https://blogs.msdn.microsoft.com/ssdt/2016/06/30/changes-to-ssdt-and-sqlpackage-exe-installation-and-updates/)。

 

**更新和修正**
* **資料庫工具︰**
    * 從現在起，SSDT 將永遠不會停用資料庫的「透明資料加密」(TDE)。 先前因為停用專案資料庫設定中的預設加密選項，所以會關閉加密。 透過此修正可啟用加密，但在發行期間永遠不會停用。 
    * 增加初始連線期間 Azure SQL DB 連線的重試計數和復原能力。
    * 如果預設檔案群組不是 PRIMARY，匯入/發行至 Azure V12 將會失敗。 現在發行時會忽略此設定。
    * 已修正當匯出的資料庫含有啟用「引號識別項」的物件時，匯出驗證可能會在某些情況下失敗的問題。
    * 已修正在建立 Hekaton 資料表時不正確加入 TEXTIMAGE_ON 選項的問題，這是不允許的動作。
    * 已修正匯出在資料階段完成之後因為寫入 model.xml 檔案而花費很長的時間匯出大量資料，造成要重新寫入 .bacpac 檔案內容的問題。
    * 已修正使用者未出現在 Azure SQL DW 和 APS 連線之 [安全性] 資料夾的問題。


 * **Analysis Services 與 Reporting Services：**
    * 已修正 MSOLAP OLEDB 提供者中只安裝 32 位元提供者，影響連線到 SQL Server 2014 的 64 位元 Excel 2016 的 SxS 問題 (未重現在從 Office365 的 ClickOnce 安裝，只重現在 MSI Excel 安裝)。
    * 修正將含有貼上資料表的 AS 模型從 1103 升級為 1200 相容性層級 (可能產生「關聯性使用無效資料行識別碼」錯誤) 時，要讓極端案例 (corner case) 更健全的問題。
    * 已修正當 SSDT-BI 2013 位於相同電腦上，解除安裝 SSDT 2015 之後可能無法再匯入 AS 模型中資料的 SxS 問題 (墨水匣共用登錄設定)。
    * 已改進當 AS 引擎的連線中斷 (亦即 SSDT 整夜開啟並回收 AS 伺服器，或連線暫時中斷的其他情況) 時解決問題/當機的穩固性。 
    * 已修正在多重監視器案例中，在不同於 VS 的螢幕上開啟對話方塊的問題。 
    * 已修正/啟用在 AS 模型貼上的資料表中從 HTML 資料表 (方格資料) 貼上的支援。 
    * 已修正升級無法將空白的貼上資料表升級為 1200 (只用來做為量值的容器資料表) 的問題。 
    * 已修正將含有貼上資料表的 AS 表格式模型升級為 1200 以使用 CalcTables (用於 1200 中的貼上資料表) 解決 AS 引擎問題，以便在升級之後直接對新的導出資料表執行處理序的問題。 
    * 已修正使用不完整的 DAX 運算式取消建立新的 AS 1200 模型導出資料表可能會當機的問題。 
    * 已修正當資料庫名稱和資料表名稱相同時，從 AS 伺服器將 1200 模型匯入至 SSDT AS 專案的問題。 
    * 已修正在 1103 表格式模型中編輯 KPI 量值的問題。 
    * 已修正在 AS 1200 模型的方格中貼上 KPI 量值時發生物件參考未設定的例外狀況。 
    * 已修正無法從 1200 模型中的圖表檢視刪除導出資料表中資料行的問題。 
    * 已修正在程式碼檢視中檢視 model.bim 專案檔屬性時發生物件參考未設定的例外狀況。 
    * 已修正將資料貼上 AS 模型方格以建立貼上的資料表會使用逗點做為小數點分隔符號在國際地區設定產生不正確值的問題。 
    * 已修正在 SSDT 中開啟 2008 RS 專案並選擇不升級的問題。 
    * 修正使用資料行類型的預設格式化允許從 UI 變更格式化類型時，在 1200 相容性層級模型的導出資料表 UI 中的問題。 
    

## <a name="ssdt-june-for-visual-studio-2015-for-sql-server-2016"></a>適用於 Visual Studio 2015 的 SSDT 6 月 (適用於 SQL Server 2016)  
發行日期︰2016 年 6 月 1 日  
  
組建編號︰14.0.60525.0 

SSDT 公開上市 (GA) 現在已發行。 2016 年 6 月的 SSDT GA 更新加入 SQL Server 2016 RTM 之最新更新的支援，和各種錯誤 (bug) 修正。 如需詳細資訊，請參閱 [2016 年 6 月的 SQL Server Data Tools GA 更新 (英文)](https://blogs.msdn.microsoft.com/ssdt/2016/06/01/sql-server-data-tools-ga-update-for-june-2016/)。

  
  
## <a name="additional-resources"></a>其他資源
  
[下載 SQL Server Data Tools &#40;SSDT&#41;](../ssdt/download-sql-server-data-tools-ssdt.md)  
[舊版的 SQL Server Data Tools (SSDT 和 SSDT-BI)](../ssdt/previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md)  
[Database Engine 的新功能](https://msdn.microsoft.com/library/bb510411.aspx)  
[Analysis Services 的新功能](https://msdn.microsoft.com/library/bb522628.aspx)  
[Integration Services 的新功能](https://msdn.microsoft.com/library/bb522534.aspx)  
  
