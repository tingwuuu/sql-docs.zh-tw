---
title: RSWindowsExtendedProtectionLevel 屬性 (WMI MSReportServer_ConfigurationSetting) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c3c4fdbf8642715a895e8c345ccd171c53ca3509
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59944844"
---
# <a name="rswindowsextendedprotectionlevel-property-wmi-msreportserverconfigurationsetting"></a>RSWindowsExtendedProtectionLevel 屬性 (WMI MSReportServer_ConfigurationSetting)
  傳回字串值，表示報表伺服器設定為支援的保護等級。 此屬性是唯讀的。  
  
## <a name="syntax"></a>語法  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a>備註  
 傳回字串值，表示報表伺服器設定為支援的保護等級。 如果 WMI 提供者連線的報表伺服器不支援擴充保護，則會傳回 "" (空字串)。 下列清單顯示有效值：  
  
 `"Off" | "Allow" | "Require"`  
  
## <a name="example-code"></a>範例程式碼  
 [MSReportServer_ConfigurationSetting 類別](msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>另請參閱  
 [RSWindowsExtendedProtectionScenario 屬性 &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [SetExtendedProtectionSettings 方法 &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setextendedprotectionsettings.md)   
 [Reporting Services 的驗證擴充保護](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [RSReportServer 設定檔](../report-server/rsreportserver-config-configuration-file.md)  
  
  
