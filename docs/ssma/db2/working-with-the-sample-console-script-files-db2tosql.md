---
title: 使用範例主控台指令碼檔 (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5c3080c3-d074-4f99-a5f5-219ebeddc474
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: dc7976fae322dddc24eda7cf6ef84ef20a7a9e61
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2018
ms.locfileid: "52394927"
---
# <a name="working-with-the-sample-console-script-files-db2tosql"></a>使用範例主控台指令碼檔 (DB2ToSQL)
幾個範例檔案，以及產品提供的使用者參考和使用方式。 本章節描述的方式，輕鬆地自訂這些指令碼，以符合使用者需求。  
  
## <a name="sample-console-script-files"></a>範例主控台指令碼檔  
使用者參考已提供下列範例主控台指令碼檔涵蓋不同的案例：  
  
-   ServersConnectionFileSample.xml  
  
-   VariableValueFileSample.xml  
  
-   AssessmentReportGenerationSample.xml  
  
-   SqlStatementConversionSample.xml  
  
-   ConversionAndDataMigrationSample.xml  
  
1.  **ServersConnectionFileSample.xml:**  
  
    -   此範例可讓來源和目標資料庫的連線使用不同的模式，使用者可以選取任何根據需求的模式。 此範例包含伺服器定義。  
  
    -   使用者可以連接到所需的資料庫，只要變更所需的來源和目標伺服器定義的值。 在範例中提供所有已提供值，變數的值中，您可以使用哪些**VariableValueFileSample.xml**。  可以從使用者的處理伺服器連線檔案中移除所有其他連接參數。  
  
    -   如需有關如何連接到來源和目標伺服器的詳細資訊，請參閱 <<c0> [ 建立伺服器連線檔案&#40;DB2ToSQL&#41; ](../../ssma/db2/creating-the-server-connection-files-db2tosql.md) 。</c0>  
  
2.  **VariableValueFileSample.xml:** 已使用範例主控台中的所有變數指令都碼檔案和`ServersConnectionFileSample.xml`已定序，此檔案中。 使用者已取代範例變數的範例主控台指令碼的執行值與使用者定義的並將這個檔案傳遞做為其他命令列引數，以及指令碼檔案。  
  
    如需有關變數值檔案的詳細資訊，請參閱[建立變數值檔案&#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)。  
  
3.  **AssessmentReportGenerationSample.xml:** 此範例中，可讓使用者產生的 xml 評定報告可以用於由使用者分析他開始轉換並移轉資料之前。  
  
    在`generate-assessment-report`命令的使用者具有 mandatorily 變更變數的值 (請參閱**VariableValueFileSample.xml**) 中`object-name`屬性加入資料庫使用者所使用的名稱所。 根據指定的物件種類`object-type`值也會變更。  
  
    如果使用者需要評估多個物件 / 資料庫他可以指定多個`metabase-object`節點中所示`generate-assessment-report`命令的範例 4 的範例主控台指令碼檔案。  
  
    如需有關如何產生報告的詳細資訊，請參閱 <<c0> [ 產生的報表&#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md)。</c0>  
  
    **注意：**  
  
    請確定變數值檔案的命令列引數傳遞至主控台應用程式，且 VariableValueFileSample.xml 會更新指定的使用者值。  
  
    請確認伺服器連線檔案命令列引數傳遞至主控台應用程式，然後 ServersConnectionFileSample.xml 已包含正確的伺服器參數值。  
  
4.  **SqlStatementConversionSample.xml:** 此範例可讓使用者產生對應`t-sql`來源資料庫的指令碼`sql`提供作為輸入的命令。  
  
    在`convert-sql-statement`命令的使用者具有 mandatorily 變更變數的值 (請參閱**VariableValueFileSample.xml**) 中`context`屬性正被使用者所使用的資料庫名稱。 使用者也必須變更`sql`屬性值的來源資料庫`sql`他/她需要轉換的命令。  
  
    使用者也可以提供要轉換的 sql 檔案。 這已在說明`convert-sql-statement`命令的範例 4 的範例主控台指令碼檔案。  
  
    > [!NOTE]  
    > 請確定變數值檔案的命令列引數傳遞至主控台應用程式，且 VariableValueFileSample.xml 會更新指定的使用者值。  
  
5.  **ConversionAndDataMigrationSample.xml:** 此範例可讓使用者從資料移轉至轉換執行端對端移轉。 一個強制屬性值，這些使用者必須先變更清單如下：  
  
    |命令名稱|描述|attribute|  
    |----------------|---------------|-------------|  
    |`map-schema`|目標結構描述的來源資料庫的結構描述對應。|`source-schema:` 指定轉換所需的來源資料庫。<br /><br />`sql-server-schema`:指定要移轉至目標資料庫|  
    |`convert-schema`|執行從來源到目標結構描述的結構描述轉換。<br /><br />如果使用者需要評估多個物件 / 資料庫他可以指定多個`metabase-object`節點中所示`convert-schema`命令的範例 4 的範例主控台指令碼檔案。|`object-name`:指定來源資料庫/物件轉換所需的名稱。 請確認對應`object-type`會依據物件中指定的類型變更 `object-name`|  
    |`synchronize-target`|會使用目標資料庫，同步處理的目標物件。<br /><br />如果使用者需要評估多個物件 / 資料庫他可以指定多個`metabase-object`節點中所示`synchronize-target`命令的範例 3 的範例主控台指令碼檔案。|`object-name:` 指定 sql server 資料庫/物件建立時所需的名稱。 請確認對應`object-type`會依據物件中指定的類型變更 `object-name`|  
    |`migrate-data`|將來源資料移轉至目標。<br /><br />如果使用者需要評估多個物件 / 資料庫他可以指定多個`metabase-object`節點中所示`migrate-data`命令的範例 2 的範例主控台指令碼檔案。|`object-name:` 指定來源資料庫/資料表移轉所需的名稱。 請確認對應`object-type`會依據物件中指定的類型變更 `object-name`|  
  
## <a name="see-also"></a>另請參閱  
[建立變數值檔案&#40;DB2ToSQL&#41;](../../ssma/db2/creating-variable-value-files-db2tosql.md)  
[建立伺服器連線檔案&#40;DB2ToSQL&#41;](../../ssma/db2/creating-the-server-connection-files-db2tosql.md)  
[產生報告&#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md)  
  
