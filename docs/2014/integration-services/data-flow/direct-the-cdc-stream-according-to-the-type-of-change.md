---
title: 依據變更類型來導向 CDC 資料流 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2ee2b3238a66000546619815a886fc6017c51fe6
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58377266"
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a>依據變更類型來導向 CDC 資料流
  若要加入及設定 CDC 分隔器轉換，封裝至少必須包含一個資料流程工作及一個 CDC 來源。  
  
 加入至封裝的 CDC 來源必須已選取 NetCDC 處理模式。 如需選取處理模式的詳細資訊，請參閱 [CDC 來源編輯器 &#40;連線管理員頁面&#41;](../cdc-source-editor-connection-manager-page.md)。  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a>若要依據變更類型來導向 CDC 資料流  
  
1.  在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 專案。  
  
2.  在 [方案總管] 中，按兩下封裝加以開啟。  
  
3.  按一下 **[資料流程]** 索引標籤，然後將 CDC 分隔器從 **[工具箱]** 拖曳到設計介面。  
  
4.  將封裝中包含的 CDC 來源連接到 CDC 分隔器。  
  
5.  將 CDC 分隔器連接到一個或多個目的地。 您最多可以連接到三個不同的輸出。  
  
6.  選取下列其中一個輸出：  
  
    -   刪除輸出：導向 DELETE 變更資料列的輸出。  
  
    -   插入輸出：導向 INSERT 變更資料列的輸出。  
  
    -   更新輸出：變更的輸出前/後更新變更資料列和合併資料列會被導向。  
  
7.  (選擇性) 您可以使用 **[進階編輯器]** 對話方塊來設定進階屬性。  
  
     **[進階編輯器]** 對話方塊包含可以程式設計方式設定的屬性。  
  
     若要開啟 **[進階編輯器]** 對話方塊：  
  
    -   在 **專案的** [資料流程] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 畫面中，以滑鼠右鍵按一下 CDC 分隔器，然後選取 **[顯示進階編輯器]**。  
  
     如需有關使用 CDC 分隔器的詳細資訊，請參閱＜Microsoft SQL Server Integration Services 的 CDC 元件＞。  
  
## <a name="see-also"></a>另請參閱  
 [CDC 分隔器](cdc-splitter.md)  
  
  
