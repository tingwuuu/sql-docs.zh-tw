---
title: updateBigDecimal 方法 (java.lang.String, java.math.BigDecimal) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBigDecimal (java.lang.String, java.math.BigDecimal)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b844cd9d-3d2d-4385-ab01-ecc89692054f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60004db3c30030affb92f57af983880d5c8c169f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645376"
---
# <a name="updatebigdecimal-method-javalangstring-javamathbigdecimal"></a>updateBigDecimal 方法 (java.lang.String, java.math.BigDecimal)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  透過指定的資料行名稱，使用 BigDecimal 物件來更新指定的資料行。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void updateBigDecimal(java.lang.String columnName,  
                             java.math.BigDecimal x)  
```  
  
#### <a name="parameters"></a>參數  
 *columnName*  
  
 包含資料行名稱的**字串**。  
  
 *x*  
  
 BigDecimal 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 updateBigDecimal 方法是由 java.sql.ResultSet 介面中的 updateBigDecimal 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [updateBigDecimal 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
