---
title: "檢視測試案例報表 (OracleToSQL) |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 99ee650698adb2536ebdcadf480ae0ccefda2628
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="viewing-test-case-reports-oracletosql"></a>檢視測試案例報表 (OracleToSQL)
測試案例報表會顯示測試驗證結果和一般測試的資訊。 如果測試失敗，也會顯示任何不相符的資料已經過驗證的物件的相關資訊。  
  
## <a name="report-structure"></a>報表結構  
報表的頂端顯示這些統計資料：  
  
-   測試的物件並測試成功的物件數目的總數。  
  
-   資料表和成功比對的外部索引鍵的數目以及驗證的資料表和外部索引鍵的總數。  
  
-   開始時間、 結束時間的測試案例和執行所花費的總時間。  
  
其餘的報表會顯示四個類別中的資訊：  
  
**先決條件錯誤**  
顯示在發生任何錯誤**先決條件步驟。** 通常，它會略過。  
  
**初始化**  
顯示做為執行狀態**成功**或**失敗**。  
  
**測試物件的結果**  
比較結果 （成功或失敗） 和 SSMA Tester 偵測到失敗時不相符。  
  
**最終處理**  
顯示做為執行狀態**成功**或**失敗**。  
  
## <a name="see-also"></a>另請參閱  
[執行測試案例 &#40; OracleToSQL &#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[測試移轉的資料庫物件 &#40; OracleToSQL &#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
