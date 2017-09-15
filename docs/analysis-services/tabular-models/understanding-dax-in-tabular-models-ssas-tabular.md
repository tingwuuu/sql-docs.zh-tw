---
title: "DAX 中表格式模型 (SSAS 表格式) |Microsoft 文件"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2693985-1bea-4861-a100-cea4761ba809
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 653c715b8a3b990cc6073b2455887232c71c32b4
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="dax-in-tabular-models-ssas-tabular"></a>DAX 中表格式模型 (SSAS 表格式)
  Data Analysis Expressions (DAX) 是一種公式語言，用來分析服務，Power BI Desktop，並在 Excel 中的 Power Pivot 中建立自訂計算。 DAX 公式包含函數、運算子和值，可對資料表和資料行中的資料執行進階計算。  
  
 雖然 DAX 會使用在 Analysis Services、 Power BI Desktop 和 Power Pivot，在 Excel 中，本主題適用於多撰寫在 SQL Server Data Tools (SSDT) 的 Analysis Services 表格式模型專案。  
  
##  <a name="bkmk_DAX"></a> DAX formulas in calculated columns, measures, and row filters  
 在 SSDT 中撰寫表格式模型，DAX 公式用於導出資料行、 量值和資料列篩選器。  
  
### <a name="calculated-columns"></a>導出資料行  
 導出資料行是資料行加入至現有的資料表 （在模型設計師），然後建立 DAX 公式定義資料行的值。 
  
> [!NOTE]  
>  使用 DirectQuery 模式從關聯式資料來源擷取資料的模型不支援導出資料行。  
  
 當導出資料行包含有效的 DAX 公式時，只要輸入公式之後，就會為每個資料列計算值。 然後值會儲存在資料庫中。 例如在 Date 資料表中，將公式 `=[Calendar Year] & " Q" & [Calendar Quarter]` 輸入公式列時，就會計算資料表中每個資料列的值，方法是取出 Calendar Year 資料行 (在相同的 Date 資料表) 中的值、加上空格和大寫字母 Q，然後加入 Calendar Quarter 資料行 (在相同的 Date 資料表) 中的值。 系統會立即計算導出資料行中每個資料列的結果，並顯示為 **2010 Q1**。 只有在重新處理資料時，才會重新計算資料行值。  
  
 如需詳細資訊，請參閱 [導出資料行](../../analysis-services/tabular-models/ssas-calculated-columns.md)中撰寫的表格式模型專案。  
  
