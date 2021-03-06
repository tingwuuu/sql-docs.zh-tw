---
title: 第 5 課：加入封裝部署模型的封裝組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 25922725e202bc7b38e2c6141a097df1af119ed2
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2019
ms.locfileid: "58378826"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a>第 5 課：加入封裝部署模型的封裝組態
  封裝組態可讓您從開發環境之外設定執行階段屬性和變數。 組態可讓您開發彈性且易於部署和散發的封裝。 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會提供下列組態類型：  
  
-   XML 組態檔  
  
-   環境變數  
  
-   登錄項目  
  
-   父封裝變數  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表  
  
 在這一課，您將修改簡單[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]您在建立封裝的[第 4 課：加入錯誤流程重新導向](lesson-4-add-error-flow-redirection-with-ssis.md)使用封裝部署模型，並利用封裝組態。 您也可以複製此教學課程所包含之已完成的第 4 課封裝。 使用封裝組態精靈，您可以建立一個 XML 組態，利用一個對應至 Directory 屬性的封裝層級變數，來更新 Foreach 迴圈容器的 `Directory` 屬性。 建立組態檔之後，您可以從開發環境之外修改變數的值，並將已修改的屬性指向新的範例資料夾。 當您再次執行封裝、 組態檔會填入變數的值和變數會更新`Directory`屬性。 因此，封裝會反覆執行新儲存資料的資料夾之檔案，而不反覆執行以寫入程式碼的方式寫入封裝內之原始資料夾的檔案。  
  
> [!IMPORTANT]  
>  這個教學課程需要 **AdventureWorksDW2012** 範例資料庫。 如需更多有關如何安裝和部署 **AdventureWorksDW2012**的資訊，請參閱 [CodePlex 上 Reporting Services 產品範例專案](https://go.microsoft.com/fwlink/?LinkID=526910)。  
  
## <a name="lesson-tasks"></a>課程工作  
 這一課包含下列工作：  
  
-   [步驟 1：複製第 4 課套件](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [步驟 2：啟用和設定封裝組態](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [步驟 3：修改 Directory 屬性組態值](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [步驟 4：測試第 5 課的教學課程封裝](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a>開始課程  
  
-   [步驟 1：複製第 4 課套件](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
