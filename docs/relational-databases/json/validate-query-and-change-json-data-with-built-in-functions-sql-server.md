---
title: "使用內建函式，驗證、查詢以及變更 JSON 資料 (SQL Server) | Microsoft 文件"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 9045ebe77cf2f60fecad22672f3f055d8c5fdff2
ms.openlocfilehash: d8c99e842ceaa2351c98583238cbba28e2a152c7
ms.contentlocale: zh-tw
ms.lasthandoff: 07/31/2017

---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>使用內建函數，驗證、查詢以及變更 JSON 資料 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

內建的 JSON 支援包含下列在此主題中簡述的內建功能。  
  
-   [ISJSON](#ISJSON) 可測試字串是否包含有效的 JSON。  
  
-   [JSON_VALUE](#VALUE) 可從 JSON 字串擷取純量值。  
  
-   [JSON_QUERY](#QUERY) 可從 JSON 字串擷取物件或陣列。  
  
-   [JSON_MODIFY](#MODIFY) 可更新 JSON 字串中的屬性值，並傳回更新後的 JSON 字串。  
 
## <a name="json-text-for-the-examples-on-this-page"></a>此頁面上之範例的 JSON 文字
此頁面上的範例使用下列 JSON 文字，其中包含複雜的項目。

```sql 
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }' 
``` 

##  <a name="ISJSON"></a> 使用 ISJSON 函數來驗證 JSON 文字  
 **ISJSON** 函數可測試字串是否包含有效的 JSON。  
  
下列範例會傳回資料行 `json_col` 中包含有效 JSON 的資料列。  
  
```sql  
SELECT id, json_col
FROM tab1
WHERE ISJSON(json_col) > 0 
```  

如需詳細資訊，請參閱 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)。  
  
##  <a name="VALUE"></a> 使用 JSON_VALUE 函數，從 JSON 文字中擷取值  
**JSON_VALUE** 函數可從 JSON 字串擷取純量值。  
  
下列範例會將巢狀 JSON 屬性 `town` 的值擷取為區域變數。  
  
```sql  
SET @town = JSON_VALUE(@jsonInfo, '$.info.address.town')  
```  
  
如需詳細資訊，請參閱 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)。  
  
##  <a name="QUERY"></a> 使用 JSON_QUERY 函數，從 JSON 文字擷取物件或陣列  
**JSON_QUERY** 函數可從 JSON 字串擷取物件或陣列。  
 
下列範例示範如何在查詢結果中傳回 JSON 片段。  
  
```sql  
SELECT FirstName, LastName, JSON_QUERY(jsonInfo,'$.info.address') AS Address
FROM Person.Person
ORDER BY LastName
```  
  
如需詳細資訊，請參閱 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)。  
  
##  <a name="JSONCompare"></a> JSON_VALUE 與 JSON_QUERY 的比較  
**JSON_VALUE** 和 **JSON_QUERY** 的主要差別是 **JSON_VALUE** 傳回純量值，而 **JSON_QUERY** 傳回物件或陣列。  
  
請參考下列 JSON 文字範例：  
  
```json  
{
    "a": "[1,2]",
    "b": [1, 2],
    "c": "hi"
}  
```  
  
在這個 JSON 文字範例中，資料成員 "a" 和 "c" 為字串值，而資料成員 "b" 是陣列。 **JSON_VALUE** 和 **JSON_QUERY** 傳回下列結果︰  
  
|路徑|**JSON_VALUE** 傳回|**JSON_QUERY** 傳回|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL 或錯誤|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL 或錯誤|  
|**$.b**|NULL 或錯誤|[1,2]|  
|**$.b[0]**|1|NULL 或錯誤|  
|**$.c**|hi|NULL 或錯誤|  
  
## <a name="test-jsonvalue-and-jsonquery-with-the-adventureworks-sample-database"></a>使用 AdventureWorks 範例資料庫，測試 JSON_VALUE 與 JSON_QUERY  
依據本主題中所述，使用 AdventureWorks 範例資料庫，執行下列範例 (其中包含 JSON 資料)，以測試內建函數。 若要取得 AdventureWorks 範例資料庫，請 [按一下此處](http://www.microsoft.com/en-us/download/details.aspx?id=49502)。  
  
在下列範例中，`SalesOrder_json`資料表中的 `Info` 資料行包含 JSON 文字。  
  
### <a name="example-1---return-both-standard-columns-and-json-data"></a>範例 1 - 傳回標準的資料行和 JSON 資料  
下列查詢會傳回來自標準關聯式資料行及 JSON 資料行的值。  
  
```sql  
SELECT SalesOrderNumber, OrderDate, Status, ShipDate, Status, AccountNumber, TotalDue,
 JSON_QUERY(Info,'$.ShippingInfo') ShippingInfo,
 JSON_QUERY(Info,'$.BillingInfo') BillingInfo,
 JSON_VALUE(Info,'$.SalesPerson.Name') SalesPerson,
 JSON_VALUE(Info,'$.ShippingInfo.City') City,
 JSON_VALUE(Info,'$.Customer.Name') Customer,
 JSON_QUERY(OrderItems,'$') OrderItems
FROM Sales.SalesOrder_json
WHERE ISJSON(Info) > 0
```  
  
### <a name="example-2--aggregate-and-filter-json-values"></a>範例 2 - 彙總並篩選 JSON 值  
下列查詢會依據客戶名稱和狀態來彙總小計 (客戶名稱是儲存在 JSON 中，而狀態是儲存在一般資料行中)。 然後依縣市 (儲存在 JSON 中) 及 OrderDate (儲存在一般資料行中) 篩選結果。  
  
```sql  
DECLARE @territoryid INT;
DECLARE @city NVARCHAR(32);

SET @territoryid=3;

SET @city=N'Seattle';

SELECT JSON_VALUE(Info, '$.Customer.Name') AS Customer, Status, SUM(SubTotal) AS Total
FROM Sales.SalesOrder_json
WHERE TerritoryID=@territoryid
 AND JSON_VALUE(Info, '$.ShippingInfo.City') = @city
 AND OrderDate > '1/1/2015'
GROUP BY JSON_VALUE(Info, '$.Customer.Name'), Status
HAVING SUM(SubTotal)>1000
```  
  
##  <a name="MODIFY"></a> 使用 JSON_MODIFY 函數來更新 JSON 文字中的屬性值  
**JSON_MODIFY** 函式會更新 JSON 字串中屬性的值，並傳回更新的 JSON 字串。  
  
下列範例會更新包含 JSON 的變數中，JSON 屬性的值。  
  
```sql  
SET @info = JSON_MODIFY(@jsonInfo, "$.info.address[0].town", 'London')    
```  
  
 如需詳細資訊，請參閱 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)。  
  
## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>深入了解 SQL Server 中的內建 JSON 支援  
對於大量的特定解決方案、使用案例和建議，請參閱 SQL Server 和 Azure SQL Database 中 Microsoft 經理專案 Jovan Popovic 所撰寫的[有關內建 JSON 支援的部落格文章](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)。
  
## <a name="see-also"></a>另請參閱  
 [ISJSON &#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)   
 [JSON 路徑運算式 &#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  
