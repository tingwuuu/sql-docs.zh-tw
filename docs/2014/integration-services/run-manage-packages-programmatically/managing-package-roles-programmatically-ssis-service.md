---
title: 以程式設計方式管理套件角色 (SSIS 服務) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e9ef79cf487044c9d3e07b0637d585c03daac0b4
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385306"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>以程式設計方式管理封裝角色 (SSIS 服務)
  當您以程式設計方式使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時，可能會想要判斷有哪些角色可供套用至封裝，或是判斷或設定套用至個別封裝的角色。 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 命名空間的 <xref:Microsoft.SqlServer.Dts.Runtime> 類別，提供各種方法以滿足這些需求。  
  
 角色只能套用到儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** 資料庫的套件中。 如需套件角色的詳細資訊，請參閱 [Integration Services 角色 &#40;SSIS 服務&#41;](../security/integration-services-roles-ssis-service.md)。  
  
 本主題中討論的所有方法都需要 `Microsoft.SqlServer.ManagedDTS` 組件的參考。 在新專案中加入參考之後，請使用 `using` 或 `Imports` 陳述式匯入 <xref:Microsoft.SqlServer.Dts.Runtime> 命名空間。  
  
> [!IMPORTANT]  
>  用以搭配 SSIS 封裝存放區使用的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 類別之方法，僅支援 "."、localhost 或是本機伺服器的伺服器名稱。 您無法使用 "(local)"。  
  
## <a name="determining-which-roles-are-available"></a>判斷可以使用哪些角色  
 若要判斷有哪些角色可供儲存在特定伺服器上的封裝使用，請呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> 類別的 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 方法。  
  
## <a name="determining-which-roles-are-assigned"></a>判斷已指派哪些角色  
 若要判斷已將哪些角色指派到特定封裝，請呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A> 方法。 若要將角色指派到套件，請呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A> 方法。  
  
![Integration Services 圖示 （小）](../media/dts-16.gif "Integration Services 圖示 （小）")**保持最多包含 Integration Services 的日期**<br /> 若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：<br /><br /> [瀏覽 MSDN 上的 Integration Services 頁面](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 角色 &#40;SSIS 服務&#41;](../security/integration-services-roles-ssis-service.md)  
  
  
