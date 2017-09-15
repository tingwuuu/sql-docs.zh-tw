---
title: "檢視及修改發送訂閱屬性 | Microsoft 文件"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing replication properties
- push subscriptions [SQL Server replication], properties
- subscriptions [SQL Server replication], push
- push subscriptions [SQL Server replication], modifying
- modifying replication properties, push subscriptions
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 801d2995-7aa5-4626-906e-c8190758ec71
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3fc246be116d9468733d8b66f501717a4310bba2
ms.contentlocale: zh-tw
ms.lasthandoff: 06/22/2017

---
# <a name="view-and-modify-push-subscription-properties"></a>檢視及修改發送訂閱屬性
  本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視及修改發送訂閱屬性。  
  
 **本主題內容**  
  
-   **若要檢視及修改發送訂閱屬性，請使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Replication Management Objects (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 從「發行者」在以下項目中檢視並修改發送訂閱屬性：  
  
-   [訂閱屬性 - \<發行者>: \<發行集資料庫>] 對話方塊，該對話方塊可從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 存取。  
  
-   **[所有訂閱]** 索引標籤，在「複寫監視器」中可用。 如需啟動複寫監視器的資訊，請參閱[啟動複寫監視器](../../relational-databases/replication/monitor/start-the-replication-monitor.md)。  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-management-studio"></a>若要在 Management Studio 中檢視並修改發送訂閱屬性  
  
1.  連接到 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。  
  
2.  展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。  
  
3.  展開適當的發行集，以滑鼠右鍵按一下訂閱，然後按一下 **[屬性]**。  
  
4.  必要時修改任何屬性，然後按一下 **[確定]**。  
  
#### <a name="to-view-and-modify-push-subscription-properties-in-replication-monitor"></a>若要在複寫監視器中檢視和修改發送訂閱屬性  
  
1.  在複寫監視器的左窗格中展開發行者群組，展開發行者，然後按一下發行集。  
  
2.  按一下 **[所有訂閱]** 索引標籤。  
  
3.  以滑鼠右鍵按一下訂閱，然後按一下 **[屬性]**。  
  
4.  必要時修改任何屬性，然後按一下 **[確定]**。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 您可以使用複寫預存程序來以程式設計的方式修改發送訂閱及存取其屬性。 使用哪些預存程序要依訂閱所屬的發行集類型而定。  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>檢視快照式或交易式發行集之發送訂閱的屬性  
  
1.  在發行集資料庫的發行者上，執行 [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)。 指定 **@publication**或 Replication Management Objects (RMO)，在 **@subscriber**，並針對 **@article** 指定 **@article**存取。  
  
2.  在發行集資料庫的發行者上，執行 [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)，並指定 **@subscriber**存取。  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>變更快照式或交易式發行集之發送訂閱的屬性  
  
1.  在發行集資料庫的發行者上，執行 [sp_changesubscriber](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)，並指定 **@subscriber** 及針對所變更的訂閱者屬性指定任何參數。  
  
2.  在發行集資料庫的發行者上，執行 [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)。 指定 **@publication**或 Replication Management Objects (RMO)，在 **@subscriber**或 Replication Management Objects (RMO)，在 **@destination_db**，並將 **@article** 指定 **@article**的值、將變更的訂閱屬性指定為 **@property**，並將新的值指定為 **@value**存取。 這樣會變更發送訂閱的安全性設定。  
  
3.  (選擇性) 若要變更訂閱的 Data Transformation Services (DTS) 封裝屬性，請在訂閱資料庫的訂閱者上，執行 [sp_changesubscriptiondtsinfo](../../relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql.md) 。 針對 **@jobid** 指定散發代理程式作業的識別碼以及下列 DTS 封裝屬性：  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     這樣會變更訂閱的 DTS 封裝屬性。  
  
    > [!NOTE]  
    >  可以執行 [sp_helpsubscription](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)來取得作業識別碼。  
  
#### <a name="to-view-the-properties-of-a-push-subscription-to-a-merge-publication"></a>檢視合併式發行集之發送訂閱的屬性  
  
1.  在發行集資料庫的發行者上，執行 [sp_helpmergesubscription](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)。 指定 **@publication** 和 **@subscriber**存取。  
  
2.  在發行者端，執行 [sp_helpsubscriberinfo](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)，並指定 **@subscriber**存取。  
  
#### <a name="to-change-the-properties-of-a-push-subscription-to-a-merge-publication"></a>變更合併式發行集之發送訂閱的屬性  
  
1.  在發行集資料庫的發行者上，執行 [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)。 指定 **@publication**或 Replication Management Objects (RMO)，在 **@subscriber**或 Replication Management Objects (RMO)，在 **@subscriber_db**的值、將變更的訂閱屬性指定為 **@property**，並將新的值指定為 **@value**存取。  
  
###  <a name="TsqlExample"></a> 範例 (Transact-SQL)  
  
##  <a name="RMOProcedure"></a> 使用 Replication Management Objects (RMO)  
 用於檢視或修改發送訂閱屬性的 RMO 類別，將取決於該發送訂閱所訂閱的發行集類型而定。  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-snapshot-or-transactional-publication"></a>檢視或修改快照式或交易式發行集之發送訂閱的屬性  
  
1.  使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連線。  
  
2.  建立 <xref:Microsoft.SqlServer.Replication.TransSubscription> 類別的執行個體。  
  
3.  設定 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A> 和 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 屬性。  
  
4.  針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的<xref:Microsoft.SqlServer.Management.Common.ServerConnection>。  
  
5.  呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。 如果此方法傳回 **false**，則表示步驟 3 中的訂閱屬性定義不正確，或者此訂閱不存在。  
  
6.  (選擇性) 若要變更屬性，請為可以設定的其中一個 <xref:Microsoft.SqlServer.Replication.TransSubscription> 屬性設定新值，然後呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。  
  
7.  (選擇性) 若要檢視新的設定，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法，重新載入訂閱的屬性。  
  
#### <a name="to-view-or-modify-properties-of-a-push-subscription-to-a-merge-publication"></a>檢視或修改合併式發行集之發送訂閱的屬性  
  
1.  使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與訂閱者的連線。  
  
2.  建立 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 類別的執行個體。  
  
3.  設定 <xref:Microsoft.SqlServer.Replication.Subscription.PublicationName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.DatabaseName%2A>、<xref:Microsoft.SqlServer.Replication.Subscription.SubscriberName%2A> 和 <xref:Microsoft.SqlServer.Replication.Subscription.SubscriptionDBName%2A> 屬性。  
  
4.  針對 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定步驟 1 中的<xref:Microsoft.SqlServer.Management.Common.ServerConnection>。  
  
5.  呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法以取得物件的屬性。 如果此方法傳回 **false**，則表示步驟 3 中的訂閱屬性定義不正確，或者此訂閱不存在。  
  
6.  (選擇性) 若要變更屬性，請為可以設定的其中一個 <xref:Microsoft.SqlServer.Replication.MergeSubscription> 屬性設定新值，然後呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。  
  
7.  (選擇性) 若要檢視新的設定，請呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> 方法，重新載入訂閱的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [檢視訂閱的資訊並執行工作 &#40;複寫監視器&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [複寫安全性最佳做法](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [訂閱發行集](../../relational-databases/replication/subscribe-to-publications.md)  
  
  