---
title: 從資料庫 (DB2ToSQL) 重新整理 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 613a8368-b372-443f-8252-fb6dc31a003d
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ef7778854248f194c01254b9cd6f833f67e9cefc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685116"
---
# <a name="refresh-from-database-db2tosql"></a>從資料庫 (DB2ToSQL) 重新整理
**從資料庫重新整理**對話方塊可讓您選取要從 DB2 資料庫重新整理的物件。 在對話方塊中的資料列的色彩標示根據中繼資料的狀態：  
  
-   如果在本機和 DB2 資料庫中，已變更物件中繼資料，資料列會變成藍色。  
  
-   如果在 DB2 資料庫，但不是在 SSMA 中，已變更物件中繼資料，資料列是黃色。  
  
-   如果已在本機變更物件中繼資料，但不是在 DB2 資料庫中，資料列是綠色。  
  
-   如果是新 DB2 資料庫中的物件，資料列是粉紅色。  
  
您可以指定中的預設物件重新整理設定**專案設定** 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 專案設定&#40;同步處理&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)。</c0>  
  
若要存取**從資料庫重新整理** 對話方塊中，以滑鼠右鍵按一下物件，在 DB2 中繼資料總管，然後按一下**從資料庫重新整理**。  
  
## <a name="options"></a>選項。  
**摺疊 （-）**  
摺疊所有的物件群組，若要隱藏個別的物件。  
  
**展開 （+）**  
展開以顯示個別物件的所有物件群組。  
  
**隱藏/顯示相等的物件**  
如果物件中繼資料相同的 SSMA 和 DB2 資料庫中，會隱藏清單中的物件。  
  
**從資料庫 （箭號按鈕） 重新整理**  
指定所選物件的中繼資料，應該更新 SSMA 中使用的箭號按鈕。  
  
**從資料庫中執行 重新整理 (X 按鈕）**  
您可以使用 [X] 按鈕，指定不應在 SSMA 中更新所選物件的中繼資料。  
  
**圖例**  
顯示**圖例** 對話方塊。 圖例會包含資料列的色彩和中繼資料狀態之間的對應。  
  
保留**圖例**對話方塊的上方**從資料庫重新整理**對話方塊中，選取**顯示在最上層**核取方塊。  
  
