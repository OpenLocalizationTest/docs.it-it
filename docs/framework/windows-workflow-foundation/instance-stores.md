---
title: Archivio di istanze
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c794c6e20b479ea4686caba29704f8851d108432
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="instance-stores"></a>Archivio di istanze
Un archivio di istanze è un contenitore logico di istanze, ovvero lo spazio in cui vengono archiviati i dati e i metadati dell'istanza. Un archivio di istanze non implica l'archiviazione fisica dedicata e può contenere informazioni durevoli in un database di SQL Server o informazioni sullo stato non durevoli in una memoria. In [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] è disponibile l'archivio di istanze del flusso di lavoro SQL, vale a dire un'implementazione concreta di un archivio di istanze che consente ai flussi di lavoro di rendere persistenti i dati e i metadati dell'istanza in un database di SQL Server 2005 o di SQL Server 2008. Windows Server AppFabric fornisce inoltre un'implementazione concreta di un archivio di istanze. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Archivio di istanze di Windows Server App Fabric, Query e provider del controllo](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 L'API di persistenza è l'interfaccia tra un host e un archivio di istanze che consente all'host di inviare richieste di comando (ad esempio <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> e <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) all'archivio di istanze. L'implementazione concreta di questa API viene definita provider di persistenza. Il provider di persistenza riceve richieste da un host e modifica l'archivio di istanze.  
  
 Gli host e gli archivi di istanze sono modulari in modo che un host possa essere usato con molti archivi di istanze e un archivio di istanze possa essere usato con molti host. Un archivio di istanze viene ottimizzato in genere per i modelli di utilizzo di un particolare host, anche se l'archivio di istanze e l'host possono evolvere in cicli di vita indipendenti. Ad esempio, il **WorkflowServiceHost** e **SqlWorkflowInstanceStore** sono progettati per funzionare correttamente insieme. È possibile creare il proprio archivio di istanze per rendere persistenti i dati e i metadati delle istanze del servizio del flusso di lavoro e utilizzare l'archivio di istanze con il **WorkflowServiceHost**. È possibile creare ad esempio un oggetto OracleWorkflowInstanceStore che consenta ai flussi di lavoro di rendere persistenti le informazioni in un database Oracle anziché salvarle in un database di SQL Server.  
  
 In genere gli host possono essere estesi con funzionalità aggiuntiva che modifica gli oggetti persistenti. Ad esempio, un sistema di persistenza delle istanze può disporre di un host del flusso di lavoro, un'estensione che supporta l'operazione "Suspend" e un archivio di istanze SQL.  L'host del flusso di lavoro potrebbe inviare un comando standard quale Salva o Carica per salvare o caricare un flusso di lavoro da un archivio di istanze o per salvare un flusso di lavoro in un archivio di istanze. L'estensione di sospensione potrebbe aggiungere ulteriore semantica ai comandi per il salvataggio e il caricamento di istanze del flusso di lavoro in modo che un'istanza del flusso di lavoro sospesa non possa essere caricata. Il provider di persistenza per l'archivio di istanze SQL riconosce i comandi per il salvataggio e il caricamento di istanze del flusso di lavoro e li implementa chiamando stored procedure appropriate che modificano le tabelle degli oggetti persistenti in un database di SQL Server.  
  
 Un host funge da proprietario di istanza all'interno di un archivio di istanze e può operare come più proprietari di istanza con più archivi di istanze contemporaneamente. L'host fornisce i GUID per chiavi di istanza associate alle istanze. Una chiave di istanza è un alias univoco che identifica un'istanza. Il sistema di persistenza crea, aggiorna ed elimina le informazioni del proprietario di istanza quando esegue i comandi richiesti dagli host.  
  
 Nell'elenco seguente sono indicati i passaggi importanti relativi all'interazione dell'host con l'archivio di istanze:  
  
1.  Ottenere un **InstanceStore** da un provider di persistenza.  

2.  Ottenere l'handle per un'istanza chiamando il <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> metodo il **InstanceStore**.  
  
3.  Richiamare i comandi sull'handle di istanza chiamando il <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> metodo il **InstanceStore**.  
  
4.  Esaminare il <xref:System.Runtime.DurableInstancing.InstanceView> restituito da **instancestore. Execute** per determinare i risultati dei comandi.
