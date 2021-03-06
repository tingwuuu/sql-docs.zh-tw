---
title: rsServerConfigurationError - Reporting Services 錯誤 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a5b89e0e1a9034327e531eda8dd4e1c68997bc9f
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59966884"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a>rsServerConfigurationError - Reporting Services 錯誤
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件識別碼|rsServerConfiguration|  
|事件來源|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|元件|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|訊息文字|報表伺服器發生組態錯誤。|  
  
## <a name="explanation"></a>說明  
 這是一般用途錯誤，當報表伺服器或報表撰寫工具具有無效的組態設定時，就會發生此錯誤。 此錯誤通常伴隨著陳述錯誤之實際原因的第二則訊息。  
  
 下列清單摘要列出可能的原因：  
  
-   找不到或無法讀取 RSReportServer.config 或 RSReportDesigner.config 檔案。  
  
-   組態檔中的 XML 元素遺失或無效。  
  
-   一或多個 XML 元素的值遺失或無效。  
  
-   登錄設定無效。  
  
## <a name="user-action"></a>使用者動作  
 如果當您在手動編輯組態檔之後開始發生這個錯誤，請移除您的變更並輸入之前的值，或者如果您有備份則還原舊版。  
  
 若要檢閱伴隨著其他錯誤訊息資訊`rsServerConfiguration`錯誤，請檢閱位於 \Microsoft SQL Server\MSRS12 報表伺服器追蹤記錄檔。\<執行個體名稱 > services\logfiles。 如需詳細資訊，請參閱 [Reporting Services 記錄檔和來源](../report-server/reporting-services-log-files-and-sources.md)。  
  
## <a name="internal-only"></a>僅供內部使用  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 組態檔](../report-server/reporting-services-configuration-files.md)   
 [修改 Reporting Services 組態檔 &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
