---
title: 結構描述元素 (DTA) 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74e72deb65d3f693e309926870174ebe72817c3e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2018
ms.locfileid: "52769400"
---
# <a name="schema-element-for-database-dta"></a>資料庫的 Schema 元素 (DTA)
  指定您要微調之資料庫的結構描述。  
  
## <a name="syntax"></a>語法  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>元素特性  
  
|特性|描述|  
|--------------------|-----------------|  
|**資料類型和長度**|無。|  
|**預設值**|無。|  
|**出現次數**|**Server** 元素之下所指定的 **Database** 元素需要使用這個元素一次。|  
  
## <a name="element-relationships"></a>元素關聯性  
  
|關聯性|元素|  
|------------------|--------------|  
|**父元素**|[伺服器的 Database 元素 &#40;DTA&#41;](database-element-for-server-dta.md)|  
|**子元素**|[結構描述的 Name 元素 &#40;DTA&#41;](name-element-for-schema-dta.md)<br /><br /> [結構描述的 Table 元素 &#40;DTA&#41;](table-element-for-schema-dta.md)|  
  
## <a name="example"></a>範例  
 如需此元素的使用範例，請參閱 [Server 元素 &#40;DTA&#41;](server-element-dta.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
