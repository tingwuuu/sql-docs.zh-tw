---
title: ADO 詞彙 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ADO, glossary
ms.assetid: b0478836-4123-4357-969a-c5784fc28be5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b93ee4ab5b57414d8c8d640bc12a5ebbff882c6
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52530396"
---
# <a name="ado-glossary"></a>ADO 詞彙
本主題會定義與 ADO 的詞彙。  
  
## <a name="a"></a>A  
 絕對 URL  
 完整的 URL，在網際網路或近端內部網路上指定之資源的所在位置。 另請參閱*URL*並*相對 URL*。  
  
 ActiveX 控制項  
 自我登錄，同處理序通常會有視覺項目在設計階段或執行的階段的 COM 元件。 ActiveX 控制項也能使用中文件的容器，例如 Microsoft Internet Explorer 與通訊的能力。  
  
 ADISAPI （進階資料網際網路伺服器應用程式開發介面）  
 提供剖析的 ISAPI DLL、 自動化控制、 封送處理資料錄集，和 MIME 封裝。 ADISAPI 元件是透過提供由網際網路資訊服務 (IIS) 中的 API 來運作。 另請參閱*ISAPI*。  
  
 彙總函式 (aggregate function)  
 在查詢中，例如 COUNT、 AVG 或計算值，使用資料表的資料行中的所有資料列的 STDEV 函式。 在撰寫運算式和程式設計中，您可以使用 SQL 彙總函式 （包含以上所列的三個） 和網域彙總函式來判斷各種統計資料。  
  
 alias  
 您授與資料行或運算式中的 SQL SELECT 陳述式，通常較短或更有意義的替代名稱。 比方說，BobSales 會有下列的 SELECT 陳述式中的別名：「 選取了 wr 銷售做為從 SalesDB BobSales"。 別名可用來以動態方式將 DataControl 物件上的控制項繫結中的資料行。  
  
 Apartment 執行緒  
 COM 執行緒的模型物件的所有呼叫都發生在一個執行緒。 在 apartment 執行緒，COM 會同步處理，並將呼叫封送處理。 另請參閱*COMmddefcom*。  
  
 非同步作業  
 控制權傳回給呼叫的程式，而不需等待作業完成的作業。 表示作業已完成之前，會繼續執行程式碼。 另請參閱*同步作業*。  
  
## <a name="b"></a>B  
 繫結項目  
 資料表中的欄位和變數之間的對應。 在 ADO Visual c + + 延伸模組**資料錄集**欄位會對應至 C/c + + 變數。  
  
 位元遮罩  
 數字的值適用於搭配其他數值的位元值比較通常加上旗標參數或傳回值中的選項。 通常這項比較是使用位元的邏輯運算子，例如**和**並**或者**在 Visual Basic 中**&** 並 **&#124;** c + + 中。  
  
 例如，ADO **FieldAttributeEnum**值可用來當做位元遮罩來決定欄位的屬性。 假設您想要判斷欄位是否可更新。 您可以測試這個，與 Visual Basic 中的下列運算式：`Field.Attributes AND adFldUpdatable`  
  
 如果結果為 TRUE，欄位是可更新的。  
  
 書籤 (bookmark)  
 可唯一識別資料列集內的資料列，以便使用者可以快速瀏覽至該標記。  
  
 商務物件  
 執行一組定義的作業，例如資料驗證 」 或 「 商務規則邏輯的物件。 通常位於中介層商務物件。  
  
 商務規則  
 驗證的編輯、 登入驗證、 資料庫查閱、 原則和構成企業的方式進行商務往來的演算轉換組合。 也稱為*商務邏輯*。  
  
