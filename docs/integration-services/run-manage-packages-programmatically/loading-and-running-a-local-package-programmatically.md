---
title: "載入和以程式設計方式執行本機封裝 |Microsoft 文件"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Integration Services packages, running
- events [Integration Services], capturing
- packages [Integration Services], running
- loading packages programmatically
- Visual Basic [Integration Services]
- running packages [Integration Services]
- programmatically load and run packages [SSIS]
ms.assetid: 2f9fc1a8-a001-4c54-8c64-63b443725422
caps.latest.revision: 60
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 07ceb460488ca1973295b6b8e991948efe8b9d2a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/03/2017

---
# <a name="loading-and-running-a-local-package-programmatically"></a>以程式設計的方式載入和執行本機封裝
  您可以執行[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]封裝視需要或是在使用中所述的方法預定時間[Running Packages](https://msdn.microsoft.com/library/ms141708(v=sql.110).aspx)。 然而，只需要幾行的程式碼，您就可以從 Windows Form 應用程式、主控台應用程式、ASP.NET Web 表單或 Web 服務，或是 Windows 服務等自訂應用程式執行封裝。  
  
 此主題會討論：  
  
-   以程式設計方式載入封裝  
  
-   以程式設計方式執行封裝  
  
 本主題中用以載入和執行封裝的方法的所有需要的參考**Microsoft.SqlServer.ManagedDTS**組件。 新的專案中加入參考之後, 匯入<xref:Microsoft.SqlServer.Dts.Runtime>命名空間與**使用**或**匯入**陳述式。  
  
## <a name="loading-a-package-programmatically"></a>以程式設計方式載入封裝  
 無論封裝儲存在本機或遠端，如果要在本機電腦上以程式設計方式載入封裝，請呼叫下列其中一種方法：  
  
|儲存位置|要呼叫的方法|  
|----------------------|--------------------|  
|檔案|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>|  
|SSIS 封裝存放區|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>|  
  
> [!IMPORTANT]  
>  搭配 SSIS 封裝存放區使用之 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 類別的方法，僅支援 "."、localhost 或本機伺服器的伺服器名稱。 您無法使用 "(local)"。  
  
## <a name="running-a-package-programmatically"></a>以程式設計方式執行封裝  
 在本機電腦上執行封裝的 Managed 程式碼中開發自訂應用程式需要下列方法。 接下來的範例主控台應用程式中將示範此處摘要的步驟。  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically"></a>以程式設計的方式在本機電腦上執行封裝  
  
1.  啟動 Visual Studio 開發環境，並以慣用的開發語言建立新應用程式。 此範例使用主控台應用程式，不過，您也可以從 Windows Form 應用程式、ASP.NET Web 表單或 Web 服務或是 Windows 服務執行封裝。  
  
2.  在**專案**功能表上，按一下 **加入參考**並加入參考**microsoft.sqlserver.manageddts.dll 中**。 按一下 **[確定]**。  
  
3.  使用 Visual Basic**匯入**陳述式或 C#**使用**陳述式匯入**Microsoft.SqlServer.Dts.Runtime**命名空間。  
  
4.  在主常式中加入下列程式碼。 完成的主控台應用程式應類似下列範例。  
  
    > [!NOTE]  
    >  範例程式碼會透過使用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> 方法示範從檔案系統載入封裝。 不過，您也可以呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> 方法從 MSDB 資料庫載入封裝，或是呼叫 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> 方法從 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝存放區載入封裝。  
  
5.  執行專案。 範例程式碼會執行隨 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 範例安裝的 CalculatedColumns 範例封裝。 封裝執行的結果會顯示在主控台視窗中。  
  
### <a name="sample-code"></a>範例程式碼  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, Nothing)  
    pkgResults = pkg.Execute()  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, null);  
      pkgResults = pkg.Execute();  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="capturing-events-from-a-running-package"></a>從執行封裝擷取事件  
 當您以程式設計方式執行封裝 (如前面的範例所示)，可能也會想要擷取當封裝執行時所發生的錯誤及其他事件。 您可以藉由加入從 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 類別繼承的類別，以及藉由在載入封裝時將參考傳遞給該類別，來完成這項作業。 雖然下列範例只會擷取 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> 事件，不過 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 類別可讓您擷取更多其他事件。  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically-and-capture-package-events"></a>以程式設計的方式在本機電腦上執行封裝並擷取封裝事件  
  
1.  遵循上述範例中的步驟，為此範例建立專案。  
  
2.  在主常式中加入下列程式碼。 完成的主控台應用程式應類似下列範例。  
  
3.  執行專案。 範例程式碼會執行隨 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 範例安裝的 CalculatedColumns 範例封裝。 封裝執行的結果以及任何發生的錯誤都會顯示在主控台視窗中。  
  
### <a name="sample-code"></a>範例程式碼  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    Dim eventListener As New EventListener()  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, eventListener)  
    pkgResults = pkg.Execute(Nothing, Nothing, eventListener, Nothing, Nothing)  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
  
Class EventListener  
  Inherits DefaultEvents  
  
  Public Overrides Function OnError(ByVal source As Microsoft.SqlServer.Dts.Runtime.DtsObject, _  
    ByVal errorCode As Integer, ByVal subComponent As String, ByVal description As String, _  
    ByVal helpFile As String, ByVal helpContext As Integer, _  
    ByVal idofInterfaceWithError As String) As Boolean  
  
    ' Add application–specific diagnostics here.  
    Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description)  
    Return False  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppWithEventsCS  
{  
  class MyEventListener : DefaultEvents  
  {  
    public override bool OnError(DtsObject source, int errorCode, string subComponent,   
      string description, string helpFile, int helpContext, string idofInterfaceWithError)  
    {  
      // Add application-specific diagnostics here.  
      Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description);  
      return false;  
    }  
  }  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      MyEventListener eventListener = new MyEventListener();  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, eventListener);  
      pkgResults = pkg.Execute(null, null, eventListener, null, null);  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [了解本機與遠端執行之間的差異](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [載入和以程式設計方式執行遠端封裝](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [載入本機封裝的輸出](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  