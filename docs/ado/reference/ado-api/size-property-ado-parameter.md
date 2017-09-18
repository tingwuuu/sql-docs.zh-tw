---
title: "Size 屬性 （ADO 參數） |Microsoft 文件"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Parameter::Size
helpviewer_keywords:
- Size property [ADO Parameter]
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 73a6f0f2cd2e0d59ba6cd3e581e9f2aab8934c5f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/09/2017

---
# <a name="size-property-ado-parameter"></a>Size 屬性 （ADO 參數）
指出的大小上限，以位元組或字元，[參數](../../../ado/reference/ado-api/parameter-object.md)物件。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回**長**值，指出位元組或字元的中值的最大大小**參數**物件。  
  
## <a name="remarks"></a>備註  
 使用**大小**屬性來判斷最大值寫入或讀取[值](../../../ado/reference/ado-api/value-property-ado.md)屬性**參數**物件。  
  
 如果您指定的可變長度資料型別**參數**物件 (例如，任何**字串**類型，例如**adVarChar**)，您必須設定物件的**大小**屬性，才能附加至[參數](../../../ado/reference/ado-api/parameters-collection-ado.md)集合; 否則就會發生錯誤。  
  
 如果您已經有附加**參數**物件**參數**集合[命令](../../../ado/reference/ado-api/command-object-ado.md)物件，而且您變更其類型為可變長度資料類型，您必須設定**參數**物件的**大小**屬性，才能執行**命令**物件; 否則就會發生錯誤。  
  
 如果您使用[重新整理](../../../ado/reference/ado-api/refresh-method-ado.md)從提供者，並取得參數資訊的方法會傳回一或多個可變長度資料型別**參數**物件 ADO 可能配置的記憶體為基礎的參數在其最大潛在大小，這可能會導致在執行期間發生錯誤。 若要避免發生錯誤，您應該明確設定**大小**這些參數執行命令之前的屬性。  
  
 **大小**屬性是讀取/寫入。  
  
## <a name="applies-to"></a>適用於  
 [參數物件](../../../ado/reference/ado-api/parameter-object.md)  
  
## <a name="see-also"></a>另請參閱  
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向屬性範例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向屬性範例 （VC + +）](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向屬性範例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Size 屬性 （ADO 資料流）](../../../ado/reference/ado-api/size-property-ado-stream.md)