## <a name="c"></a>c  
 導出的運算式  
 運算式不是常數，但其值取決於其他值。 要評估，必須取得的導出的運算式，並將其計算從其他來源，通常是在其他欄位或資料列的值中。  
  
 章節  
 從資料來源的資料列範圍參考。 在 ADO 中，一整章通常是另一個的參考**資料錄集**。  
  
 章節資料行會使您能夠定義*父系-子系*關聯性其中*父系*會**資料錄集**包含章節資料行和*子系*已**資料錄集**一章所表示。  
  
 章別名  
 參考附加至父代的資料行的別名。  
  
 字元集 (character set)  
 一組為其數值字元的對應。 比方說，Unicode 是 16 位元的字元設定支援的所有已知的字元編碼，並做為全球的字元編碼標準。  
  
 child  
 階層式關聯性的相依端。 子系是在其上方的另一個節點的階層式結構中的節點 （較接近根目錄）。 另請參閱*子系別名*，*父子式關聯性*，*父*。  
  
 子別名  
 別名所參考之子系。 另請參閱*別名*，*子*。  
  
 CLSID （類別識別項）  
 通用唯一識別碼 (UUID) 識別的 COM 元件。 每個 COM 元件的 CLSID Windows 登錄中，以便由其他應用程式可以載入它。 另請參閱*ProgID*， *COM*。  
  
 用戶端層  
 通常從使用者中呈現資料和輸入的程序是分散式系統的邏輯層有時稱為*前端*。 通常，用戶端層從根據輸入，伺服器要求資料，然後格式化並顯示結果。 另請參閱*中層*，*資料來源層*，*分散式應用程式*。  
  
 COM （元件物件模型）  
 一種二進位的標準，可讓在網路環境，不論他們所開發的語言為何，或其所在的電腦交互操作的物件。 以 COM 為基礎的技術包括 ActiveX 控制項、 自動化和連結與嵌入 (OLE) 物件。 COM 可讓物件公開給其他元件和主控件應用程式，其功能。 它會定義物件如何公開本身和跨處理序和跨網路，此公開資訊的運作方式。 COM 也會定義物件的生命週期。  
  
 COM 元件  
 二進位檔-例如.dll、.ocx，以及一些.exe 檔案-支援 COM 標準提供的物件。 這類檔案包含一或多個 class factory，COM 類別、 登錄項目機制，載入程式碼，以及等等的程式碼。  
  
 比較運算子  
 此運算子比較兩個運算式，並傳回布林值。  
  
 準則 」 參數可能會表示為">"（大於）、"\<"（小於）、"="（等於）、"> ="（大於或等於）"< ="（小於或等於）、"<>"（不等於） 或"like"（模式比對）。  
  
 component  
 物件，封裝資料和程式碼，並提供一組正確指定公開可用的服務。  
  
 複合檔案  
 COM 實作結構化檔案的儲存體。 複合檔案會將不同的物件儲存在兩個主要的項目所組成的單一、 結構化檔案： 儲存物件和資料流物件。 在一起，這些函式類似檔案內的檔案系統。  
  
 繫結在一起，一個實體檔案中的個別檔案的數目。 可以存取每個個別的檔案，在複合檔案中，如同它是單一的實體檔案。  
  
 常數  
 數值或字串值，不會變更。 具名的 ADO 列舉 （列舉常數） 可用於您的程式碼，而不是實際的值，例如**adUseClient**是的常數，其值為 3。 (Const adUseClient = 3)。 另請參閱*列舉型別*。  
  
 cursor  
 資料庫項目，以控制記錄巡覽、 可更新性的資料和可見性的其他使用者對資料庫所做的變更。  
  
