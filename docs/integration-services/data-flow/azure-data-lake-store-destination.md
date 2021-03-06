---
title: Azure Data Lake Store 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSDEST.F1
- sql14.dts.designer.afpadlsdest.f1
ms.assetid: 4c4f504f-dd2b-42c5-8a20-1a8ad9a5d632
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 89f94d89bdc5249881e66fe884eda18bb81018d6
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2019
ms.locfileid: "58280632"
---
# <a name="azure-data-lake-store-destination"></a>Azure Data Lake Store 目的地
  **Azure Data Lake Store 目的地** 元件可讓 SSIS 套件將資料寫入 Azure Data Lake Store。 支援的檔案格式：文字、Avro 和 ORC。 
  
 **Azure Data Lake Store 目的地**是 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) 的元件。
 
> [!NOTE]
> 為確保 Azure Data Lake Store 連線管理員及使用它的元件 (即 Azure Data Lake Store 來源及 Azure Data Lake Store 目的地) 能夠連接服務，請務必從 [這裡](https://www.microsoft.com/download/details.aspx?id=49492)下載最新版的 Azure Feature Pack。 

## <a name="configure-the-azure-data-lake-store-destination"></a>設定 Azure Data Lake Store 目的地  
1. 將 **Azure Data Lake Store 目的地** 拖放到資料流程設計師，然後在上面按兩下以查看編輯器。  

2.  在 [Azure Data Lake Store 連線管理員]  欄位指定現有的 Azure Data Lake Store 連線管理員，或建立參考 Azure Data Lake Store 服務的新連線管理員。  
  
    1.  在 [檔案路徑]  欄位指定想要寫入資料的檔案名稱。 如果此檔案已經存在，則會覆寫其內容。  
  
    2.  在 [檔案格式]  欄位指定想要使用的檔案格式。  
  
       檔案格式若為文字，則您必須指定 [資料行分隔符號字元]  值。 若檔案中第一個資料列包含資料行名稱，請選取 [第一個資料列的資料行名稱]  。  

       如果檔案格式是 ORC，您會需要為適當的平台安裝 Java Runtime Environment (JRE)。
  
3.  指定連接資訊後，請切換至 [資料行]  頁面，將來源資料行對應至 SSIS 資料流程的目的地資料行。  
