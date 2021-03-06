---
title: Web 服務工作編輯器 （輸入頁面） |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.input.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 93529c88-f540-47f2-a10a-12c87318ed6f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 29ca581697231a3aa70aa6f4342fcea3408d6c99
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58384426"
---
# <a name="web-service-task-editor-input-page"></a>Web 服務工作編輯器 (輸入頁面)
  使用 [Web 服務工作編輯器] 對話方塊的 [輸入] 頁面，即可指定 Web 服務、Web 方法，以及提供給 Web 方法的輸入值。 在 [值] 資料行中直接輸入字串，或是在 [值] 資料行中選取變數，即可提供這些值。  
  
 若要了解這個工作，請參閱 [Web 服務工作](control-flow/web-service-task.md)。  
  
## <a name="options"></a>選項。  
 **服務**  
 從清單中選取要用於執行 Web 方法的 Web 服務。  
  
 **方法**  
 從清單中選取要用於執行工作的 Web 方法。  
  
 **WebMethodDocumentation**  
 鍵入 Web 方法的描述，或按一下瀏覽按鈕 **(...)**，然後在 [Web 方法文件集] 對話方塊中鍵入描述。  
  
 **名稱**  
 列出 Web 方法之輸入的名稱。  
  
 **型別**  
 列出輸入的資料類型。  
  
> [!NOTE]  
>  「Web 服務」工作只支援下列資料類型的參數：基本類型 (如整數和字串)、基本類型的陣列和順序以及列舉。  
  
 **變數**  
 選取該核取方塊，即可使用變數來提供輸入。  
  
 **值**  
 如果選取了 [變數] 核取方塊，請從清單中選取要用於提供輸入的變數，否則請直接輸入要用於輸入的值。  
  
## <a name="see-also"></a>另請參閱  
 [Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Web 服務工作編輯器 &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md)   
 [Web 服務工作編輯器 &#40;輸出頁面&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [運算式頁面](expressions/expressions-page.md)  
  
  