### <a name="measures"></a>量值  
 量值為動態公式，其結果會根據內容而改變。 量值用於報告支援結合與篩選模型資料的使用多個屬性，例如 Power BI 報表或 Excel 樞紐分析表或樞紐分析圖的格式。 模型作者定義量值在 SSDT 中模型設計師中使用的量值方格 （和公式列）。  
  
 量值中的公式可以使用由自動加總功能自動建立的標準彙總函式 (例如 COUNT 或 SUM)，或者您可以使用 DAX 自行定義公式。 當您在公式列中定義量值的公式時，工具提示功能會顯示目前內容總計應該有的結果預覽，但是不會在任何地方立即輸出結果。 其他量值詳細資料也會出現在 **[屬性]** 窗格中。  
  
 您無法立即看到計算 (已篩選) 結果的原因如下：在沒有內容的情況下無法判定量值的結果。 評估量值需要報告用戶端應用程式可以提供擷取每一個資料格之相關資料所需的內容，然後為每一個資料格評估運算式。 用戶端可能是 Excel 樞紐分析表或樞紐分析圖、 Power BI 報表或 MDX 查詢。 不論報告用戶端為何，都會針對結果中的每一個資料格執行個別的查詢。 也就是說，樞紐分析表，資料列和資料行的標頭的每個組合或交叉分析篩選器和篩選器，在 Power BI 報表中，每個選取項目會產生不同的導出量值的資料子集。 例如，在具有公式的量值`Total Sales:=SUM([Sales Amount])`，當使用者將 TotalSales 量值放入樞紐分析表，在 [值] 視窗中，而且然後數位 DimProductCategory 從資料行篩選] 視窗的 [Sales Amount 的加總 DimProduct 資料表為每個產品類別目錄計算並顯示。  
  
 與導出資料行和資料列篩選不同的是，量值的語法會在公式前加上量值的名稱。 在剛才提供的範例中，名稱 **Total Sales:** 會出現在公式之前。 當您建立量值之後，名稱及其定義會出現在報告用戶端應用程式的欄位清單中，而且可以提供給模型的所有使用者使用 (視檢視方塊和角色而定)。  
  
 如需詳細資訊，請參閱 [量值](../../analysis-services/tabular-models/measures-ssas-tabular.md)中撰寫的表格式模型專案。  
  
### <a name="row-filters"></a>資料列篩選  
 資料列篩選會定義特定角色的成員可以看到的資料表資料列。 您可以使用 DAX 公式，為模型中的每個資料表建立資料列篩選。 資料列篩選器會在 SSDT 中使用角色管理員建立特定的角色。 使用角色屬性在 SQL Server Management Studio (SSMS) 也已部署的模型定義資料列篩選。  
  
 在資料列篩選中，必須評估為布林 TRUE/FALSE 條件的 DAX 公式會定義該特定角色成員的查詢結果可傳回的資料列。 無法傳回 DAX 公式中未包含的資料列。 例如，對於 Sales 角色成員來說，Customers 資料表具有下列 DAX 公式 `=Customers[Country] = “USA”`，因此 Sales 角色成員只能檢視美國客戶的資料，以及彙總，例如只針對美國客戶傳回的 SUM。  
  
 當您透過使用 DAX 公式定義資料列篩選時，會建立允許的資料列集。 這並不會拒絕存取其他資料列；而是它們根本不會做為允許的資料列集一部分傳回。 其他角色可以允許存取 DAX 公式所排除的資料列。 如果使用者是另一個角色的成員，而且該角色的資料列篩選允許存取該特定資料列集，使用者就可以檢視該資料列的資料。  
  
 資料列篩選會套用至指定的資料列及相關的資料列。 當資料表具有多個關聯性時，篩選會對作用中關聯性套用安全性。 資料列篩選會與針對相關資料表定義的其他資料列篩選進行交叉篩選。  
  
 如需詳細資訊，請參閱[角色](../../analysis-services/tabular-models/roles-ssas-tabular.md)。  
  
##  <a name="bkmk_DAX_datatypes"></a> DAX 資料類型  
 您可以從可能支援不同資料類型的許多不同資料來源，將資料匯入模型中。 當您將資料匯入模型時，資料會轉換為其中一個表格式模型資料類型。 當模型資料用於計算時，在計算的持續時間內資料會轉換為 DAX 資料類型做為輸出。 當您建立 DAX 公式時，用於公式中的詞彙會自動判斷傳回的值資料類型。  
  
 表格式模型和 DAX 支援下列資料類型：  
  
|模型中的資料類型|DAX 中的資料類型|說明|  
|------------------------|----------------------|-----------------|  
|整數|64 位元 (八位元組) 整數值 <sup>1、2</sup>|沒有小數位數的數字。 整數可以是正數或負數，但必須是 -9,223,372,036,854,775,808 (-2^63) 到 9,223,372,036,854,775,807 (2^63-1) 之間的整數。|  
|十進位數字|64 位元 (八位元組) 實數 <sup>1、2</sup>|實數是可以有小數位數的數字。 實數涵蓋極廣的值範圍：<br /><br /> 負值是從 -1.79E + 308 到 -2.23E - 308<br /><br /> 零 (0)<br /><br /> 正值是從 2.23E -308 到 1.79E + 308<br /><br /> 不過，有效位數的數目限制為 17 個小數位數。|  
|布林|布林|True 或 False 值。|  
|Text|字串|Unicode 字元資料字串。 可以是字串或數字，或以文字格式表示的日期。|  
|日期|日期/時間|採用可接受之日期時間表示方式的日期和時間。<br /><br /> 有效日期為 1900 年 3 月 1 日之後的所有日期。|  
|貨幣|貨幣|貨幣資料類型允許的值是從 -922,337,203,685,477.5808 到 922,337,203,685,477.5807 且固定有效位數為四個小數位數。|  
|不適用|空白|空白是 DAX 中表示和取代 SQL Null 的資料類型。 您可以使用 BLANK 函數建立空白，然後使用邏輯函數 ISBLANK 來測試空白。|  
  
 表格式模型也包含資料表資料類型，做為許多 DAX 函數的輸入或輸出。 例如，FILTER 函數會採用資料表做為輸入，並輸出只包含符合篩選條件之資料列的另一份資料表。 您可以結合資料表函數與彙總函式，透過動態定義的資料集執行複雜的計算。  
  
 資料類型通常會自動設定，因此，了解資料類型以及套用方式 (尤其是套用至 DAX 公式) 相當重要。 例如，公式中的錯誤或非預期的結果通常是因為使用無法搭配引數中指定之資料類型使用的特定運算子所造成。 例如，公式 `= 1 & 2`會傳回字串結果 12。 不過，公式 `= “1” + “2”`會傳回整數結果 3。  
  
 如需在表格式模型和 DAX 中的資料類型的明確和隱含轉換的資料類型的詳細資訊，請參閱[支援的資料類型](../../analysis-services/tabular-models/data-types-supported-ssas-tabular.md)。  
  
##  <a name="bkmk_DAX_opertors"></a> DAX 運算子  
 DAX 語言會在公式中使用四種不同類型的計算運算子：  
  
-   比較運算子，用於比較值並傳回全域 TRUE\FALSE 值。  
  
-   算術運算子，用於執行傳回數值的算術計算。  
  
-   加入兩個或多個文字字串的文字串聯運算子。  
  
-   邏輯運算子，其中會結合兩個或多個運算式以傳回單一結果。  
  
 如需 DAX 公式中使用之運算子的詳細資訊，請參閱 [DAX Operator Reference](http://msdn.microsoft.com/en-us/1befbddc-6178-472c-8bc4-05dafd62207e)。  
  
##  <a name="bkmk_DAX_Formulas"></a> DAX formulas  
 DAX 公式對於在導出資料行和量值中建立計算，以及使用資料列層級篩選保護資料安全相當重要。 若要建立導出資料行和量值的公式，您將使用模型設計師視窗或 DAX 編輯器上方的公式列。 若要建立資料列篩選的公式，您要使用 [角色管理員] 對話方塊。 本節中的資訊是為了讓您開始了解 DAX 公式的基本概念。  
  
###  <a name="basics"></a> Formula basics  
 DAX 可讓表格式模型作者在兩個模型資料表中定義自訂計算當做導出資料行的一部分，以及當做與資料表相關但是未直接出現在其中之量值的一部分。 DAX 也可讓模型作者保護資料安全，方法是，建立傳回布林值的計算、定義相關聯角色的成員使用者可以在特定或相關資料表中查詢的資料列。  
  
 DAX 公式可以很簡單也可以很複雜。 下表顯示可能會在導出資料行中使用的一些簡單公式範例。  
  
|||  
|-|-|  
|公式|說明|  
|`=TODAY()`|在資料行的每個資料列中插入今天的日期。|  
|`=3`|在資料行的每個資料列中，插入 3 這個值。|  
|`=[Column1] + [Column2]`|將 [Column1] 和 [Column2] 同一資料列中的值相加，並將結果放在相同資料列的導出資料行中。|  
  
 無論您建立的公式簡單還是複雜，都可以在建立公式時使用以下步驟：  
  
1.  每個公式開頭都必須為等號。  
  
2.  您可以輸入或選取函數名稱，或輸入運算式。  
  
3.  開始輸入所需之函數或名稱的前幾個字母，「自動完成」就會顯示可用函數、資料表和資料行的清單。 按 TAB 鍵從「自動完成」清單將項目加入至公式。  
  
     您也可以按一下 **Fx** 按鈕來顯示可用函數的清單。 若要從下拉式清單中選取函數，使用方向鍵反白顯示該項目，然後按一下 **[確定]** ，就可以將該函數加入至公式中。  
  
4.  從可能之資料表和資料行的下拉式清單中選取引數，或輸入值來提供函數的引數。  
  
5.  檢查語法錯誤：請確認所有括號都有成對，而且資料行、資料表和值的參考都正確。  
  
6.  按下 ENTER 鍵接受公式。  
  
> [!NOTE]  
>  導出資料行，只要輸入公式而且公式已驗證，資料行會填入值。 在量值中，按下 ENTER 可將量值定義與資料表一起儲存在量值方格中。 如果公式無效，則會顯示錯誤。  
  
 在此範例中，我們將會在「當季天數」量值中看到更複雜的公式：  
  
```  
Days in Current Quarter:=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))  
```  
  
 這個量值可用來在一個不完整期間與前一個期間之間建立比率。 此公式必須考慮期間內已經過的比例，並且將它與前一個期間中的相同比例進行比較。 在此案例中，[Days Current Quarter to Date]/[Days in Current Quarter] 會得出目前期間內已經過的比例。  
  
 此公式包含下列元素：  
  
|公式元素|說明|  
|---------------------|-----------------|  
|`Days in Current Quarter:=`|量值的名稱。|  
|`=`|等號 (=) 開始公式。|  
|`COUNTROWS`|[COUNTROWS 函數 (DAX)](http://msdn.microsoft.com/en-us/830dd659-5405-4e0a-8d26-01ae9d5e5e9a) 會計算 Date 資料表中資料列的總數|  
|`()`|左右括號會指定引數。|  
|`DATESBETWEEN`|DATESBETWEEN 函數會傳回 Date 資料表的 Date 資料行中，每個值最後一個日期間的日期。|  
|`'Date'`|指定 Date 資料表。 資料表用單引號括住。|  
|`[Date]`|指定 Date 資料表中的 Date 資料行。 資料行用括弧括住。|  
|`,`||  
|`STARTOFQUARTER`|STARTOFQUARTER 函數會傳回季度開始的日期。|  
|`LASTDATE`|LASTDATE 函數會傳回季度的最後一個日期。|  
|`'Date'`|指定 Date 資料表。|  
|`[Date]`|指定 Date 資料表中的 Date 資料行。|  
|`,`||  
|`ENDOFQUARTER`|ENDOFQUARTER 函數|  
|`'Date'`|指定 Date 資料表。|  
|`[Date]`|指定 Date 資料表中的 Date 資料行。|  
  
#### <a name="using-formula-autocomplete"></a>使用公式自動完成  
 模型設計師中的公式列和 [角色管理員] 對話方塊中的 [資料列篩選公式] 視窗都會提供 [自動完成] 功能。 [自動完成] 透過提供您公式中每個元素的選項，協助您輸入有效的公式語法。  
  
-   您可以透過巢狀函數，在現有的公式中間使用「公式自動完成」功能。 插入點前方的文字用於顯示下拉式清單中的值，而在插入點之後的所有文字則維持不變。  
  
-   自動完成不會加入函數的右括號，也不會自動比對括號。 您必須確定每個函數的語法正確，否則您無法儲存或使用公式。  
  
#### <a name="using-multiple-functions-in-a-formula"></a>在公式中使用多個函數  
 您可以巢狀函數，也就是說，您可以使用某個函數的結果做為另一個函數的引數。 您最多可以在計算結果欄中巢狀 64 個層級的函數。 不過，巢狀可能會使公式的建立或疑難排解變得困難。  
  
 許多函數的設計都是當做巢狀函數單獨使用。 這些函數會傳回一個資料表，這個資料表是為了當做資料表函數的輸入而提供，無法直接儲存為結果。 例如，SUMX、AVERAGEX 和 MINX 這些函數都需要使用資料表做為第一個引數。  
  
> [!NOTE]  
>  為確保效能不受到資料行間相依性所需之多個計算的影響，在量值中巢狀函數有一些限制。  
  
##  <a name="bkmk_DAX_functions"></a> DAX functions  
 本節提供 DAX 支援之函數類型  的概觀。 如需詳細資訊，請參閱 [DAX Function Reference](http://msdn.microsoft.com/en-us/4dbb28a1-dd1a-4fca-bcd5-e90f74864a7b)。  
  
 DAX 會提供各種函數，您可以使用這些函數來執行使用日期和時間的計算、建立條件式值、處理字串、根據關聯性執行查閱，而且能夠逐一查看資料表以執行遞迴計算。 如果您熟悉 Excel 公式，這些功能很多似乎非常相似，不過，DAX 公式在以下重要方面不同：  
  
-   DAX 函數一律參考完整的資料行或資料表。 如果您只要使用資料表或資料行中的特定值，可以將篩選加入至公式。  
  
-   如果您需要逐資料列自訂計算，DAX 提供的函數可讓您使用目前的資料列值或相關的值來當做某種參數，以便執行依內容而改變的計算。 若要了解這些函數的運作方式，請參閱本主題稍後的＜ [Context in DAX Formulas](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md#bkmk_context) ＞。  
  
-   DAX 包含的許多函數都會傳回資料表，而不是傳回值。 此資料表不會顯示在報告用戶端中，但是會用來提供其他函數的輸入。 例如，您可以擷取資料表，然後計算其中相異值的數目，或是計算橫跨篩選資料表或資料行的動態總和。  
  
-   DAX 函數包含各種*時間智慧*函式。 這些函數可讓您定義或選取日期範圍，並根據這些日期或範圍執行動態計算。 例如，您可以比較平行期間的總和。  
  
### <a name="date-and-time-functions"></a>日期和時間函數  
 DAX 中的日期和時間函數與 Microsoft Excel 中的日期和時間函數類似。 不過，DAX 函數會以 Microsoft SQL Server 所使用的 **datetime** 資料類型為基礎。 如需詳細資訊，請參閱 [日期和時間函數 (DAX)](http://msdn.microsoft.com/en-us/9fc9214a-fcd6-40c0-bf51-0c95637c6ffb)。  
  
### <a name="filter-functions"></a>篩選函數  
 DAX 中的篩選函數會傳回特定的資料類型、查閱相關資料表中的值，以及依相關值篩選。 查閱函數會透過使用資料表和關聯性 (例如資料庫) 運作。 篩選函數可讓您操作資料內容來建立動態計算。 如需詳細資訊，請參閱 [篩選函數 (DAX)](http://msdn.microsoft.com/en-us/b036fd40-4d3b-426d-a0d2-80258b53d8e5)。  
  
### <a name="information-functions"></a>資訊函數  
 資訊函數會查看當做引數提供的資料格或資料列，然後告訴您該值是否符合預期的類型。 例如，如果您參考的值包含錯誤，ISERROR 函數會傳回 TRUE。 如需詳細資訊，請參閱 [資訊函數 (DAX)](http://msdn.microsoft.com/en-us/6d2bee09-0456-4444-b4d2-c231fd788a2e)。  
  
### <a name="logical-functions"></a>邏輯函數  
 邏輯函數會在運算式上作用，以傳回運算式中值的相關資訊。 例如，TRUE 函數會讓您知道您所評估的運算式是否會傳回 TRUE 值。 如需詳細資訊，請參閱 [邏輯函數 (DAX)](http://msdn.microsoft.com/en-us/2eb33add-60b2-44ab-b761-012a473116a2)。  
  
### <a name="mathematical-and-trigonometric-functions"></a>數學和三角函數  
 DAX 中的數學函數與 Excel 的數學和三角函數非常類似。 在 DAX 函數所使用的數值資料類型中有一些小差異。 如需詳細資訊，請參閱 [數學與三角函數 (DAX)](http://msdn.microsoft.com/en-us/1f408ec1-e769-43d6-a68c-567bc30d893f)。  
  
### <a name="statistical-functions"></a>統計函數  
 DAX 提供執行彙總的統計函數。 在 DAX 中，除了可以建立加總與平均值，或尋找最小與最大值之外，您還可以先篩選資料行再進行彙總，或是根據相關資料表建立彙總。 如需詳細資訊，請參閱 [統計函數 (DAX)](http://msdn.microsoft.com/en-us/ba4c1298-57a0-40fc-b6f6-00e187ace559)。  
  
### <a name="text-functions"></a>文字函數  
 DAX 中的文字函數與其在 Excel 中的對應項目非常類似。 您可以傳回字串的一部分、搜尋字串中的文字，或串連字串值。 DAX 也提供了用來控制日期、時間和數字之格式的函數。 如需詳細資訊，請參閱 [文字函數 (DAX)](http://msdn.microsoft.com/en-us/e4821571-ae55-4df7-ae98-c578200bba5f)。  
  
### <a name="time-intelligence-functions"></a>時間智慧函數  
 DAX 中提供的時間智慧函數可讓您建立使用行事曆與日期之內建知識的計算。 若將時間和日期範圍與彙總或計算搭配使用，您可以針對銷售量、存貨等等，根據類似的時間範圍建立有意義的比較。 如需詳細資訊，請參閱[時間智慧函數 (DAX)](http://msdn.microsoft.com/en-us/91df278d-4b28-40c1-a572-cdb91f081517)。  
  
###  <a name="bkmk_TableFunc"></a> Table-valued functions  
 有 DAX 函數可以輸出資料表並 (或) 採用資料表做為輸入。 資料表可能會只有單一資料行，因此資料表值函式也會採用單一資料行做為輸入。 了解如何使用這些資料表值函式對於善用 DAX 公式相當重要。 DAX 包括下列類型的資料表值函式：  
  
  **篩選函數**-傳回資料行、 資料表或目前的資料列相關的值。  
    
  **彙總函式**-彙總資料表資料列上任何運算式。  
    
  **時間智慧函數**-傳回資料表的日期，或計算彙總使用的日期資料表。  
  
##  <a name="bkmk_context"></a> Context in DAX formulas  
 *「內容」* (Context) 是使用 DAX 建立公式時要了解的重要概念。 內容可讓您執行動態分析當做公式變更的結果，以反映目前的資料列或資料格選擇以及任何相關的資料。 了解內容並有效地使用內容對於建立高效能的動態分析及排除公式內的問題而言將會非常關鍵。  
  
 表格式模型中的公式可以在不同內容中評估，這取決於其他設計元素：  
  
-   在樞紐分析表或報表中套用的篩選  
  
-   公式中定義的篩選  
  
-   使用公式中的特殊函數指定的關聯性  
  
 內容可分為以下不同類型： *「資料列內容」*(Row Context)、 *「查詢內容」*(Query Context) 和 *「篩選內容」*(Filter Context)。  
  
###  <a name="bkmk_row_context"></a> Row context  
 *「資料列內容」* (Row context) 可以被視為「目前的資料列」。 如果您已經在導出資料行中建立公式，該公式的「資料列內容」(Row Context) 就會包含目前資料列中所有資料行的值。 如果資料表與另一個資料表相關，則內容也會包含後者中與目前資料列相關的所有值。  
  
 例如，假設您建立導出資料行 `=[Freight] + [Tax]`，將相同資料表中兩個資料行 Freight 和 Tax 的值相加。 此公式只會從指定之資料行中目前的資料列自動取得值。  
  
 資料列內容也會遵循資料表之間已定義的任何關聯性，包過在導出資料行內使用 DAX 公式所定義的關聯性，以判斷相關資料表中的哪些資料列與目前的資料列相關。  
  
 例如，下列公式會根據訂單的運送區域，使用 RELATED 函數來提取相關資料表中的稅額值。 稅額值的決定方式是使用目前資料表中的區域值，在相關資料表中查閱該區域，然後從相關資料表取得該區域的稅率。  
  
```  
= [Freight] + RELATED('Region'[TaxRate])  
```  
  
 此公式會從 Region 資料表取得目前區域的稅率，然後將它加入至 Freight 資料行的值。 在 DAX 公式中，您不需要知道或指定連接不同資料表的特定關聯性。  
  
#### <a name="multiple-row-context"></a>多個資料列內容  
 DAX 包含會反覆對資料表進行計算的函數。 這些函數可以有多個目前資料列，每一個資料列都有自己的資料列內容。  實際上，這些函數可讓您建立公式，這些公式會以遞迴方式對內部和外部迴圈執行運算。  
  
 例如，假設您的模型中包含一個 **Products** 資料表和一個 **Sales** 資料表。 使用者可能會想查看整個 Sales 資料表 (其中都是與多項產品相關的交易)，然後在其中找到任何一次交易中每項產品的最大訂購數量。  
  
 使用 DAX 時，您可以建立單一公式來傳回正確的值，而且每當使用者將資料加入至資料表時，都會自動更新結果。  
  
```  
=MAXX(FILTER(Sales,[ProdKey]=EARLIER([ProdKey])),Sales[OrderQty])  
```  
  
 如需此公式的詳細逐步解說，請參閱 [EARLIER 函數 (DAX)](http://msdn.microsoft.com/en-us/6d126c4d-2315-49ec-899d-cb396eefbae6)。  
  
 總而言之，EARLIER 函數會儲存目前運算前之運算中的資料列內容。 函數隨時都會在記憶體中儲存兩組內容：一組內容代表公式內部迴圈的目前資料列，另一組內容代表公式外部迴圈的目前資料列。 DAX 會自動在兩個迴圈之間選取饋入值，讓您能夠建立複雜的彙總。  
  
####  <a name="bkmk_query_context"></a> Query context  
 *「查詢內容」* (Query Context) 指的是以隱含方式針對公式擷取之資料的子集。 當使用者將量值或其他值欄位放入樞紐分析表中或是以表格式模型為基礎的報表中時，引擎會檢查資料列和資料行標頭、交叉分析篩選器和報表篩選來判斷內容。 然後，將會針對資料來源執行必要查詢來取得正確的資料子集、執行公式所定義的計算，然後填入樞紐分析表或報表中的每個資料格。 所擷取的資料集就是每個資料格的查詢內容。  
  
> [!WARNING]  
>  在 DirectQuery 模式的模型中，先評估內容，然後擷取正確資料子集和計算結果的設定作業會轉譯成 SQL 陳述式。 這些陳述式會直接針對關聯式資料存放區來執行。 因此，雖然取得資料和計算結果的方法不同，但是內容本身不會改變。  
  
 因為內容會根據您放置公式的地方而不同，所以公式的結果也會改變。  
  
 例如，假設您建立公式來加總 **Sales** 資料表中 **Profit** 資料行內的值： `=SUM('Sales'[Profit])`。  如果您在 **Sales** 資料表之中的導出資料行內使用這個公式，整個資料表的公式結果都是一樣的，因為公式的查詢內容一律都是 **Sales** 資料表的整個資料集。 結果會包含所有區域、所有產品、所有年度等等的利潤。  
  
 但是，使用者通常不會想要一直看到相同的結果，而會想取得特定年度、特定國家/地區、特定產品，或上述各項的某個組合的利潤，然後取得總計。  
  
 您可以加入或移除資料行和資料列標頭，以及加入或移除交叉分析篩選器，來變更樞紐分析表中的內容。 每當使用者將資料行或資料列標題加入樞紐分析表時，都會變更評估量值的查詢內容。 配量和篩選作業也會影響內容。 因此，用於量值中的同一個公式會以不同的 *「查詢內容」* (Query Context) 為每個資料格進行評估。  
  
####  <a name="bkmk_filter_context"></a> Filter context  
 *「篩選內容」* (Filter Context) 是每一個資料行中或是從相關資料表擷取的值中所允許的一組值。 篩選可以在設計工具或展示層 (報表與樞紐分析表) 中套用到資料行。 也可以由公式內的篩選運算式明確定義篩選。  
  
 當您使用公式的引數來指定資料行或資料表內允許之值組的篩選條件約束時，就會加入「篩選內容」(Filter Context)。 篩選內容會套用到其他內容 (如資料列內容或查詢內容) 之上。  
  
 在表格式模型中，有多個方式可以建立篩選內容。 用戶端可以取用模型，例如 Power BI 報表的內容中使用者可以建立篩選，立即在資料列和資料行標題上加入交叉分析篩選器或報表篩選。 您也可以直接在公式內指定篩選運算式，以便指定相關的值、篩選當做輸入使用的資料表，或是針對計算中使用的值來動態取得內容。 您也可以完全清除或選擇性清除特定資料行上的篩選。 當您建立公式來計算總計時，這樣的方式非常實用。  
  
 如需如何在公式中建立篩選的詳細資訊，請參閱 [FILTER 函數 (DAX)](http://msdn.microsoft.com/en-us/f1f6bee4-547b-407c-b70b-9216b2f3d3fd)。  
  
 如需如何清除篩選以建立總計的範例，請參閱 [ALL 函數 (DAX)](http://msdn.microsoft.com/en-us/a7e0ab71-d83e-4463-bc77-9eb5dd73c6fc)。  
  
 如需如何在公式中選擇性清除及套用篩選的範例，請參閱 [ALLEXCEPT 函數 (DAX)](http://msdn.microsoft.com/en-us/a6f575a1-9803-4bb2-85b3-c95c060f1fb1)。  
  
####  <a name="bkmk_determine_context"></a> Determining context in formulas  
 當您建立 DAX 公式時，會先測試公式的語法是否有效，然後再測試來確定公式內包含的資料行和資料表名稱可以在目前內容中找到。 如果找不到公式所指定的任何資料行或資料表，就會傳回錯誤。  
  
 如前幾節中所述，驗證期間的內容 (和重算運算) 是使用模型中可用的資料表、資料表之間的任何關聯性，以及已套用的任何篩選來決定。  
  
 例如，如果您只將某些資料匯入新的資料表，而且該資料並未與其他任何資料表有關 (而且您尚未套用任何篩選)，則「目前內容」是資料表中一組完整的資料行。 如果此資料表與其他資料表之間有關聯性，則目前內容會包含相關資料表。 如果您將資料表中的資料行加入至擁有交叉分析篩選器以及或許某些報表篩選的報表中，則公式的內容為報表內每一個資料格中的資料子集。  
  
 內容是效用強大的概念，但也可能會使公式的疑難排解變得很困難。 建議您從簡單的公式和關聯性開始，以了解內容如何運作。 下一節提供一些範例，說明公式如何使用不同類型的內容以動態方式傳回結果。  
  
##### <a name="examples-of-context-in-formulas"></a>公式中的內容範例  
  
1.  [RELATED 函數 (DAX)](http://msdn.microsoft.com/en-us/0023fd13-c17a-4243-ab77-3779a4b502b6) 可擴充目前資料列的內容來包含相關資料行內的值。 這可以讓您執行查閱。 本主題中的範例說明篩選與資料列內容的互動。  
  
2.  [FILTER 函數 (DAX)](http://msdn.microsoft.com/en-us/f1f6bee4-547b-407c-b70b-9216b2f3d3fd) 可讓您指定要包含在目前內容中的資料列。 本主題的範例也將說明如何在執行彙總的其他函數中嵌入篩選。  
  
3.  [ALL 函數 (DAX)](http://msdn.microsoft.com/en-us/a7e0ab71-d83e-4463-bc77-9eb5dd73c6fc) 可在公式中設定內容。 您可以使用它來覆寫套用為查詢內容結果的篩選。  
  
4.  [ALLEXCEPT 函數 (DAX)](http://msdn.microsoft.com/en-us/a6f575a1-9803-4bb2-85b3-c95c060f1fb1) 可讓您移除所指定篩選以外的所有篩選。 兩個主題都包含範例，可讓您逐步建立公式及了解複雜的內容。  
  
5.  [EARLIER 函數 (DAX)](http://msdn.microsoft.com/en-us/6d126c4d-2315-49ec-899d-cb396eefbae6) 和 [EARLIEST 函數 (DAX)](http://msdn.microsoft.com/en-us/9befa04d-78db-492e-a463-80b8b77206d6) 都可讓您透過執行計算對資料表執行迴圈，同時參考內部迴圈的值。 如果您很熟悉遞迴的概念以及內部和外部迴圈，將深刻領會 EARLIER 和 EARLIEST 函數所提供的強大效用。 如果您不太熟悉這些概念，應該小心地遵循範例中的步驟執行，以了解內部和外部內容如何運用於計算中。  
  
##  <a name="bkmk_RelModel"></a> Formulas and the tabular model  
 模型設計師中的，在 SSDT 中，是一個區域，您可以在此使用多個資料表的資料，並連接表格式模型中的資料表。 在此模型內，將會透過資料行與一般值 (索引鍵) 的關聯性來聯結資料表。 此表格式模型可讓您將值連結到其他資料表內的資料行，並建立更有趣的計算。 正如在關聯式資料庫中一樣，您可以連接許多層級的相關資料表，並使用結果內任何資料表中的資料行。  
  
 例如，您可以連結銷售資料表、產品資料表和產品類別資料表，而且使用者可以在樞紐分析表和報表內使用各種不同的資料行組合。 相關欄位可以用來篩選連接的資料表，或是用來建立子集的計算 (如果您不熟悉關聯式資料庫以及如何使用資料表和聯結，請參閱[關聯性](../../analysis-services/tabular-models/relationships-ssas-tabular.md)。)  
  
 表格式模型支援資料表之間的多個關聯性。 為了避免混淆或結果錯誤，一次只會將一個關聯性指定為作用中的關聯性，但是您可以視需要變更作用中的關聯性，以便周遊計算資料中的不同連接。 [USERELATIONSHIP 函數 (DAX)](http://msdn.microsoft.com/en-us/200484ab-9da1-4570-a100-7f9ed20d33af) 可用來指定要用於特定計算中的一個或多個關聯性。  
  
 在表格式模型中，您應該會看到這些公式設計規則：  
  
-   當透過關聯性連接資料表時，您必須確認當做索引鍵使用的兩個資料行擁有相符的值。 但是不會強制執行參考完整性，所以有可能索引鍵資料行中有不相符的值而仍建立關聯性。 如果發生這個狀況，您應該小心空白值或不相符的值可能會影響公式的結果。  
  
-   當您在模型中使用關聯性來連結資料表時，便會放大評估公式所在的範圍或 *「內容」*(Context)。 因為增加新的資料表、新的關聯性或是使用中關聯性的變更而導致的內容變更可能會導致您的結果以意外的方式改變。 如需詳細資訊，請參閱本主題先前的 [DAX 公式中的內容](#bkmk_context) 。  
  
##  <a name="bkmk_tables"></a> Working with tables and columns  
 表格式模型中資料表的外觀就像 Excel 資料表，但其搭配資料與公式使用的方式有所不同：  
  
-   公式只能搭配資料表和資料行運作，而不能搭配個別的資料格、範圍參考或陣列。  
  
-   公式可以使用關聯性從相關的資料表取得值。 擷取的值永遠都會與目前的資料列值相關聯。  
  
-   您不能像是在 Excel 工作表一樣，擁有不規則或「不完全」的資料， 資料表中的每個資料列都必須包含相同數目的資料行。 不過，在某些資料行中可以有空的值。 Excel 資料表和表格式模型資料表不能彼此交換。  
  
-   因為資料類型是針對每個資料行設定的，所以該資料行中的每個值都必須是相同類型。  
  
### <a name="referring-to-tables-and-columns-in-formulas"></a>在公式中參考資料表和資料行  
 您可以使用名稱來參照任何資料表和資料行。 例如，下列公式說明如何使用 *「完整」* (Fully Qualified) 名稱，參照兩個資料表的資料行：  
  
```  
=SUM('New Sales'[Amount]) + SUM('Past Sales'[Amount])  
```  
  
 評估公式時，模型設計師會先檢查一般語法，然後對照目前內容中可能的資料行和資料表來檢查您提供的資料行和資料表名稱。 如果名稱模稜兩可，或是找不到資料行或資料表，公式就會出現錯誤 (發生錯誤的資料格將顯示 #ERROR 字串而非資料值)。 如需資料表、資料行及其他物件之命名需求的詳細資訊，請參閱 [DAX Syntax Reference](http://msdn.microsoft.com/en-us/098630f4-7d1d-467e-976c-99b2279430d5)中的＜Naming Requirements＞。  
  
### <a name="table-relationships"></a>資料表關聯性  
 藉由建立資料表之間的關聯性，您能夠查閱其他資料表中的資料，並使用相關聯的值來執行複雜的計算。 例如，您可以使用導出資料行，查閱與目前轉售商相關的所有送貨記錄，然後加總各記錄的送貨成本。 但在許多情況下，關聯性可能沒有必要。 您可以在公式中使用 LOOKUPVALUE 函數，針對符合 *search_column* 和 *search_value* 參數所指定之準則的資料列傳回 *result_columnName* 中的值。  
  
 許多 DAX 函數都需要在資料表之間，或是在多個資料表中存在關聯性，才能找到您所參考的資料行，並且傳合理的結果。 其他函數會嘗試識別關聯性。不過，如需達成最佳的結果，您都應該盡可能多加建立關聯性。 如需詳細資訊，請參閱本主題稍早的 [公式與表格式模型](#bkmk_RelModel) 。  
  
##  <a name="bkmk_RefreshRecalc"></a> Updating the results of formulas (Process)  
 *「資料處理」* (Data Process) 和 *「重新計算」* (Recalculation) 是兩個不同但相關的作業。 當您要設計的模型包含複雜公式、大量資料，或包含從外部資料來源取得的資料時，您應該徹底了解這兩個概念。  
  
 *「處理資料」* (Processing Data) 是以外部資料來源的新資料來更新模型中資料的程序。  
  
 *「重新計算」* (Recalculation) 是更新公式結果，以反映公式本身的任何變更與基礎資料的變更之程序。 重新計算可能會以下列方式影響效能：  
  
-   系統會計算導出資料行中的值並將其儲存在模型中。 若要更新導出資料行中的值，您必須使用三個處理命令的其中一個來處理模型：[完整處理]、[處理資料] 或 [處理重新計算]。 每當您變更公式時，公式的結果一定會針對整個資料行重新計算。  
  
-   每當使用者將量值加入樞紐分析表中或開啟報表時，就會動態評估量值所導出的值；當使用者修改內容時，量值傳回的值就會變更。 量值的結果永遠會反映記憶體中最新快取。  
  
 除非重新計算的結果傳回不同的值，而讓角色成員可以或不可以查詢資料列，否則處理和重新計算都不會影響資料列篩選公式。  
  
 如需詳細資訊，請參閱 [處理資料 &#40;SSAS 表格式&#41;](../../analysis-services/tabular-models/process-data-ssas-tabular.md)。  
  
##  <a name="bkmk_troubleshoot"></a> Troubleshooting errors in formulas  
 如果您在定義公式時出現錯誤，該公式可能包含 *「語法錯誤」*(Syntactic Error)、 *「語意錯誤」*(Semantic Error) 或 *「計算錯誤」*(Calculation Error)。  
  
 語法錯誤最容易解決。 它們通常與遺漏括號或逗號有關。 如需個別函數語法的說明，請參閱 [DAX Function Reference](http://msdn.microsoft.com/en-us/4dbb28a1-dd1a-4fca-bcd5-e90f74864a7b)。  
  
 語法正確，但值或參考的資料行在公式的內容中沒有意義時，會發生其他類型的錯誤。 這種語意和計算錯誤可能是由下列任何問題所造成：  
  
-   公式參考不存在的資料行、資料表或函數。  
  
-   公式似乎正確，但是資料引擎擷取到它發現類型不符並引發錯誤的資料。  
  
-   公式傳遞給函數的參數個數或類型不正確。  
  
-   此公式參考有錯誤的另一個資料行，因此它的值無效。  
  
-   此公式會參考尚未處理的資料行，這表示它有中繼資料，但沒有用於計算的實際資料。  
  
 在前四種情況下，DAX 會針對包含無效公式的整個資料行加上旗標。 在最後一種情況下，DAX 會使資料行呈現灰色，表示該資料行處於尚未處理的狀態。  
  
##  <a name="bkmk_addional_resources"></a> Additional resources  
 [表格式模型化 &#40;Adventure Works 教學課程&#41;](../../analysis-services/tabular-modeling-adventure-works-tutorial.md) 對於如何建立在導出資料行、量值和資料列篩選中包含許多計算的表格式模型，提供逐步指示。 對於大部分的公式，則會提供該公式用途的描述。  
  
 [Analysis Services 團隊部落格](http://go.microsoft.com/fwlink/?LinkID=220949&clcid=0x409)提供最新的資訊、 提示、 新聞和宣告。 
  
 [DAX 資源中心](http://go.microsoft.com/fwlink/?LinkID=220966&clcid=0x409) 會提供關於 DAX 的內外部資訊，包括由主要的 Business Intelligence 專業人員所提交的多個 DAX 解決方案。  
  
## <a name="see-also"></a>請參閱＜  
 [Data Analysis Expressions (DAX) 參考](http://msdn.microsoft.com/en-us/70a82136-0926-4a91-bcb3-e18e82593b0d)   
 [量值](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [導出資料行](../../analysis-services/tabular-models/ssas-calculated-columns.md)   
 [角色](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Kpi](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [支援的資料來源](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  