---
title: SQLAllocConnect (Visual FoxPro ODBC Driver) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc05bae8e67098bb89345b1cf0333abae68397d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655926"
---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (Visual FoxPro ODBC Driver)
> [!NOTE]  
>  本主題包含 Visual FoxPro ODBC 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支援： 完整  
  
 ODBC API 一致性： 核心層級  
  
 配置連接控制代碼，記憶體*hdbc*，由識別環境內*henv*。 驅動程式管理員會處理此呼叫，並呼叫的驅動程式**SQLAllocConnect**每當[SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)， **SQLBrowseConnect**，或[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)呼叫。  
  
 如需詳細資訊，請參閱 < [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md)中*ODBC 程式設計人員參考*。
