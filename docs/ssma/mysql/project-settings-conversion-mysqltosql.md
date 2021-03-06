---
title: 專案設定 （轉換） (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7ad5fe44-6445-4ba8-a457-5af792631f11
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 12e2e61c6b55bf3c549c08f2b090059d674ed83d
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52411265"
---
# <a name="project-settings-conversion-mysqltosql"></a>專案設定 (轉換) (MySQLToSQL)
[轉換] 頁面**專案設定**對話方塊包含設定自訂 SSMA 如何將 MySQL 語法轉換為 SQL Server 或 SQL Azure 的語法。  
  
[轉換] 窗格位於**專案設定**並**預設專案設定**對話方塊。  
  
-   使用**預設專案設定**對話方塊來設定的所有專案的組態選項。 若要存取轉換設定] 中，在**工具**功能表上，選取**預設專案設定**，選取 [移轉專案類型，則需要檢視 / 變更設定**移轉目標版本**下拉式清單中，按一下**一般**底部的左的窗格中，然後選取**轉換**。  
  
-   若要指定目前的專案中，設定**工具**功能表上，按一下**專案設定**，然後按一下**一般**底部的左窗格中，然後按一下  **轉換**。  
  
## <a name="options"></a>選項。  
  
### <a name="collate-clause"></a>Collate 子句  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**明確的 COLLATE 子句轉換**|明確的 COLLATE 子句轉換選項會指定如何將轉換 MySQL 程式碼中明確的 COLLATE 子句。 可能的選項：忽略並以警告標記/會產生錯誤<br /><br />**預設模式**:忽略並以警告標記<br /><br />**開放式模式**:忽略並以警告標記<br /><br />**完整模式**:忽略並以警告標記|  
  
### <a name="column-constraints"></a>資料行條件約束  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**列舉資料類型的資料行產生條件約束**|如果它不會在 MySQL 資料表，請在 SQL Server 或 SQL Azure 資料表中，產生列舉資料類型的資料行的條件約束。 如果是，還會提供列舉資料型別的所有轉換的資料行，包含控制值的檢查條件約束。<br /><br />**預設模式**: 否<br /><br />**開放式模式**:否<br /><br />**完整模式**: 是|  
|**設定資料類型的資料行產生條件約束**|如果它不會在 MySQL 資料表，請在 SQL Server 或 SQL Azure 資料表中，產生設定資料類型的資料行的條件約束。 如果是，還會提供已轉換的所有資料行集的資料類型，包含控制值的檢查條件約束。<br /><br />**預設模式**: 否<br /><br />**開放式模式**:否<br /><br />**完整模式**: 是|  
|**產生的不帶正負號的數值資料類型資料行的資料行的條件約束**|將新增核取為非負數值至不帶正負號的數值資料類型的資料行。<br /><br />**預設模式**: 否<br /><br />**開放式模式**:否<br /><br />**完整模式**: 是|  
|**產生一年的資料類型的資料行的條件約束**|如果它不會在 MySQL 資料表，請在 SQL Server 或 SQL Azure 資料表中，產生一年的資料類型的資料行的條件約束。 如果是，轉換後的所有資料行的一年的資料型別還會提供包含控制值的檢查條件約束。<br /><br />**預設模式**: 否<br /><br />**開放式模式**:否<br /><br />**完整模式**: 是|  
  
### <a name="data-types"></a>資料型別  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**列舉資料類型轉換**|指定 MySQL 列舉資料型別應該如何轉換成轉換為 NVARCHAR 或轉換成數值<br /><br />**預設模式**:將轉換為 NVARCHAR<br /><br />**開放式模式**:將轉換為 NVARCHAR<br /><br />**完整模式**:將轉換為 NVARCHAR|  
|**資料類型轉換**|指定應如何設定 MySQL 資料類型轉換，轉換到 NVARCHAR (L) / 將轉換為 BINARY(L)<br /><br />**預設模式**:將轉換成 NVARCHAR(L)<br /><br />**開放式模式**:將轉換成 NVARCHAR(L)<br /><br />**完整模式**:將轉換成 NVARCHAR(L)|  
  
### <a name="generic"></a>泛型  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**資料行沒有預設值，在插入和取代**|如果 [是]，參考資料表使用 MyISAM 和 InnoDb 以外的儲存的引擎的所有陳述式，都應該標示為轉換的警告訊息。<br /><br />**預設模式**:將資料行清單<br /><br />**開放式模式**:將資料行清單<br /><br />**完整模式**: 將資料行清單|  
|**會產生除以零的轉換**|指定要模擬 MySQL 無 ERROR_FOR_DIVISION_BY_ZERO 行為。<br /><br />**預設模式**: 錯誤<br /><br />**開放式模式**:錯誤<br /><br />**完整模式**: NULL|  
|**IN 運算子**|指定如何將 MySQL IN 運算子的轉換。<br /><br />**預設模式**: 永遠將轉換成 IN<br /><br />**開放式模式**:永遠將轉換成 IN<br /><br />**完整模式**: 視需要展開|  
|**MySQL 函式轉換**|指定如何將轉換 MySQL 標準函式。<br /><br />**預設模式**: 開放式<br /><br />**開放式模式**:開放式<br /><br />**完整模式**: 精確|  
|**不支援儲存引擎**|如果 [是]，參考資料表使用 MyISAM 和 InnoDb 以外的儲存的引擎的所有陳述式，都應該標示為轉換的警告訊息。<br /><br />**預設模式**: 否<br /><br />**開放式模式**:否<br /><br />**完整模式**: 是|  
|**抑制 ROWID 輔助的資料行產生**|如果是，禁止 ROWD 輔助的資料行建立在目標資料表上建立。 可能會影響某些結構的移轉。<br /><br />**預設模式**: 否<br /><br />**開放式模式**:否<br /><br />**完整模式**: 否|  
|**TRUNCATE 陳述式轉換**|指定如何將轉換截斷陳述式。<br /><br />**預設模式**: TRUNCATE<br /><br />**開放式模式**:TRUNCATE<br /><br />**完整模式**: TRUNCATE|  
  
### <a name="misc"></a>其他  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**預設結構描述對應**|指定如何將 MySQL 資料庫對應至 SQL Server 結構描述。<br /><br />**預設模式**:資料庫的資料庫<br /><br />**開放式模式**:資料庫的資料庫<br /><br />**完整模式**:資料庫的資料庫|  
  
### <a name="procedures-and-functions"></a>程序及函數  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**預設函式轉換**|指定是否函式應該預設會轉換到 T-SQL 函數或預存程序。<br /><br />**預設模式**:將轉換成函式<br /><br />**開放式模式**:將轉換成函式<br /><br />**完整模式**:將轉換成函式|  
|**產生 SET XACT_ABORT 上**|指定要加入至轉換後的程序或觸發程序的開頭需要 SET XACT_ABORT ON。<br /><br />**預設模式**:是<br /><br />**開放式模式**:是<br /><br />**完整模式**:是|  
|**產生 SET NOCOUNT**|指定需要轉換的程序或觸發程序的開頭加入 SET NOCOUNT ON。<br /><br />**預設模式**:是<br /><br />**開放式模式**:是<br /><br />**完整模式**:是|  
  
### <a name="spatial-data-types"></a>空間資料類型  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**週框方塊的預設值 {XMAX&#124;XMIN&#124;YMAX&#124;YMIN} 為空間索引**|定義預設值 {XMAX&#124;XMIN&#124;YMAX&#124;YMIN} 的週框方塊中空間索引所使用的參數。<br /><br />**預設模式**<br /><br />XMAX:100<br /><br />XMIN:0<br /><br />YMAX:100<br /><br />YMIN:0<br /><br />**開放式的模式**<br /><br />XMAX:100<br /><br />XMIN:0<br /><br />YMAX:100<br /><br />YMIN:0<br /><br />**完整模式**<br /><br />XMAX:100<br /><br />XMIN:0<br /><br />YMAX:100<br /><br />YMIN:0|  
|**預設為空間索引的的方格密度**|為 LEVEL_1、 LEVEL_2、 LEVEL_3 和用於空間索引的方格密度的 LEVEL_4 定義預設值。<br /><br />**預設模式**<br /><br />LEVEL_1:預設<br /><br />LEVEL_2:預設<br /><br />LEVEL_3:預設<br /><br />LEVEL_4:預設<br /><br />**開放式的模式**<br /><br />LEVEL_1:預設<br /><br />LEVEL_2:預設<br /><br />LEVEL_3:預設<br /><br />LEVEL_4:預設<br /><br />**完整模式**<br /><br />LEVEL_1:預設<br /><br />LEVEL_2:預設<br /><br />LEVEL_3:預設<br /><br />LEVEL_4:預設|  
  
### <a name="transactions"></a>交易  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**非交易式資料表**|指定轉換的警告訊息應該標示所有資料表的參考，不支援交易。<br /><br />**預設模式**:否<br /><br />**開放式模式**:否<br /><br />**完整模式**:是|  
|**交易隔離等級**|指定新的交易應該使用何種交易隔離等級。<br /><br />**預設模式**: 預設<br /><br />**開放式模式**:預設<br /><br />**完整模式**: 可重複讀取|  
  
### <a name="value-control"></a>值控制項  
  
|||  
|-|-|  
|**詞彙**|**[定義]**|  
|**數值轉換的字元**|指定如何處理隱含和明確從字元資料類型轉換成數值資料類型。<br /><br />**預設模式**: 開放式<br /><br />**開放式模式**:開放式<br /><br />**完整模式**: 精確|  
|**控制不帶正負號的數字值**|將值指派給不帶正負號的數值變數和參數的控制項。<br /><br />**預設模式**: 否<br /><br />**開放式模式**:否<br /><br />**完整模式**: 是|  
|**控制項不帶正負號的減法運算**|修改插入至資料表資料行的不帶正負號的資料類型的負值。<br /><br />**預設模式**: 轉換 ' 做為-是 '<br /><br />**開放式模式**:轉換 ' 做為-是 '<br /><br />**完整模式**: 以警告標記|  
|**二進位資料型別來回轉換**|指定如何處理從二進位資料類型的隱含和明確轉換。<br /><br />**預設模式**: 開放式<br /><br />**開放式模式**:開放式<br /><br />**完整模式**: 精確|  
|**轉換成日期/時間資料類型**|指定如何處理隱含和明確轉換成日期/時間資料類型。<br /><br />**預設模式**: 模擬 MySQL 格式<br /><br />**開放式模式**:使用 SQL Server 格式<br /><br />**完整模式**: 模擬 MySQL 格式|  
|**具有超過 38 的有效位數的數值常值**|指定如何將數值常值轉換具有有效位數超過 38。<br /><br />**預設模式**: 如果可能的話四捨五入<br /><br />**開放式模式**:如果可能的話四捨五入<br /><br />**完整模式**: 如果可能的話四捨五入|  
|**NOT NULL 資料行中的零-日期**|指定如何處理 NOT NULL 資料行的零日期，在日期中零或無效的日期/時間值的指派。<br /><br />**預設模式**: GETDATE （)<br /><br />**開放式模式**:GETDATE （)<br /><br />**完整模式**: GETDATE （)|  
  
## <a name="see-also"></a>另請參閱  
[使用者介面參考&#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
  
