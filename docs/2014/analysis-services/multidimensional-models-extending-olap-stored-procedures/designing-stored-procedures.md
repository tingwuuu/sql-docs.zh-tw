---
title: 設計預存程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b05a4b7b1fe1c8ee70692472dc69105f01a275e0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164428"
---
# <a name="designing-stored-procedures"></a>設計預存程序
  管理的物件模型分析管理物件 (AMO) 和用戶端導向的物件模型 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (多維度) (ADO MD)，二者都可在預存程序中使用。  
  
 預存程序必須在被呼叫的多維度運算式 (MDX) 層級可以看見的範圍內 (伺服器或資料庫)。 不過，一旦叫用預存程序後，其範圍就不限於其父系下的動作。 預存程序可以在伺服器上的任何位置進行變更或修改，只受限於叫用它之使用者處理序的安全性限制，或是它正在執行之交易的限制。  
  
 伺服器範圍的程序可以在伺服器的所有內容中使用。 資料庫範圍的預存程序，只有在定義它們之資料庫的資料庫內容中才看得見。  
  
 如同所有的 MDX 函數，必須先解析預存程序才能繼續 MDX 工作階段；在執行時，預存程序會鎖定 MDX 工作階段。 除非有特定原因需暫止 MDX 工作階段，等候使用者互動，否則不建議使用者互動 (例如對話方塊)。  
  
## <a name="dependent-assemblies"></a>相依組件  
 所有相依組件都必須載入 Common Language Runtime (CLR) 所要尋找的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體中。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會將相依組件儲存在與主組件相同的資料夾中，所以 CLR 會自動解析組件中函數的所有函數參考。  
  
## <a name="see-also"></a>另請參閱  
 [多維度模型組件管理](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [定義預存程序](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
