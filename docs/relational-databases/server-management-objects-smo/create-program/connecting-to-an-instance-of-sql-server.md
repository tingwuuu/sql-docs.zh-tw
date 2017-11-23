---
title: "連接到 SQL server 執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, connections
- connections [SMO]
- instances of SQL Server, connections
- SMO [SQL Server], connections
ms.assetid: ad3cf354-b2e3-468b-b986-1232e375fd84
caps.latest.revision: "50"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: edbad8837867dbb863672db7d3803a0d9e1e4ac5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="connecting-to-an-instance-of-sql-server"></a>連接到 SQL Server 的執行個體
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]中的第一個程式設計步驟[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理物件 (SMO) 的應用程式會建立的執行個體<xref:Microsoft.SqlServer.Management.Smo.Server>物件，並建立其連線到的執行個體[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。  
  
 您可以用三種方式建立 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件的執行個體，並建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接。 第一種方式是，使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數來提供連接資訊。 第二種方式是，明確地設定 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件屬性來提供連接資訊。 第三種方式是，在 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件建構函式中傳遞 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。 
  
 **使用 ServerConnection 物件**  
  
 使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數的優點是，連接資訊可以重複使用。 宣告 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件變數。 接著，宣告 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件，並利用連接資訊 (例如，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱與驗證模式) 設定屬性。 然後，傳遞<xref:Microsoft.SqlServer.Management.Common.ServerConnection>物件變數當做參數<xref:Microsoft.SqlServer.Management.Smo.Server>物件建構函式。 不建議同時在不同的伺服器物件之間共用連接。 使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.Copy%2A> 方法來取得現有連接設定的複本。  
  
 **明確地設定伺服器物件屬性**  
  
 或者，您可以宣告 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件變數，並呼叫預設的建構函式。 同時，<xref:Microsoft.SqlServer.Management.Smo.Server> 物件會嘗試利用所有預設的連接設定，連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的預設執行個體。  
  
 **提供 SQL Server 執行個體名稱中伺服器物件的建構函式**  
  
 宣告 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件變數，然後傳遞 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體名稱，做為建構函式中的字串參數。 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件會利用包含預設連接設定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體建立連接。  
  
## <a name="connection-pooling"></a>連接共用  
 通常不需要呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 物件的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 方法。 SMO 將會在需要時，自動建立連接，並在執行作業完畢之後，將連接釋放到連接集區。 呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法時，並不會將連接釋放到集區。 若要將連接釋放到集區，必須明確地呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> 方法。 此外，您可以設定 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.NonPooledConnection%2A> 物件的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 屬性來要求非集區的連接。  
  
## <a name="multithreaded-applications"></a>多執行緒應用程式  
 對於多執行緒應用程式，應該在每個執行緒中使用個別的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。  
  
## <a name="connecting-to-an-instance-of-sql-server-for-rmo"></a>連接到 SQL Server for RMO 的執行個體  
 Replication Management Objects (RMO) 會使用與 SMO 稍微不同的方法來連接到複寫伺服器。  
  
 RMO 程式設計物件需要的執行個體的連接[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]由使用<xref:Microsoft.SqlServer.Management.Common.ServerConnection>物件所實作**Microsoft.SqlServer.Management.Common**命名空間。 這個伺服器連接會獨立於 RMO 程式設計物件之外建立。 接著會在執行個體建立期間，或是將它指派到物件的 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性，藉以將它傳遞到 RMO 物件。 以此方式，就可以個別建立和管理 RMO 程式設計物件與連接物件執行個體，而且多個 RMO 程式設計物件可以重複使用單一連接物件。 下列規則適用於應用程式伺服器的連接：  
  
-   連接的所有屬性是針對指定的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件所定義。  
  
-   每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接都必須有它自己的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。  
  
-   在 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件中，會提供所有建立連接及成功登入伺服器的驗證資訊。  
  
-   根據預設，連接都是使用「Microsoft Windows 驗證」所建立。 若要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證，必須將 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> 設定為 False 與 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A>，而且 <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> 必須設定為有效的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入與密碼。 安全性認證必須以安全方式儲存和處理，而且每當有需要時必須在執行階段提供。  
  
-   您必須明確地呼叫 <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> 方法，才能將連接傳遞到任何 RMO 程式設計物件。  
  
## <a name="examples"></a>範例  
如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。 如需詳細資訊，請參閱[建立 Visual C# 35。在 Visual Studio.NET 中的 SMO 專案](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。  
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a>在 Visual Basic 中使用 Windows 驗證連接到 SQL Server 的本機執行個體  
 連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本機執行個體不需要太多程式碼。 而是依賴驗證方法和伺服器的預設值。 需要擷取資料的第一個作業將會導致連接建立。  
 
這個範例是使用 Windows 驗證連接到 SQL Server 的本機執行個體的 Visual Basic.NET 程式碼。 

```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'The connection is established when a property is requested.
Console.WriteLine(srv.Information.Version)
'The connection is automatically disconnected when the Server variable goes out of scope.
```
  
## <a name="connecting-to-the-local-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a>在 Visual C# 中使用 Windows 驗證連接到 SQL Server 的本機執行個體  
 連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本機執行個體不需要太多程式碼。 而是依賴驗證方法和伺服器的預設值。 需要擷取資料的第一個作業將會導致連接建立。  
  
 此範例為 Visual C# .NET 程式碼，會用 Windows 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的本機執行個體。  
  
```csharp  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//The connection is established when a property is requested.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-basic"></a>在 Visual Basic 中使用 Windows 驗證連接到 SQL Server 的遠端執行個體  
 當您使用 Windows 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，您不需要指定驗證類型。 Windows 驗證是預設值。  
  
 這個範例是[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]會連接到遠端執行個體的.NET 程式碼[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]使用 Windows 驗證。 字串變數*strServer*包含遠端執行個體的名稱。  
  
```VBNET   
'Connect to a remote instance of SQL Server.
Dim srv As Server
'The strServer string variable contains the name of a remote instance of SQL Server.
srv = New Server(strServer)
'The actual connection is made when a property is retrieved. 
Console.WriteLine(srv.Information.Version)
'The connection is automatically disconnected when the Server variable goes out of scope.
```
  
## <a name="connecting-to-a-remote-instance-of-sql-server-by-using-windows-authentication-in-visual-c"></a>在 Visual C# 中使用 Windows 驗證連接到 SQL Server 的遠端執行個體  
 當您使用 Windows 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，您不需要指定驗證類型。 Windows 驗證是預設值。  
  
 此範例為 Visual C# .NET 程式碼，會使用 Windows 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的遠端執行個體。 字串變數*strServer*包含遠端執行個體的名稱。  
  
```csharp  
{   
//Connect to a remote instance of SQL Server.   
Server srv;   
//The strServer string variable contains the name of a remote instance of SQL Server.   
srv = new Server(strServer);   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
}   
//The connection is automatically disconnected when the Server variable goes out of scope.  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-basic"></a>在 Visual Basic 中使用 SQL Server 驗證連接到 SQL Server 的執行個體  
 當您使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，您必須指定驗證類型。 此範例示範宣告 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數的替代方法，讓連接資訊得以重複使用。  
  
 此範例是[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].NET 程式碼示範如何連接到遠端和*vPassword*包含登入和密碼。  
  
```VBNET  
' compile with:   
' /r:Microsoft.SqlServer.Smo.dll  
' /r:Microsoft.SqlServer.ConnectionInfo.dll  
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      Dim sqlServerLogin As [String] = "user_id"  
      Dim password As [String] = "pwd"  
      Dim instanceName As [String] = "instance_name"  
      Dim remoteSvrName As [String] = "remote_server_name"  
  
      ' Connecting to an instance of SQL Server using SQL Server Authentication  
      Dim srv1 As New Server()   ' connects to default instance  
      srv1.ConnectionContext.LoginSecure = False   ' set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin  
      srv1.ConnectionContext.Password = password  
      Console.WriteLine(srv1.Information.Version)   ' connection is established  
  
      ' Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      Dim srvConn As New ServerConnection()  
      srvConn.ServerInstance = ".\" & instanceName   ' connects to named instance  
      srvConn.LoginSecure = False   ' set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin  
      srvConn.Password = password  
      Dim srv2 As New Server(srvConn)  
      Console.WriteLine(srv2.Information.Version)   ' connection is established  
  
      ' For remote connection, remote server name / ServerInstance needs to be specified  
      Dim srvConn2 As New ServerConnection(remoteSvrName)  
      srvConn2.LoginSecure = False  
      srvConn2.Login = sqlServerLogin  
      srvConn2.Password = password  
      Dim srv3 As New Server(srvConn2)  
      Console.WriteLine(srv3.Information.Version)   ' connection is established  
   End Sub  
End Class  
```  
  
## <a name="connecting-to-an-instance-of-sql-server-by-using-sql-server-authentication-in-visual-c"></a>在 Visual C# 中使用 SQL Server 驗證連接到 SQL Server 的執行個體  
 當您使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體時，您必須指定驗證類型。 此範例示範宣告 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件變數的替代方法，讓連接資訊得以重複使用。  
  
 此範例會示範如何連接到遠端的 Visual C#.NET 程式碼和*vPassword*包含登入和密碼。  
  
```csharp  
// compile with:   
// /r:Microsoft.SqlServer.Smo.dll  
// /r:Microsoft.SqlServer.ConnectionInfo.dll  
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using System;  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {   
      String sqlServerLogin = "user_id";  
      String password = "pwd";  
      String instanceName = "instance_name";  
      String remoteSvrName = "remote_server_name";  
  
      // Connecting to an instance of SQL Server using SQL Server Authentication  
      Server srv1 = new Server();   // connects to default instance  
      srv1.ConnectionContext.LoginSecure = false;   // set to true for Windows Authentication  
      srv1.ConnectionContext.Login = sqlServerLogin;  
      srv1.ConnectionContext.Password = password;  
      Console.WriteLine(srv1.Information.Version);   // connection is established  
  
      // Connecting to a named instance of SQL Server with SQL Server Authentication using ServerConnection  
      ServerConnection srvConn = new ServerConnection();  
      srvConn.ServerInstance = @".\" + instanceName;   // connects to named instance  
      srvConn.LoginSecure = false;   // set to true for Windows Authentication  
      srvConn.Login = sqlServerLogin;  
      srvConn.Password = password;  
      Server srv2 = new Server(srvConn);  
      Console.WriteLine(srv2.Information.Version);   // connection is established  
  
      // For remote connection, remote server name / ServerInstance needs to be specified  
      ServerConnection srvConn2 = new ServerConnection(remoteSvrName);  
      srvConn2.LoginSecure = false;  
      srvConn2.Login = sqlServerLogin;  
      srvConn2.Password = password;  
      Server srv3 = new Server(srvConn2);  
      Console.WriteLine(srv3.Information.Version);   // connection is established  
   }  
}  
```  
  
## <a name="see-also"></a>請參閱＜  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 <xref:Microsoft.SqlServer.Management.Common.ServerConnection>  
  
  