---
title: Notifiche di query in SQL Server
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 854407d2e6d1341d5917cc78664c1f653e55fa35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="query-notifications-in-sql-server"></a>Notifiche di query in SQL Server
Basate sull'infrastruttura Service Broker, le notifiche di query consentono di inviare notifiche alle applicazioni quando i dati vengono modificati. Questa funzionalità è particolarmente utile per le applicazioni che forniscono una cache di informazioni da un database, ad esempio un'applicazione Web, e che richiedono una notifica quando i dati di origine vengono modificati.  
  
 Sono disponibili tre metodi per implementare le notifiche di query usando ADO.NET:  
  
1.  L'implementazione di basso livello è fornita dalla classe `SqlNotificationRequest` che espone la funzionalità sul lato server e consente di eseguire un comando con una richiesta di notifica.  
  
2.  L'implementazione di alto livello è fornita dalla classe `SqlDependency`, che consente un'astrazione di alto livello della funzionalità di notifica tra l'applicazione di origine e SQL Server, permettendo di usare una dipendenza per rilevare le modifiche nel server. Nella maggior parte dei casi si tratta del modo più semplice ed efficace per sfruttare la funzionalità di notifica di SQL Server in applicazioni client gestite usando il provider di dati .NET Framework per SQL Server.  
  
3.  Nelle applicazioni Web compilate con ASP.NET 2.0 o versione successiva è inoltre possibile usare le classi helper `SqlCacheDependency`.  
  
 Le notifiche di query vengono usate per applicazioni che richiedono l'aggiornamento delle visualizzazioni o delle cache in seguito a modifiche dei dati sottostanti. Microsoft SQL Server consente ad applicazioni .NET Framework di inviare un comando a SQL Server e di richiedere che venga generata una notifica se l'esecuzione del comando produrrebbe set di risultati diversi da quelli recuperati inizialmente. Le notifiche generate nel server vengono inviate tramite code per l'elaborazione successiva.  
  
 È possibile impostare le notifiche per le istruzioni SELECT ed EXECUTE. Quando si usa un'istruzione EXECUTE, SQL Server registra una notifica per il comando eseguito anziché per l'istruzione EXECUTE stessa. Il comando deve soddisfare i requisiti e le limitazioni previste per un'istruzione SELECT. Quando un comando che registra una notifica contiene più di un'istruzione, il Motore di database crea una notifica per ogni istruzione inclusa nel batch.  
  
 Se si sviluppa un'applicazione in cui è necessario notifiche frazioni di secondo affidabili quando i dati, rivedere le sezioni **pianificazione di una strategia di notifiche di Query efficienti** e **alternative alle Query Le notifiche** nel [pianificazione per le notifiche](http://go.microsoft.com/fwlink/?LinkId=211984) argomento nella documentazione Online di SQL Server. Per altre informazioni sulle notifiche di query e su SQL Server Service Broker, vedere i collegamenti seguenti agli argomenti della documentazione online di SQL Server.  
  
 **Documentazione online di SQL Server**  
  
-   [Notifiche di Query](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [Creazione di una Query da notificare](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Service Broker](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [Centro informazioni per sviluppatori di Service Broker](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Sviluppo (Service Broker)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Abilitazione di notifiche di Query](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 Viene descritto come usare le notifiche di query, compresi i requisiti per l'abilitazione e l'uso.  
  
 [SqlDependency in un'applicazione ASP.NET](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 Viene illustrato come usare le notifiche di query da un'applicazione ASP.NET.  
  
 [Il rilevamento delle modifiche con SqlDependency](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 Viene illustrato come rilevare i casi in cui i risultati delle query saranno diversi da quelli ricevuti in origine.  
  
 [Esecuzione di SqlCommand con SqlNotificationRequest](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Viene illustrata la configurazione di un oggetto <xref:System.Data.SqlClient.SqlCommand> da usare con una notifica di query.  
  
## <a name="reference"></a>Riferimento  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Vengono descritti la classe <xref:System.Data.Sql.SqlNotificationRequest> e tutti i relativi membri.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Vengono descritti la classe <xref:System.Data.SqlClient.SqlDependency> e tutti i relativi membri.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Vengono descritti la classe <xref:System.Web.Caching.SqlCacheDependency> e tutti i relativi membri.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server e ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](http://go.microsoft.com/fwlink/?LinkId=217917)
