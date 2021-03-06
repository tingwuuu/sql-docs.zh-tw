---
title: 分葉成員暫存資料表 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members staging table [Master Data Services]
- database [Master Data Services], members staging table
ms.assetid: a8c953da-ec20-47dc-8656-ed5f0dfed89b
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 24e6d55dda51e663247a3a54900004b2e18f24ae
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52751000"
---
# <a name="leaf-member-staging-table-master-data-services"></a>分葉成員暫存資料表 (Master Data Services)
  使用 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中的分頁成員暫存資料表 (stg.name_Leaf) 建立、更新、停用以及刪除分葉成員。 您也可以用它來更新分葉成員的屬性值。  
  
##  <a name="TableColumns"></a> 資料表資料行  
 下表說明分葉暫存資料表中各欄位的用途。  
  
|資料行名稱|描述|  
|-----------------|-----------------|  
|**ID**|自動指派的識別碼。 請勿在此欄位中輸入值。 如果尚未處理批次，這個欄位是空白。|  
|**ImportType**<br /><br /> 必要項|下列**識別碼**值會決定暫存的資料符合已存在於資料時該怎麼辦[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]資料庫：<br /><br /> **0**:建立新的成員。 將現有的 MDS 資料取代為暫存資料，但唯有在暫存資料不是 NULL 的情況下。 系統會忽略 NULL 值。 若要將字串屬性值變更為 NULL，請將它設定為 **~NULL~**。 若要將數字屬性值變更為 NULL，請將它設定為 **-98765432101234567890**。 若要將日期時間屬性值變更為 NULL，請將它設定為 **5555-11-22T12:34:56**。<br /><br /> **1**:建立新的成員。 對現有 MDS 資料的任何更新都將失敗。<br /><br /> **2**:建立新的成員。 將現有的 MDS 資料取代為暫存資料。 如果您匯入 NULL 值，它們會覆寫現有的 MDS 值。<br /><br /> **3**:停用成員，根據程式碼的值。 將會維護所有屬性、階層和集合成員資格，以及交易，但已無法在使用者介面中使用。 如果成員當做另一個成員的網域屬性值使用，則停用將會失敗。 如需替代方法，請參閱 **ImportType5**。<br /><br /> **4**:永久刪除成員，根據程式碼的值。 將會永久刪除所有屬性、階層和集合成員資格，以及交易。 如果成員當做另一個成員的網域屬性值使用，則刪除將會失敗。 如需替代方法，請參閱 **ImportType6**。<br /><br /> **5**:停用成員，根據**程式碼**值。 將會維護所有屬性、階層和集合成員資格，以及交易，但已無法在使用者介面中使用。 如果成員當做其他成員的網域屬性值使用，則相關的值將會設為 NULL。 ImportType 5 僅適用於分葉成員。<br /><br /> **6**:永久刪除成員，根據**程式碼**值。 將會永久刪除所有屬性、階層和集合成員資格，以及交易。 如果成員當做其他成員的網域屬性值使用，則相關的值將會設為 NULL。 ImportType 6 僅適用於分葉成員。|  
|**ImportStatus_ID**<br /><br /> 必要項|匯入程序的狀態。 可能的值為：<br /><br /> **0**：您用來指定記錄已備妥，可供暫存。<br /><br /> **1**：自動指派，表示記錄的暫存處理序已成功。<br /><br /> **2**：自動指派，表示記錄的暫存處理序已失敗。|  
|**Batch_ID**<br /><br /> 只有 Web 服務需要|自動指派的識別碼，可用來將暫存的記錄分組。 批次中的所有成員都會被指派這個識別碼，這個識別碼會顯示在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者介面的 **[識別碼]** 欄中。<br /><br /> 如果尚未處理批次，這個欄位是空白。|  
|**BatchTag**<br /><br /> 必要項，只有 Web 服務不需要|批次的唯一名稱 (最多 50 個字元)。|  
|**ErrorCode**|顯示錯誤碼。 若要查詢 **ImportStatus_ID** 為 **2**的所有記錄，請參閱 [暫存處理序錯誤 &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)。|  
|**[字碼]**<br /><br /> 必要項，除非程式碼自動為 **ImportType1** 或 **2** 產生。如需詳細資訊，請參閱[自動建立代碼 &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)。|成員的唯一代碼。|  
|**名稱**<br /><br /> 選擇性|成員的名稱。|  
|**NewCode**|唯有在您要變更成員代碼時才使用。|  
|\<屬性名稱>|實體中的每個屬性都有一個資料行存在。 將其搭配 **ImportType** **0** 或 **2**使用。 對於自由格式屬性，指定屬性的新文字或字串值。 對於網域屬性，指定將成為屬性之成員的代碼。 對於連結屬性，URL 開頭必須是 **http://**。<br /><br /> 注意：您無法暫存檔案屬性。|  
  
##  <a name="feedback"></a> 沒有 這篇文章會協助您？ 我們洗耳恭聽  
 您要尋找哪些資訊？找到了嗎？ 我們會聆聽您的意見反應來改進內容。 請將您的意見傳送到 [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Leaf%20Member%20Staging%20Table%20page)  
  
## <a name="see-also"></a>另請參閱  
 [載入或更新 Master Data Services 中的成員，使用暫存處理序](/sql/2014/master-data-services/add-update-and-delete-data-master-data-services)   
 [資料匯入&#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [檢視暫存處理序期間發生的錯誤&#40;Master Data Services&#41;](view-errors-that-occur-during-staging-master-data-services.md)   
 [暫存處理序錯誤 &#40;Master Data Services&#41;](staging-process-errors-master-data-services.md)  
  
  
