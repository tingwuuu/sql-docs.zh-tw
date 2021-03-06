---
title: 瀏覽資料與 Cube 中的中繼資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 5faf2a9d-df39-465f-9c81-a00d5cd63f5a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c062137987a8ee1499449425d8e02df0d203050
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52519892"
---
# <a name="browse-data-and-metadata-in-cube"></a>瀏覽 Cube 中的資料和中繼資料
  使用 Cube 設計師的 [瀏覽器] 索引標籤瀏覽 Cube 資料。 您可以使用此檢視檢查 Cube 的結構，並檢查資料庫物件的資料、計算、格式及安全性。 您可以像是使用者在報表工具或其他用戶端應用程式檢視 Cube 一樣，快速檢查 Cube。 當您瀏覽 Cube 資料時，您可以檢視不同的維度、向下鑽研至成員，以及配量維度。  
  
 在瀏覽 Cube 之前，您必須對其進行處理及重新連接。 處理後，請開啟 Cube 設計師的 [瀏覽器] 索引標籤。 按一下工具列上的 [重新連接] 按鈕，重新整理連接。  
  
 **瀏覽器**索引標籤具有三個窗格-中繼資料 窗格、 篩選 窗格和 資料 窗格。 使用 [中繼資料] 窗格，可以樹狀目錄檢查 Cube 的結構。 使用 [瀏覽器] 索引標籤頂端的 [篩選] 窗格，可定義您要瀏覽的任何 Subcube。 使用 [資料] 窗格，可檢視結果集並向下鑽研維度階層。  
  
## <a name="setting-up-the-browser"></a>設定瀏覽器  
 若要準備瀏覽 Cube，您可以指定所要使用的檢視方塊或翻譯。 您可以將量值和維度加入至 [資料] 窗格，並在 [篩選] 窗格中指定任何篩選。  
  
##### <a name="specifying-a-perspective"></a>指定檢視方塊  
 使用 [檢視方塊] 清單，選擇為 Cube 定義的檢視方塊。 檢視方塊會在 Cube 設計師的 [檢視方塊] 索引標籤中定義。 若要切換為其他檢視方塊，請選取清單中的任何檢視方塊。  
  
##### <a name="specifying-a-translation"></a>指定翻譯  
 使用 [語言] 清單，選擇為 Cube 定義的翻譯。 翻譯會在 Cube 設計師的 [翻譯] 索引標籤中定義。 [瀏覽器] 索引標籤一開始會顯示由 Cube 的 [語言] 屬性所指定之預設語言的標題。 若要切換為其他語言，請選取清單中的任何語言。  
  
##### <a name="formatting-the-data-pane"></a>格式化資料窗格  
 您可以格式化 [資料] 窗格中的標題和資料格。 以滑鼠右鍵按一下要格式化的選取資料格或標題，然後按一下 [命令與選項]。 根據您選取的項目，[命令與選項] 對話方塊會顯示 [格式]、[篩選條件與群組]、[報表] 及 [行為] 的設定。  
  
## <a name="setting-up-the-data"></a>設定資料  
  
##### <a name="adding-or-removing-measures"></a>加入或移除量值  
 將您要瀏覽的量值從 [中繼資料] 窗格，拖曳至 [資料] 窗格 (即工作空間右下方的大型空白窗格) 的詳細資料區域。 當您拖曳額外的量值時，這些量值會加入為資料行。 垂直線表示每個額外的量值將放置的位置。 拖曳 [量值] 資料夾以將所有量值放入詳細資料區域中。  
  
 若要從詳細資料區域中移除量值，請將量值拖出 [資料] 窗格，或以滑鼠右鍵按一下量值，然後按一下捷徑功能表上的 [刪除]。  
  
