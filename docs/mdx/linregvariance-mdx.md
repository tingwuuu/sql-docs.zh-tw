---
title: LinRegVariance (MDX) |Microsoft 文件
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b3ae56238623c41d29ccb388a5aaa178352af196
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741227"
---
# <a name="linregvariance-mdx"></a>LinRegVariance (MDX)


  計算集合的線性迴歸，並傳回與迴歸線 y = ax + b。  
  
## <a name="syntax"></a>語法  
  
```  
  
LinRegVariance(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] ] )  
```  
  
## <a name="arguments"></a>引數  
 *Set_Expression*  
 傳回集合的有效多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression_y*  
 有效的數值運算式，這通常是傳回表示 Y 軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
 *Numeric_Expression_x*  
 有效的數值運算式，這通常是傳回表示 X 軸數值之資料格座標的多維度運算式 (MDX) 運算式。  
  
## <a name="remarks"></a>備註  
 線性迴歸利用最小平方法，計算迴歸線方程式 (也就是說，數點之間的最佳直線)。 迴歸線具有下列方程式，其中為斜率，b 是截距：  
  
 y = ax+b  
  
 **LinRegVariance**函式會評估指定的 setagainst 第一個數值運算式，以取得 y 軸的值。 如果指定，以取得 x 軸的值，此函式接著會評估指定的 setagainst 第二個數值運算式。 如果未指定第二個數值 expressionis，此函數會使用指定集合中的資料格目前內容的值當做 x 軸。 Time 維度經常不指定 X 軸引數。  
  
 取得數點之後, **LinRegVariance**函式會傳回描述線性方程式與點的符合程度統計變異數。  
  
> [!NOTE]  
>  **LinRegVariance**函式會忽略空白資料格包含文字或邏輯值。 不過，此函數包括值為零的資料格。  
  
## <a name="example"></a>範例  
 下列範例會傳回統計變異數，以描述線性方程式與單位銷售量和商店銷售量值點的符合程度。  
  
```  
LinRegVariance(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
