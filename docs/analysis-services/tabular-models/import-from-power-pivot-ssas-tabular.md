---
title: 從 Analysis Services 中的 Power Pivot 匯入 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21abcfbec94808df6560af887ff0598d97fcb068
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072375"
---
# <a name="import-from-power-pivot"></a>從 Power Pivot 匯入 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  本文說明如何匯入中繼資料和從資料建立新的表格式模型專案[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]使用從匯入的活頁簿[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]中的專案範本[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]。  
  
## <a name="create-a-new-tabular-model-from-a-power-pivot-for-excel-file"></a>從 Power Pivot for Excel 檔案建立新的表格式模型  
 從 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿匯入來建立新的表格式模型專案時，會使用定義活頁簿結構的中繼資料來建立及定義 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中表格式模型專案的結構。 資料表、資料行、量值和關聯性等物件會保留，並以其在 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿的顯示方式出現在表格式模型專案中。 .xlsx 活頁簿檔案將不會做任何變更。  
  
> [!NOTE]  
>  表格式模型不支援連結資料表。 從包含連結資料表的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿匯入時，會將連結資料表資料視為複製/貼上的資料，並儲存在 Model.bim 檔案中。 檢視複製/貼上的資料表之屬性時，會停用 [來源資料] 屬性，並停用 [資料表] 功能表上的 [資料表屬性] 對話方塊。  
>   
>  可以加入至模型中內嵌資料的上限為 10,000 個資列列。 如果您匯入模型，以從[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]且看到錯誤，「 資料已截斷。 貼上的資料表不能包含超過 10000 個資料列 」 您應該修改[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]藉由將內嵌的資料移到另一個資料來源，例如 SQL Server 中的資料表建立模型，然後重新匯入。  
  
 根據工作空間資料庫位於與 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 相同之電腦 (本機) 的 Analysis Services 執行個體還是遠端 Analysis Services 執行個體上而有特殊考量。  
  
 如果工作空間資料庫位於本機 Analysis Services 執行個體上，您可以從 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿匯入中繼資料和資料。 中繼資料會從活頁簿複製，並用來建立表格式模型專案。 然後從活頁簿複製並儲存在專案的工作區資料庫 （複製/貼上資料除外，它會儲存在 Model.bim 檔案） 資料。  
  
 如果工作空間資料庫位於遠端 Analysis Services 執行個體上，您不能從 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel 活頁簿匯入資料。 您依然可以匯入活頁簿中繼資料；不過，這會導致指令碼在遠端 Analysis Services 執行個體上執行。 您應只從受信任的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿匯入中繼資料。 必須從資料來源連接中定義的來源匯入資料。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿中複製/貼上和連結資料表的資料必須複製及貼到表格式模型專案中。  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-power-pivot-for-excel-file"></a>若要從 Power Pivot for Excel 檔案建立新的表格式模型專案  
  
1.  在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]的 **[檔案]** 功能表上，按一下 **[新增]**，然後再按一下 **[專案]**。  
  
2.  在 [新增專案] 對話方塊的 [已安裝的範本] 下，按一下 [商務智慧]，然後按一下 **[從 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 匯入]**。  
  
3.  在 [名稱]中，輸入專案的名稱，並指定位置和方案名稱，然後按一下 [確定]。  
  
4.  在 [開啟] 對話方塊中，選取包含您要匯入之模型中繼資料和資料的 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] 檔案，然後按一下 [開啟]。  
  
## <a name="see-also"></a>另請參閱  
 [工作空間資料庫](../../analysis-services/tabular-models/workspace-database-ssas-tabular.md)   
 [複製及貼上資料](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)  
  
  