##### <a name="adding-or-removing-dimensions"></a>加入或移除維度  
 將階層或維度拖曳至資料列或篩選區域。  
  
 如果您想要使用多個維度，請使用 [在 Excel 中進行分析]。 如果 Excel 與 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]安裝在同一部電腦上，[在 Excel 中進行分析] 捷徑會啟動 Excel。 Excel 會開啟活頁簿，其中包含目前資料庫的現有連接，以及預先載入量值和維度的樞紐分析表欄位清單。 如需詳細資訊，請參閱[在 Excel 中進行分析 &#40;瀏覽器索引標籤，Cube 設計師&#41; &#40;Analysis Services - 多維度資料&#41;](../analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)。  
  
 若要移除維度，請將維度拖出 [資料] 窗格，或以滑鼠右鍵按一下維度，然後按一下捷徑功能表上的 [刪除]。  
  
##### <a name="adding-or-removing-filters"></a>加入或移除篩選  
 您可以使用下列兩種方法之一加入篩選：  
  
-   在 [中繼資料] 窗格中展開維度，然後將階層拖曳至 [篩選] 窗格。  
  
     \-或-  
  
-   在**維度**資料行**篩選**窗格中，按一下  **\<選取維度 >** 並從清單中，選取維度，然後按一下  **\<選取階層 >** 中**階層**資料行，然後選取清單中的階層。  
  
 指定階層之後，請指定運算子和篩選運算式。 下表描述運算子和篩選運算式。  
  
|運算子|篩選運算式|描述|  
|--------------|-----------------------|-----------------|  
|等於|一個或多個成員|值必須等於指定的成員<br /><br /> (為父子式階層以外的屬性階層提供多個成員選取，並為其他階層提供單一成員選取)。|  
|Not Equal|一個或多個成員|值不得等於指定的成員<br /><br /> (為父子式階層以外的屬性階層提供多個成員選取，並為其他階層提供單一成員選取)。|  
|In|一個或多個命名集|值必須在指定的命名集中<br /><br /> (僅支援屬性階層)。|  
|Not In|一個或多個命名集|值不得在指定的命名集中<br /><br /> (僅支援屬性階層)。|  
|Range (Inclusive)|範圍的一個或兩個分隔的成員|值必須介於分隔的成員之間，或等於分隔的成員。 如果分隔的成員等於或僅指定一個成員，則不會限制範圍，且會允許所有值<br /><br /> (僅支援屬性階層。 範圍必須在階層的其中一個層級。 目前不支援無限制的範圍)。|  
|Range (Exclusive)|範圍的一個或兩個分隔的成員|值必須介於分隔的成員之間。 如果分隔的成員等於或僅指定一個成員，則值必須大於或小於分隔的成員<br /><br /> (僅支援屬性階層。 範圍必須在階層的其中一個層級。 目前不支援無限制的範圍)。|  
|MDX|傳回成員集的 MDX 運算式|值必須在導出成員集中。 選取此選項會顯示用於建立 MDX 運算式的 [導出成員產生器] 對話方塊。|  
  
 針對可在篩選運算式中指定多個成員的使用者定義階層，所有指定的成員必須位於相同的層級，並共用相同的父系。 此限制不適用父子式階層。  
  
## <a name="working-with-data"></a>使用資料  
  
##### <a name="drilling-down-into-a-member"></a>向下鑽研至某位成員  
 若要向下鑽研至特定成員，請按一下該成員旁的加號 (+)，或按兩下該成員。  
  
##### <a name="slicing-through-cube-dimensions"></a>配量 Cube 維度  
 若要篩選 Cube 資料，請按一下最上層資料行標頭的下拉式清單方塊。 您可以展開階層，然後選取或清除任何層級的成員，以顯示或隱藏該成員及其所有下階。 清除 [(全部)] 旁的核取方塊，可清除階層中的所有成員。  
  
 針對維度設定此篩選之後，您可以在 [資料] 窗格中的任何位置按一下滑鼠右鍵，然後按一下 [自動篩選] 開啟或關閉篩選。  
  
##### <a name="filtering-data"></a>篩選資料  
 您可以使用篩選區域定義要瀏覽的 Subcube。 若要加入篩選，請按一下 [篩選] 窗格中的維度，或在 [中繼資料] 窗格中展開維度，再將階層拖曳至 [篩選] 窗格。 然後指定 [運算子] 和 [篩選運算式]。  
  
##### <a name="performing-actions"></a>執行動作  
 三角形標示 [資料] 窗格中含有動作的任何標題或資料格。 這可能適用於維度、層級、成員或 Cube 資料格。 將指標移至標題物件上方，以查看可用的動作清單。 按一下資料格中的三角形顯示功能表，然後啟動相關聯處理序。  
  
 為了安全起見，[瀏覽器] 索引標籤僅支援下列動作：  
  
-   URL  
  
-   資料列集  
  
-   鑽研  
  
 不支援命令列、陳述式及專屬動作。 只有連結網頁安全，URL 動作才安全。  
  
##### <a name="viewing-member-properties-and-cube-cell-information"></a>檢視成員屬性和 Cube 資料格資訊  
 若要檢視維度物件或資料格值的詳細資訊，請將指標移至資料格上方。  
  
##### <a name="showing-or-hiding-empty-cells"></a>顯示或隱藏空的資料格  
 您可以在 [資料] 窗格中的任何位置按一下滑鼠右鍵，然後按一下 [顯示空的資料格]，以隱藏資料格中的空資料格。  
  
  
