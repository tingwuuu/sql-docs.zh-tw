---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa6bce659e20fb80f013539049cc1b99e3e0b4c1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055238"
---
# <a name="mssqlserver10538"></a>MSSQLSERVER_10538
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|10538|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|PG_INVALID_PLANGUIDE_HANDLE|  
|訊息文字|找不到計畫指南，可能是因為指定的計畫指南識別碼是 NULL 或無效，或是因為您對計畫指南參考的物件不具有權限。 請確認計畫指南識別碼是否有效、目前工作階段是否設定為正確的資料庫內容，以及您是否具有計畫指南所參考物件的 ALTER DATABASE 權限或 ALTER 權限。|  
  
## <a name="explanation"></a>說明  
 指定之計畫指南的識別碼為 NULL 或無效，或者您對計畫指南所參考的物件沒有權限。  
  
## <a name="user-action"></a>使用者動作  
 請確認計畫指南識別碼是否有效、目前工作階段是否設定為正確的資料庫內容，以及您是否具有計畫指南所參考物件的 ALTER DATABASE 權限或 ALTER 權限。  
  
## <a name="see-also"></a>另請參閱  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [計畫指南](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
