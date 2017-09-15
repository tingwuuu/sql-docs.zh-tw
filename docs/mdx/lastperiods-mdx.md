---
title: "LastPeriods (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LASTPERIODS
dev_langs:
- kbMDX
helpviewer_keywords:
- LastPeriods function
ms.assetid: a15df7a1-b261-48ed-aacc-d2804db8dbf7
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dc24f14f734c697946226974a8d51761a6d8182e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回指定成員之前的成員集合 (包含指定成員)。  
  
## <a name="syntax"></a>語法  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>引數  
 *索引*  
 指定週期數目的有效數值運算式。  
  
 *Member_Expression*  
 傳回成員的有效多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 如果指定的週期數目是正數， **LastPeriods**函式會傳回一組成員之後的第開頭的成員*索引*-1，從指定的成員運算式，且結尾為指定的成員。 函數所傳回的成員數目等於*索引*。  
  
 如果指定的週期數目是負數， **LastPeriods**函式會傳回一組的開頭指定成員的成員和成員，會導致以結束 (-*索引*-1) 從指定的成員。 函數所傳回的成員數目等於數值的絕對值*索引*。  
  
 如果指定的週期數目為零， **LastPeriods**函式會傳回空集合。 這是與不同的是**延隔**函式，如果指定 0 時，傳回指定的成員。  
  
 如果未指定成員， **LastPeriods**函式使用**Time.CurrentMember**。 如果沒有維度標示為 Time 維度，此函數將會剖析，並且在不發生錯誤的情況下執行，但會在用戶端應用程式中造成資料格錯誤。  
  
## <a name="examples"></a>範例  
 下列範例會傳回 2002 會計年度第二、第三、第四會計季度的預設量值。  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  這個範例也可以使用 : (冒號) 運算子撰寫如下：  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 下列範例會傳回 2002 會計年度第一個會計季度的預設量值。 雖然指定的週期數是三，但是只會傳回一個，因為該會計年度中沒有更早的週期。  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
