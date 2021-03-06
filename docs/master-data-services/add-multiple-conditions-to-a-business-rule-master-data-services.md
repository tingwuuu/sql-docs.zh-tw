---
title: 將多個條件新增至商務規則 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], multiple conditions
ms.assetid: 5f0f6958-6cf2-444b-bdcd-05b887637a0b
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 34e7a7cb4cfaaa75eca8d51bdb591a7016ba411b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52777370"
---
# <a name="add-multiple-conditions-to-a-business-rule-master-data-services"></a>將多個條件加入至商務規則 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  如果您想要比較複雜的規則，請在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中將多個 **AND** 或 **OR** 條件新增至商務規則。  
  
> [!NOTE]  
>  如果您建立使用 **OR** 運算子的商務規則，請考慮為每個可獨立評估的條件陳述式建立不同的規則。 然後您可以視需要排除規則，提供更多彈性和輕鬆疑難排解。  
  
## <a name="prerequisites"></a>Prerequisites  
 若要執行此程序：  
  
-   您必須擁有存取 **[系統管理]** 功能區域的權限。  
  
-   您必須是模型管理員。 如需詳細資訊，請參閱 [管理員 &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)，您就可以在群組中加入及移除使用者。  
  
-   商務規則必須存在。 如需詳細資訊，請參閱[建立及發行商務規則 &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)。  
  
### <a name="to-add-multiple-conditions-to-a-business-rule"></a>若要將多個條件加入至商務規則  
  
1.  在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。  
  
2.  從功能表列，指向 **[管理]** ，然後按一下 **[商務規則]**。  
  
3.  在 [商務規則] 頁面上，從 [模型] 下拉式清單選取模型。  
  
4.  從 [實體]  下拉式清單選取實體。  
  
5.  從 [成員類型] 下拉式清單中，選取成員的類型。  
  
6.  按一下您想要編輯之商務規則的資料列。  
  
7.  按一下 **[編輯]**。  
  
8.  在 [If] 區塊下，從左側的邏輯運算子下拉式清單中選取 [AND/OR/ NOT]。  
  
9. 按一下 **[加入]**。 面板隨即顯示。  
  
10. 從 [屬性]  下拉式清單中，選取屬性。  
  
11. 從 [運算子] 下拉式清單中選取條件。  
  
12. 完成所有必要的欄位。  
  
13. 按一下 **[儲存]**。 新的資料列就會新增至 [If] 方格中。  
  
14. 或者若要加入更多條件，請完成步驟 8-13。  
  
    > [!TIP]  
    >  若要刪除條件，請選取條件並以滑鼠右鍵按一下它，然後按一下 [刪除]。  
  
    > [!TIP]  
    >  您可以選取多個條件，並按一下滑鼠右鍵將它們集合在邏輯運算子內，或取消群組特定邏輯運算子內的條件。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則 &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)   
 [變更商務規則名稱 &#40;Master Data Services&#41;](../master-data-services/change-a-business-rule-name-master-data-services.md)   
 [設定商務規則來傳送通知 &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
