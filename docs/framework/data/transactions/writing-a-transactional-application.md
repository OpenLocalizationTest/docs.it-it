---
title: Scrittura di un'applicazione transazionale
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c988f5ab5a342ad3282414634ca3bfc21f481ea5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="writing-a-transactional-application"></a>Scrittura di un'applicazione transazionale
I programmatori di applicazioni transazionali possono utilizzare i due modelli di programmazione forniti dallo spazio dei nomi <xref:System.Transactions> per creare una transazione. È possibile utilizzare il modello di programmazione esplicito utilizzando il <xref:System.Transactions.Transaction> , classe o il modello di programmazione implicito in cui le transazioni vengono gestite automaticamente dall'infrastruttura, utilizzando la <xref:System.Transactions.TransactionScope> classe. È consigliabile utilizzare il modello di esecuzione implicita delle transazioni per lo sviluppo. È possibile trovare ulteriori informazioni sull'utilizzo di un ambito di transazione nel [implementazione di una transazione implicita con ambito di transazione](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) argomento.  
  
 Entrambi i modelli supportano il commit delle transazioni quando il programma raggiunge uno stato coerente. Se il commit riesce, il sistema esegue il commit permanente della transazione. Se il commit non riesce, la transazione viene interrotta. Se risulta impossibile completare correttamente una transazione, il programma dell'applicazione tenta di interromperla e quindi di annullarne gli effetti.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
### <a name="creating-a-transaction"></a>Creazione di una transazione  
 Lo spazio dei nomi <xref:System.Transactions> offre due modelli per creare una transazione. Questi modelli vengono descritti negli argomenti seguenti.  
  
 [Implementazione di una transazione implicita con ambito di transazione](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Descrive il modo in cui lo spazio dei nomi <xref:System.Transactions> supporta la creazione di transazioni implicite mediante la classe <xref:System.Transactions.TransactionScope>.  
  
 [Implementazione di una transazione esplicita utilizzando CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Descrive il modo in cui lo spazio dei nomi <xref:System.Transactions> supporta la creazione di transazioni esplicite mediante la classe <xref:System.Transactions.CommittableTransaction>.  
  
### <a name="escalating-transaction-management"></a>Gestione dell'escalation delle transazioni  
 Quando una transazione deve accedere a una risorsa contenuta in un altro dominio applicazione oppure quando si desidera integrare le risorse in un altro gestore di risorse durevoli, il sistema esegue automaticamente l'escalation di tale transazione in modo che venga gestita dal gestore MSDTC. Viene descritta l'escalation delle transazioni nel [escalation della gestione transazioni](../../../../docs/framework/data/transactions/transaction-management-escalation.md) argomento.  
  
### <a name="concurrency"></a>Concorrenza  
 L'argomento [gestione della concorrenza con DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) viene illustrato come è possibile ottenere concorrenza tra le attività asincrone mediante il <xref:System.Transactions.DependentTransaction> classe.  
  
### <a name="com-interop"></a>Interoperabilità COM+  
 L'argomento [interoperabilità con servizi aziendali e le transazioni COM+](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) viene illustrato come effettuare le transazioni distribuite interagire con le transazioni COM+.  
  
### <a name="diagnostics"></a>Diagnostica  
 [Le tracce di diagnostica](../../../../docs/framework/data/transactions/diagnostic-traces.md) descrive come è possibile utilizzare i codici di traccia generati dal <xref:System.Transactions> infrastruttura per risolvere gli errori nelle applicazioni.  
  
### <a name="working-within-aspnet"></a>Utilizzo delle funzionalità all'interno di ASP.NET  
 Il [utilizzando System. Transactions in ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) argomento viene descritto come è possibile utilizzare correttamente <xref:System.Transactions> all'interno di un'applicazione ASP.NET.
