---
title: SQLInstallTranslator 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslator
helpviewer_keywords:
- SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de493cc42980390fee94ca4d86efc8f5cd40646c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776626"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator 函式
**合規性**  
 版本導入： ODBC 2.5 中，已被取代  
  
 **摘要**  
 在 ODBC 3.0 **SQLInstallTranslator**已被取代[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)。 若要呼叫**SQLInstallTranslator**將會對應至**SQLInstallTranslatorEx**。 如需詳細資訊，請參閱 < **SQLInstallTranslatorEx**。  
  
 **SQLInstallTranslator**會傳回 FALSE，如果應用程式所呼叫的是它在 ODBC 3 *.x*使用的驅動程式管理員*lpszInfFile*引數設定為 NULL 以外的值。 使用 ODBC 2 的 Odbc.inf 檔案。*x*不再支援在 ODBC 3 *.x*、 甚至是為了與舊版相容。
