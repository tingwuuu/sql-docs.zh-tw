---
title: 書籤 C 資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b81acf6c60bd11e03a598e349e145dbf72e174b4
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53205287"
---
# <a name="bookmark-c-data-type"></a>書籤 C 資料類型
書籤 C 資料類型可讓應用程式擷取書籤。 書籤 C 類型僅用於擷取書籤值可以是可變長度;它們不應該轉換成其他資料型別。 應用程式會擷取從資料行 0 的結果集的書籤**SQLBulkOperations** （與 SQL_ADD 的作業）， **SQLFetch**， **SQLFetchScroll**，或**SQLGetData**。 如需詳細資訊，請參閱 <<c0> [ 書籤](../../../odbc/reference/develop-app/bookmarks-odbc.md)。  
  
 下表列出的值*CType*書籤 C 資料類型，可實作書籤 C 資料類型，與此資料定義的 ODBC C 資料類型則是從 SQL 類型。H.  
  
> [!NOTE]
>  SQL_C_BOOKMARK 資料型別已被取代。 ODBC 3 *.x*應用程式不應使用 SQL_C_BOOKMARK。 ODBC 3 *.x*驅動程式需要他們想要使用 ODBC 2 時，才支援 SQL_C_BOOKMARK。*x*使用它的應用程式。 驅動程式管理員會將 SQL_C_VARBOOKMARK 對應至 SQL_C_BOOKMARK 中，當應用程式會使用 ODBC 2。*x*驅動程式。  
  
|C 類型識別碼|ODBC C typedef|C 類型|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(已被取代)|書籤|不帶正負號的 long int|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
