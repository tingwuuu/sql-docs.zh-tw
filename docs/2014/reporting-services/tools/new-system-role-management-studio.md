---
title: 新增系統角色 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.newsystemrole.f1
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 33cf72fa9f82b4bf6fdbd8b1b5b2b73757706206
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59939184"
---
# <a name="new-system-role-management-studio"></a>新增系統角色 (Management Studio)
  使用此頁面，即可建立系統層級角色定義。 系統角色定義會指定一組整個套用至報表伺服器的系統層級工作。  
  
> [!NOTE]  
>  角色定義只會用於以原生模式執行的報表伺服器。 如果報表伺服器是針對 SharePoint 整合所設定，這個頁面就無法使用。  
  
## <a name="options"></a>選項。  
 **名稱**  
 鍵入角色定義的名稱。 角色定義名稱在報表伺服器命名空間內必須是唯一的。 名稱必須至少包含一個英數字元。 它也可以包含空格和某些符號。 指定名稱時，請勿使用下列字元：  
  
 ; ? : \@ & = + , $ / * \< >  
  
 " /  
  
 **說明**  
 提供如何使用角色的描述，並列舉該角色支援的項目。  
  
 **工作**  
 選取可以透過此角色所執行的系統層級工作。 您無法建立新工作，或修改 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]支援的現有工作。 您無法為系統角色定義選擇項目層級工作。  
  
 **工作描述**  
 顯示工作的描述，其中列舉出工作能夠支援的作業或權限。  
  
## <a name="see-also"></a>另請參閱  
 [Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md)   
 [角色定義](../security/role-definitions.md)  
  
  
