---
title: Progettazione e implementazione di servizi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3429a9145695a957089941d8c814d441da498c93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="designing-and-implementing-services"></a>Progettazione e implementazione di servizi
In questa sezione viene illustrato come definire e implementare [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contratti. Un contratto di servizio specifica quale endpoint comunica con il mondo esterno. A un livello più concreto, è un'istruzione su un set di messaggi specifici organizzati in modelli di scambio di messaggi di base (MEP, Message Exchange Pattern) quali, ad esempio, request/reply, unidirezionale e duplex. Se un contratto di servizio è un set logicamente correlato di scambi di messaggi, un'operazione di servizio è un singolo scambio di messaggi. Un'operazione `Hello` deve, ad esempio, accettare un messaggio (quindi il chiamante può annunciare il saluto) e può o non può restituire un messaggio (a seconda del livello di cortesia dell'operazione).  
  
 Per ulteriori informazioni sui contratti e altri componenti di base [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] concetti, vedere [concetti fondamentali di Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md). Questo argomento si incentra sulla comprensione dei contratti di servizio. Per ulteriori informazioni sulla compilazione di client che utilizzano contratti di servizio per connettersi ai servizi, vedere [panoramica dei Client WCF](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Panoramica  
 In questo argomento viene fornito un orientamento concettuale di alto livello alla progettazione e all'implementazione di servizi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Negli argomenti correlati vengono fornite informazioni più dettagliate sulle specifiche di progettazione e implementazione. Prima di progettare e implementare l'applicazione [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], è consigliabile:  
  
-   Comprendere cosa siano i contratti di servizio, come funzionino e come sia possibile crearne uno.  
  
-   Comprendere che i contratti prevedono requisiti minimi che la configurazione di runtime o l'ambiente host potrebbe non supportare.  
  
## <a name="service-contracts"></a>Contratti di servizio  
 In un contratto di servizio viene specificato quanto segue:  
  
-   Le operazioni esposte nel contratto.  
  
-   Forma delle operazioni in termini di messaggi scambiati.  
  
-   Tipi di dati di questi messaggi.  
  
-   Posizione delle operazioni.  
  
-   Protocolli e formati di serializzazione specifici usati per supportare la corretta comunicazione con il servizio.  
  
 Un contratto di ordine di acquisto può, ad esempio, includere un'operazione `CreateOrder` che accetta un input di tipi di informazioni sull'ordine e restituisce informazioni sull'esito positivo o negativo, incluso un identificatore di ordine. Può inoltre includere un'operazione `GetOrderStatus` che accetta un identificatore di ordine e restituisce informazioni sullo stato dell'ordine. Un contratto di servizio di questo tipo specificherebbe:  
  
1.  Che il contratto di ordine di acquisto è costituito da operazioni `CreateOrder` e `GetOrderStatus`.  
  
2.  Che le operazioni hanno specificato messaggi di input e di output.  
  
3.  I dati che questi messaggi possono contenere.  
  
4.  Istruzioni categoriali sull'infrastruttura di comunicazione necessaria per elaborare correttamente i messaggi. Questi dettagli includono, ad esempio, indicazioni sulla necessità della protezione, e sui tipi di sicurezza eventualmente necessari, per stabilire una corretta comunicazione.  
  
 Per comunicare questo tipo di informazioni da altre applicazioni su più piattaforme (incluse piattaforme non Microsoft), i contratti di servizio XML vengono pubblicamente espressi in formati XML standard, ad esempio [Web Services Description Language](http://go.microsoft.com/fwlink/?LinkId=94952) ( WSDL) e [XML Schema](http://go.microsoft.com/fwlink/?LinkId=94953) (XSD), tra gli altri. Gli sviluppatori operanti su molte piattaforme possono usare queste informazioni pubbliche sui contratti per creare applicazioni che possano comunicare con il servizio, perché comprendono il linguaggio della specifica e perché tali linguaggi sono progettati per consentire l'interoperabilità descrivendo i tipi, i formati e i protocolli pubblici supportati dal servizio. Per ulteriori informazioni su come [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] handle di questo tipo di informazioni, vedere [metadati](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 I contratti possono essere espressi in molti modi e, sebbene WSDL e XSD siano eccellenti per descrivere i servizi in modo accessibile, sono linguaggi difficili da utilizzare direttamente e costituiscono semplici descrizioni di un servizio, non implementazioni del contratto di servizio. Pertanto, le applicazioni [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] utilizzano interfacce, classi e attributi gestiti sia per definire la struttura di un servizio sia per implementarlo.  
  
 Il contratto risulta definito nei tipi gestiti può essere *esportato* come metadati, WSDL e XSD, quando richiesto da client o altri implementatori del servizio. Il risultato è un modello di programmazione semplice, che può essere descritto (utilizzando metadati pubblici) per qualsiasi applicazione client. I dettagli dei messaggi SOAP sottostanti, le informazioni sul trasporto e sulla sicurezza e così via possono essere gestiti da [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], che esegue automaticamente le conversioni necessarie tra il sistema dei tipi di contratto di servizio e il sistema dei tipi XML.  
  
 Per ulteriori informazioni sulla progettazione di contratti, vedere [progettazione contratti di servizio](../../../docs/framework/wcf/designing-service-contracts.md). Per ulteriori informazioni sull'implementazione dei contratti, vedere [contratti di servizio che implementa](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Orientamento ai messaggi  
 L'utilizzo di interfacce, classi e metodi gestiti per modellare le operazioni di servizio è piuttosto semplice se si utilizzano abitualmente firme dei metodi in stile RPC (Remote Procedure Call), in cui il passaggio di parametri in un metodo e la restituzione di valori costituiscono la forma standard per richiedere la funzionalità di un oggetto o di un altro tipo di codice. I programmatori che, ad esempio, utilizzano linguaggi gestiti come [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] e C++ COM possono applicare le proprie conoscenze sull'approccio in stile RPC (utilizzando oggetti o interfacce) alla creazione di contratti di servizio [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] senza incorrere in problemi inerenti ai sistemi con oggetti distribuiti in stile RPC. L'orientamento ai servizi offre il vantaggio di una programmazione orientata ai messaggi, ad accoppiamento debole, mantenendo comunque la semplicità della programmazione RPC.  
  
 Molti programmatori preferiscono utilizzare interfacce di programmazione di applicazioni orientate ai messaggi, ad esempio le code di messaggi come Microsoft MSMQ, gli spazi dei nomi <xref:System.Messaging> di .NET Framework o l'invio di XML non strutturato nelle richieste HTTP, solo per citarne alcune. Per ulteriori informazioni sulla programmazione a livello di messaggio, vedere [con contratti di messaggio](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [canale del servizio a livello di programmazione](../../../docs/framework/wcf/extending/service-channel-level-programming.md), e [l'interoperabilità con applicazioni POX](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Informazioni sulla gerarchia di requisiti  
 Un contratto di servizio raggruppa le operazioni, specifica il modello di scambio dei messaggi, i tipi di messaggio e i tipi di dati contenuti nei messaggi e indica le categorie di comportamento runtime che un'implementazione deve avere per supportare il contratto (se, ad esempio, è necessario che i messaggi siano crittografati e firmati). Il contratto di servizio stesso non specifica con precisione in che modo vengono soddisfatti questi requisiti, ma solo che devono essere soddisfatti. Il tipo di crittografia e la modalità di firma di un messaggio dipendono dall'implementazione e dalla configurazione di un servizio conforme.  
  
 Si noti il modo in cui il contratto richiede certe caratteristiche dell'implementazione del contratto di servizio e della configurazione di runtime per l'aggiunta di un comportamento. Il set dei requisiti che devono essere soddisfatti per esporre un servizio affinché possa essere usato si basa sul set di requisiti precedente. Se un contratto prevede requisiti per l'implementazione, un'implementazione può richiedere ancora più caratteristiche di configurazione e associazioni che consentono l'esecuzione del servizio. Infine, anche l'applicazione host deve supportare tutti i requisiti aggiunti dalla configurazione e dalle associazioni del servizio.  
  
 Questo processo relativo ai requisiti aggiuntivi è importante da tener presente quando si progetta, implementa, configura e ospita un'applicazione del servizio [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]. Il contratto può, ad esempio, specificare che deve essere supportata una sessione. In questo caso sarà quindi necessario configurare le associazioni per supportare il requisito contrattuale o l'implementazione del servizio non funzionerà. Se il servizio richiede invece l'autenticazione integrata di Windows ed è ospitato in Internet Information Services (IIS), nell'applicazione Web in cui risiede il servizio deve essere attivata l'autenticazione integrata di Windows e disattivato il supporto di utenti anonimi. Per ulteriori informazioni sulle funzionalità e impatto dei tipi di applicazione di servizio diversi host, vedere [servizi di Hosting](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione dei contratti di servizio](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Implementazione dei contratti di servizio](../../../docs/framework/wcf/implementing-service-contracts.md)
