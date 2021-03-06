---
title: 使用 WQL 與指令碼與組態管理的 WMI 提供者的語言 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cc9994d4429e82f2bdd4f40797df1c5f628c6500
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52784120"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a>搭配組態管理的 WMI 提供者使用 WQL 與指令碼語言
  管理應用程式會以兩種方式，使用組態管理物件的 Windows Management Instrumentation (WMI) 提供者，存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務與網路設定：  
  
-   使用 WQL 編輯器或查詢工具 (例如，WBEMTest.exe) 來查訊利用 Windows Management Instrumentation 語言 (WQL) 設定的物件。  
  
-   使用指令碼語言，例如 VBScript。  
  
 或者，可以使用 SMO 中的 WMI Managed 物件，以程式設計方式管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務與網路設定。 如需程式設計 WMI managed 物件，請參閱 <<c0> [ 管理的服務和網路設定，使用 WMI 提供者所](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)。  
  
 組態管理的 WMI 提供者可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console 來進行存取。 如需有關從使用者介面存取 WMI 提供者的詳細資訊，請參閱 <<c0> [ 管理服務的如何主題&#40;SQL Server 組態管理員&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)。</c0>  
  
## <a name="see-also"></a>另請參閱  
 [存取 WMI 提供者使用 WQL 的組態管理](access-wmi-provider-for-configuration-management-using-wql.md)   
 [使用 VBScript 修改 SQL Server 服務進階屬性](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
