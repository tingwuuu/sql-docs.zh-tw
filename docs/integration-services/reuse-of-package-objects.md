---
title: "重複使用封裝物件 |Microsoft 文件"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GUID regenerating [Integration Services]
- reusing packages
- templates [Integration Services]
- copying packages
- regenerating package GUID
ms.assetid: 08f723bf-15b5-44bd-9a46-04e8781bfbfb
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 31653debba3400f6a5f3a5b23474bd3055e02522
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="reuse-of-package-objects"></a>重複使用封裝物件
  您要重複使用的常用封裝功能。 例如，如果建立了一組工作，您可能想要以群組方式重複使用這些項目，您也可能想重複使用單一項目，例如您在不同的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中建立的連接管理員。  
  
## <a name="copy-and-paste"></a>複製與貼上  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」支援複製及貼上封裝物件的功能，這些物件可以包括控制流程項目、資料流程項目和連接管理員。 您可以在專案之間和封裝之間執行複製和貼上功能。 如果方案包含多個專案，您可以在專案之間進行複製，而且專案可以屬於不同類型。  
  
 如果方案包含多個封裝，您可以在這些封裝之間進行複製和貼上。 這些封裝可以位於相同或不同的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中。 不過，封裝物件可能具有其他物件的相依性，如果缺少這些相依性，物件便無效。 例如，您必須複製「執行 SQL」工作所使用的連接管理員，才能讓工作發揮作用。 此外，某些封裝物件要求封裝必須已經包含某一特定物件，如果沒有這個物件，您就不能成功地將複製的物件貼到封裝中。 例如，您不能將資料流程貼到沒有任何「資料流程」工作的封裝中。  
  
 您可能會發現自己重複複製了相同的封裝。 若要避免複製處理，您可以將這些封裝指定成範本，並在建立新封裝時使用這些範本。  
  
 複製封裝物件時， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會自動指定新的 GUID 給新物件的 **ID** 屬性，並更新 **Name** 屬性。  
  
 您無法複製變數。 如果工作之類的物件使用了變數，則您必須在目的地封裝中重新建立變數。 相反地，如果您複製整個封裝，也會一併複製封裝中的變數。  
  
## <a name="related-tasks"></a>相關工作  
  
-   [複製封裝物件](../integration-services/copy-package-objects.md)  
  
-   [複製專案項目](http://msdn.microsoft.com/library/1606c54d-20f9-49f3-a4ef-caad83a772aa)  
  
-   [將封裝儲存為封裝範本](http://msdn.microsoft.com/library/efe66cec-3933-4f6e-8d35-fe3d300de66c)  
  
  