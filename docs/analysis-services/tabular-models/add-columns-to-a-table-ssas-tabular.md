---
title: 加入 Analysis Services 表格式模型資料表資料行 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a726f7dd8ef72ad30bd055d2f76cc58c7db6183d
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072705"
---
# <a name="add-columns-to-a-table"></a>在資料表新增資料行
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  本文說明如何將資料行新增至現有的資料表。  
  
## <a name="add-columns-from-the-datasource"></a>從資料來源加入資料行  
 當您使用 [資料表匯入精靈] 從資料來源資料表匯入資料時，系統會在模型中建立新的資料表，此模型包含來源資料表中的所有資料行；或者如果您選擇使用 [預覽和篩選] 功能來篩選出某些資料行，則只會包含您選取的資料行及篩選的資料。 您也可以撰寫 SQL 查詢來指定只匯入某些資料行。 但是，您之後可決定來源資料表擁有您想要加入至模型資料表的其他資料行，或者您必須加入所包含的值衍生自 DAX 公式的導出資料行。  
  
 例如，當您一開始從資料來源匯入時，您可以使用 [資料表匯入精靈] 的 [預覽和篩選] 功能，從來源資料表選取有限數目的資料行，稍後您可以決定是否需要從來源資料表加入模型資料表中尚不存在的其他資料行。 又如，新的 AdjustedProfit 資料行已加入至資料來源的 FactSales 資料表，您現在想將相同的 AdjustedProfit 資料行和資料加入至模型中的 Sales 資料表。  
  
 在此情況下，您可以使用 [編輯資料表屬性] 對話方塊從來源資料表中選取資料行，再將其加入至模型資料表。 [編輯資料表屬性] 對話方塊包含 [資料表預覽] 視窗。 [資料表預覽] 視窗會顯示來源端的資料表。 目前包含在模型資料表定義中的資料行已經過檢查。 尚未包含在模型資料表定義中的資料行則不會予以檢查。 您可以從來源中選取資料行，然後按一下 [確定]，將資料行加入至模型資料表定義。 [編輯資料表屬性] 對話方塊的 [資料表預覽] 視窗，提供與 [資料表匯入精靈] 之 [預覽和篩選] 頁面中的 [資料表預覽] 視窗相同的檢視和功能。  
  
> [!IMPORTANT]  
>  將資料行加入至包含兩個 (含) 以上之資料分割的資料表時，您必須先使用資料分割管理員將資料行加入至所有已定義的資料分割，再使用 [編輯資料表屬性] 對話方塊將資料行加入至資料表定義。 將資料行加入至已定義的資料分割之後，即可接著使用 [編輯資料表屬性] 對話方塊，將相同的資料行加入至資料表定義。  
  
> [!NOTE]  
>  如果在一開始使用 [資料表匯入精靈] 匯入資料時，使用 SQL 查詢選取資料表和資料行，則必須在 [編輯資料表屬性] 對話方塊中，再次使用 SQL 查詢將資料行加入至模型資料表。  
  
#### <a name="to-add-a-column-from-the-data-source-by-using-the-edit-table-properties-dialog-box"></a>使用 [編輯資料表屬性] 對話方塊從資料來源加入資料行  
  
1.  在模型設計師中，按一下您要加入資料行的資料表，然後按一下 **[資料表]** 功能表，再按一下  **[資料表屬性]**。  
  
2.  在 **[編輯資料表屬性]** 對話方塊的 [資料表預覽] 視窗中，選取您要加入的來源資料行，再按一下 [確定]。 目前包含在資料表定義中的資料行已經過檢查。  
  
## <a name="add-a-calculated-column"></a>加入導出資料行  
 在導出資料行中，您可以使用 DAX 公式定義每個資料列的值。 例如，您可以使用簡單的公式 (=1)，將值 1 加入至每個資料列，以建立導出資料行。 導出資料行也可以使用更複雜的公式，根據模型中的其他資料計算值。 其他主題將涵蓋有關導出資料行的詳細資訊。 如需詳細資訊，請參閱 [導出資料行](../../analysis-services/tabular-models/ssas-calculated-columns.md)中撰寫的表格式模型專案。  
  
#### <a name="to-create-a-calculated-column"></a>若要建立導出資料行  
  
1.  在模型設計師的 [資料檢視] 中，選取您要加入新的空白導出資料行的資料表，然後捲動至最右側資料行，或按一下 [資料行] 功能表，再按一下 [加入資料行]。  
  
     若要在兩個現有的資料行之間建立新資料行，請以滑鼠右鍵按一下現有的資料行，然後按一下 [插入資料行]。  
  
2.  在公式列中輸入 DAX 公式，以便為每個資料列加入屬性。  
  
## <a name="add-a-blank-column"></a>加入空白的資料行  
 您可以在模型資料表中建立空白的具名資料行。 如果您想從其他來源貼上資料，空白資料行會很有用。 請記住，貼上的資料之儲存方式與匯入的資料之儲存方式不同。 如需詳細資訊，請參閱 <<c0> [ 複製並貼上資料](../../analysis-services/tabular-models/ssas-import-data-copy-and-paste-data.md)。  
  
#### <a name="to-create-a-named-blank-column"></a>建立空白的具名資料行  
  
1.  在模型設計師的 [資料檢視] 中，選取您要加入空白資料行的資料表，然後捲動至最右側資料行，或按一下 [資料行] 功能表，再按一下 [加入資料行]。  
  
     若要在兩個現有的資料行之間建立新資料行，請以滑鼠右鍵按一下現有的資料行，然後按一下 [插入資料行]。  
  
2.  按一下頂端資料格，然後輸入名稱，再按 ENTER。  
  
## <a name="see-also"></a>另請參閱  
 [編輯資料表屬性對話方塊](http://msdn.microsoft.com/library/8d913e83-7246-44cc-8fc7-31729023c0d8)   
 [變更資料表、資料行或資料列篩選對應](../../analysis-services/tabular-models/change-table-column-or-row-filter-mappings-ssas-tabular.md)  
  
  