## <a name="d"></a>D  
 資料繫結  
 建立關聯的物件或控制項的資料來源的應用程式的程序。 與資料來源相關聯的控制項稱為*資料繫結控制項*。  
  
 資料繫結控制項的內容會與資料庫中的值相關聯。 比方說，繫結至方格控制項**Recordset**物件可以是更新時中的資料列**資料錄集**會更新。 當新的值藉由擷取**資料錄集**，新的值會顯示在方格中。  
  
 資料提供者 (data provider)  
 公開 （expose） 至 ADO 應用程式資料的軟體不論是直接或透過服務提供者。 另請參閱服務提供者。  
  
 資料成形  
 技術，其使用正式的語法 (稱為**圖形語言**) 來定義特殊**資料錄集**物件 (稱為*塑造資料錄集*) 不包含只是資料，但也參考其他**Recordset**物件和/或計算的值根據項目另**資料錄集**物件。  
  
 資料來源層  
 代表執行 DBMS，例如 SQL Server 資料庫的電腦是分散式系統的邏輯層。 另請參閱*用戶端層*，*中層*，*分散式應用程式*。  
  
 DCOM  
 網路通訊協定，讓 COM 元件，能夠透過網路彼此直接通訊。 另請參閱*COM*，*元件*。  
  
 DDL （資料定義語言）  
 這些陳述式在 SQL 中定義，而不是操作資料。 資料庫結構描述是透過建立或修改 DDL。 例如， **CREATE TABLE**， **CREATE INDEX**，**授與**，以及**撤銷**SQL DDL 陳述式。  
  
 預設資料流  
 文字或二進位資料流 (由**Stream**物件) 相關聯**記錄**或是**資料錄集**物件時使用特定 OLE DB 提供者，例如適用於網際網路發佈的 Microsoft OLE DB 提供者。 預設資料流通常會包含根的網站等的 HTML 程式碼檔案的內容。  
  
 分散式應用程式  
 撰寫，以便處理可以分配給多部電腦在網路上的程式。 一般而言，分散式應用程式分成簡報、 商務邏輯和資料存放區層級，或*層*。 用戶端層、 中介層、 資料來源層，請參閱。  
  
 已中斷連線的資料錄集  
 A**資料錄集**不再有即時連接到伺服器的用戶端快取中的物件。 如果原始資料來源需要存取一次的某些原因，例如更新的資料，則必須重新建立連線。 不過，集合、 屬性和方法的已中斷連接**資料錄集**仍可存取。  
  
 DML （資料操作語言）  
 這些陳述式在 SQL 中操作，而不是資料定義。 選取並修改 DML 與資料庫中的值。 例如，**插入**，**更新**，**刪除**，以及**選取**SQL DML 陳述式。  
  
 文件來源提供者  
 管理資料夾和文件的提供者的特殊類別。 文件由何時**記錄**物件或文件的資料夾由**資料錄集**物件時，文件的來源提供者會填入這些物件具有一組唯一的欄位，描述的文件，而不是實際的文件本身的特性。 另請參閱資源記錄。  
  
 DSN （資料來源名稱）  
 用來連接到特定的 ODBC 資料庫應用程式資訊的集合。 ODBC 驅動程式管理員會使用這項資訊來建立資料庫的連接。 在檔案 （檔案 DSN） 或 Windows 登錄 （資料來源名稱的電腦） 中，可以儲存 DSN。  
  
 動態屬性  
 此資料提供者或資料指標服務特有的屬性。 **屬性**自動填入這些物件的集合 （「 動態 」）。 連接到資料來源透過特定的資料提供者之前，物件會有任何動態屬性。 另請參閱資料提供者]、 [資料指標。  
  
## <a name="e"></a>E  
 列舉型別  
 具名常數的清單。 列舉的值不需要是唯一的。 不過每個值的名稱必須是已定義列舉的範圍內唯一的。 在 ADO 中，列舉型別用於數字參數和傳回值，以新增 ADO 程式碼的意義，並可為開發人員之數字的值 （這可能會變更版本）。 例如，若要開啟的靜態**Recordset**，使用**adOpenStatic**列舉值： `Recordset.Open ,,adOpenStatic`  
  
 也稱為*列舉的常數*。 另請參閱*常數*。  
  
 event  
 物件，您可以撰寫程式碼來回應所識別的動作。 藉由執行命令、 交易完成、 資料錄集巡覽和資料的更新，以及其他動作，就可以產生事件。 另請參閱*事件處理常式*。  
  
 事件處理常式 (event handler)  
 事件處理常式是在事件發生時執行的程式碼。 另請參閱事件。  
  
## <a name="h"></a>H  
 handler (處理常式)  
 所管理的常見且相當簡單的條件或作業，例如錯誤復原或資料管理的常式。  
  
 階層式資料錄集  
 A **Recordset**包含另一個**資料錄集**。 另請參閱資料成形，一章。  
  
 如需詳細資訊，請參閱 <<c0> [ 存取階層式資料錄集中的資料列](../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)。  
  
 階層 (hierarchy)  
 一般情況下，階層是包含 top 的排名的結構層級和從屬層級。 在 ADO 中，階層式**資料錄集**用來代表資料錄和一整章間的父子式關聯性。 在 ADO 中，而且**記錄**並**Stream**物件可以用來存取階層式樹狀結構，例如資料夾和文件。 也包含 ADO MD**階層**物件，以表示 OLAP cube 中維度的層級之間的關聯性。 另請參閱階層式資料錄集父子式關聯性、 章、 樹狀目錄中。  
  
## <a name="i-l"></a>I-L  
 ISAPI （網際網路伺服器應用程式開發介面）  
 一組針對網際網路的伺服器，例如執行 Microsoft® Internet Information Services (IIS) Windows NT® Server/Windows 2000 Server 的函式。  
  
 Key  
 資料行或資料表中唯一識別資料列; 的資料行通常用來編製索引的資料表。  
  
## <a name="m"></a>M  
 封送處理  
 跨執行緒或處理序界限的封裝、 傳送和 unpackaging 介面方法參數的程序。  
  
 中介層  
 在分散式系統中的使用者介面或 Web 用戶端與資料庫之間的邏輯層。 這通常是商務物件執行個體化的位置。 中介層是商務規則和產生並操作經過接收資訊的函式的集合。 他們這麼做，透過商務規則，它可以經常變更，並因此會封裝成實際分開的應用程式邏輯本身的元件。 也稱為*應用程式伺服器層*。 分散式應用程式、 用戶端層、 資料來源層，請參閱。  
  
 MIME （多用途網際網路郵件延伸標準）  
 網際網路通訊協定最初開發跨異質網路、 電腦和電子郵件環境允許以豐富的內容的電子郵件訊息的交換。 在實務上，MIME 也已採用並擴充非電子郵件應用程式。  
  
 MIME 是一種標準，允許發行，並在網際網路上閱讀的二進位資料。 使用二進位資料檔案的標頭包含資料的 MIME 類型這會通知用戶端程式 (Web 瀏覽器和郵件封裝執行個體)，它們必須以不同方式處理資料，比它們處理文字。 例如，包含 JPEG 圖片的 Web 文件的標頭包含 JPEG 檔案格式的具體 MIME 類型。 如果有的話，這可讓以顯示其 JPEG 檢視器中，使用檔案瀏覽器。  
  
## <a name="n-o"></a>N-O  
 node  
 階層樹狀結構中的元素。 節點可能是根目錄或另一個節點的子系。 節點也可以是多個子系的父系。 另請參閱階層、 樹狀結構、 根、 子系、 父系。  
  
 物件變數  
 包含對物件之參考的變數。 比方說，`objCustomObject`是指向 CustomObject 型別的物件變數：`Set objCustomObject = CreateObject(adodb.Recordset)`  
  
 ODBC (開放式資料庫連接)  
 用來連接到各種資料來源的標準程式設計語言介面。 這通常是透過 [控制台]，其中指派資料來源名稱 (Dsn)，若要使用特定的 ODBC 驅動程式存取。  
  
 OLE DB  
 一組將資料從各種來源使用 COM 公開的介面 OLE DB 介面會提供統一存取各種資訊來源所儲存資料的應用程式。 這些介面支援 DBMS 功能適用於資料來源，讓它共用其資料的量。 另請參閱 com。  
  
 開放式鎖定  
 一種鎖定類型其中包含一或多個記錄，包括正在編輯的記錄的資料頁都無法提供給其他使用者正由更新記錄時，才**更新**方法，但已使用之前和之後若要呼叫**更新**。  
  
 使用開放式鎖定時**Recordset**物件會以開啟**LockType**參數或屬性設定為**adLockOptimistic**或**Adlockpessimistic**。 請參閱也封閉式鎖定。  
  
 序數值  
 訂單中項目的數值的位置。 ADO 集合中的第一個項目序數的值會是零 (0)。 下一個項目是一 （1），依此類推。  
  
## <a name="p"></a>P  
 參數化的命令  
 查詢或命令，可讓您執行命令之前，設定參數值中。 例如，SQL 字串可以參數化 SQL 字串中內嵌參數標記 (指定的 '？ ' 字元)。 應用程式然後指定每個參數的值，並執行命令。  
  
 父系 (parent)  
 階層式關聯性控制側邊。 在階層式結構中，父代有階層中的正下方的一個或多個子節點。 另請參閱父別名，父子式關聯性，子系。  
  
 父別名  
 父代是指的別名。 請參閱也別名、 父代。  
  
 父子式關聯性  
 在父代的更新版本，而且直接相關聯一個或多個子系的一個層級的階層式結構的關聯性。 子系是一個較低的層級，而且必須具有一個父代。 另請參閱父系、 子系。  
  
 封閉式鎖定  
 一種鎖定類型其中包含一或多個記錄，包括正在編輯的記錄的頁面都無法提供給其他使用者，以確保會對進行更新。 封閉式鎖定行為是由 OLE DB 提供者定義。 一般而言，記錄被鎖定時編輯，並維持無法使用，直到**更新**方法完成。  
  
 封閉式鎖定已啟用時**Recordset**物件會以開啟**LockType**參數或屬性設定為**Locktype**。 請參閱也開放式鎖定。  
  
 集區  
 效能最佳化，根據使用的預先配置的資源，例如物件或資料庫連接的集合。 它會更有效率的方式繪製現有的資源，而不是建立新的資源集區中。  
  
 ProgID （程式設計識別項）  
 對應至 Windows 登錄的 COM 應用程式的唯一名稱。 ADO 連接的 ProgID 是 「 ADODB。連線 」。 另請參閱 CLSID、 com。  
  
 Proxy  
 提供參數封送處理的特定介面的物件，並呼叫在不同的執行緒，或在另一個處理序在不同的執行環境中，執行這類的應用程式物件的用戶端所需的通訊。 Proxy 會位於與用戶端，而且與對應的虛設常式位於與應用程式物件所呼叫之通訊。 請參閱 「 虛設常式 」。  
  
## <a name="r"></a>R  
 相對的 URL  
 不完整的 URL，在網際網路或近端內部網路，其位置會相對於指定的絕對 URL 」 或 「 對等的 ADO 連接物件的起始點上指定的資源。 在 作用中，串連絕對和相對 Url consitute 是完整的 URL。 URL 和絕對 URL，請參閱。  
  
 遠端資料來源  
 資料來源的另一部電腦上，而不是本機系統上存在 （用戶端應用程式所執行所在）。  
  
 資源記錄  
 文件來源提供者的欄位的定義和描述的資料夾或文件包含一筆記錄。 文件本身不會包含在資源記錄，但通常可以存取的預設資料流或包含 URL 的資源記錄中的欄位。 另請參閱文件來源提供者，預設資料流、 URL。  
  
 資料列集  
 一組從資料來源，全都具有相同的欄位結構描述的資料列。 資料列集可以代表資料表中的所有或部分欄位。 資料列集也可以代表的虛擬資料表，查詢或聯結的兩個或多個資料表所建立。 在 ADO 中，資料列集由**資料錄集**物件。  
  
## <a name="s"></a>S  
 範圍。  
 參考的物件或變數或檢視表或資料表中的記錄範圍的範圍。 比方說，本機變數可以參考只有在所定義的程序內。 公用變數是可從應用程式的任何位置存取。 如果在定義的搜尋路徑物件，例如目前的資料庫，就會在範圍內。 記錄範圍可以指定含有範圍子句中的許多命令。  
  
 服務提供者  
 封裝服務所產生和取用資料，擴充功能，ADO 應用程式中的軟體。 它不會直接公開的資料提供者，而不是它提供一項服務，例如查詢處理。 服務提供者可能會處理資料提供者所提供的資料。 另請參閱資料提供者。  
  
 圖形化的資料錄集  
 A **Recordset**其資料行已特別定義為包含不只是資料，但也參考 （稱為章節），其他**資料錄集**物件和/或計算的值根據其他**資料錄集**物件。  
  
 同層級  
 任何兩個或多個節點階層式結構中，位於相同的層級，階層中。 在階層中的根節點有任何同層級項目。  
  
 預存程序  
 先行編譯程式碼，例如 SQL 陳述式和選擇性的流程控制陳述式集合的名稱下儲存，並當做一個單位處理。 預存程序會儲存在資料庫中;他們可以使用一次呼叫，從應用程式執行，並允許使用者宣告的變數、 條件式執行及其他功能強大的程式設計功能。  
  
 虛設常式  
 提供參數封送處理的特定介面的物件，並接收來自不同的執行緒上，或在另一個處理序在不同的執行環境中，執行這類的用戶端呼叫的應用程式物件所需的通訊。 虛設常式會位於與應用程式物件，而且會與對應的 proxy 位於與它所呼叫的用戶端通訊。 請參閱 「 proxy 」。  
  
 子節點  
 請參閱子系。  
  
 同步作業  
 作業完成之前可能會開始下一項作業的程式碼所起始。 另請參閱非同步作業。  
  
## <a name="t-z"></a>T-Z  
 樹狀結構  
 結構，表示項目 （節點） 之間的階層式關聯性。 有一個節點位於最上層 （根） 的樹狀結構。 為根目錄，底下可以有多個子系。 每個子系又可能是其他子系，因此類似樹狀結構分支的父代。 包含文件和其他資料夾的資料夾是樹狀結構的典型範例。 另請參閱階層、 節點、 根、 子系、 父系。  
  
 網頁伺服器  
 提供 Web 服務和頁面，以內部網路和網際網路使用者的電腦。
