---
title: SELECT FROM&lt;結構&gt;。案例 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 65ab4d5ebf1fbe64d3e85854df186d9ebe098e84
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600058"
---
# <a name="select-from-ltstructuregtcases"></a>SELECT FROM&lt;結構&gt;。案例
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  傳回用於建立採礦結構的案例。  
  
 如果結構上未啟用鑽研，則陳述式會失敗。 同時，如果使用者沒有採礦結構的鑽研權限，陳述式將會失敗。  
  
 在  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，預設會啟用新的採礦結構的鑽研。 若要確認是否針對特定結構啟用鑽研，請檢查是否的值**CacheMode**屬性設定為**KeepTrainingCases**。  
  
 如果值**CacheMode**變更為**ClearAfterProcessing**、 從快取清除結構案例，而且您無法使用鑽研。  
  
> [!NOTE]  
>  您無法使用資料採礦延伸模組 (DMX)，在採礦結構上啟用或停用鑽研。  
  
## <a name="syntax"></a>語法  
  
```  
  
SELECT [TOP n] <expression list> FROM <structure>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引數  
 *n*  
 選擇性。 指定要傳回多少資料列的整數。  
  
 *運算式清單*  
 逗號分隔的運算式清單。  
  
 運算式可以包含資料行識別碼、使用者定義函數，以及 VBA 函數。  
  
 *結構*  
 結構的名稱。  
  
 *條件運算式*  
 限制從資料行清單傳回之值的條件。  
  
 *expression*  
 選擇性。 傳回純量值的運算式。  
  
## <a name="remarks"></a>備註  
 如果同時在模型和結構上都啟用鑽研，具有採礦結構和模型之鑽研權限的任何角色成員都可以使用下列語法，傳回不包含在模型中的結構資料行：  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 因此，若要保護敏感性資料或個人資訊，您應該建構您的資料來源檢視來遮罩個人資訊，並授與**AllowDrillthrough**採礦結構或採礦模型權限時，才必要。  
  
## <a name="examples"></a>範例  
 下列範例以採礦結構中，目標郵寄 」，此作業取決於[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]資料庫和相關聯的採礦模型。 如需詳細資訊，請參閱 < [83c8-9df5dddfeb9c"&gt;basic Data Mining Tutorial&lt](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)。  
  
### <a name="example-1-drill-through-to-structure-cases"></a>範例 1：鑽研結構案例  
 下列範例會傳回採礦結構「目標郵寄」中，最舊的 500 位客戶的清單。 此查詢會傳回採礦模型中的所有資料行，但會將資料列限制為購買自行車的客戶，並以年齡加以排序。 您也可以編輯運算式清單，僅傳回您需要的資料行。  
  
```  
SELECT TOP 500 *  
FROM [Targeted Mailing].Cases  
WHERE [Bike Buyer] = 1  
ORDER BY Age DESC;  
```  
  
### <a name="example-2-drillthrough-to-test-or-training-cases-only"></a>範例 2：僅鑽研測試或培訓案例  
 下列範例會針對為測試而保留的「目標郵寄」，傳回結構案例的清單。 如果採礦結構不包含鑑效組測試集，系統預設會將所有案例視為培訓案例，因此，此查詢會傳回 0 個案例。  
  
```  
SELECT [Customer Key], Gender, Age  
FROM [Targeted Mailing].Cases  
WHERE IsTestCase();  
```  
  
 若要傳回培訓案例，取代函數 `IsTrainingCase()`。  
  
## <a name="see-also"></a>另請參閱  
 [選取&AMP;#40;DMX&AMP;#41;](../dmx/select-dmx.md)   
 [資料採礦延伸模組&#40;DMX&#41;資料定義陳述式](../dmx/dmx-statements-data-definition.md)   
 [資料採礦延伸模組&#40;DMX&#41;資料操作陳述式](../dmx/dmx-statements-data-manipulation.md)   
 [資料採礦延伸模組 &#40;DMX&#41; 陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
