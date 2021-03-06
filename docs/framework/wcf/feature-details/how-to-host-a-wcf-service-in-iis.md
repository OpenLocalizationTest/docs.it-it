---
title: 'Procedura: ospitare un servizio WCF in IIS'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 934b5d16cdea7026e0e7874cf04ab53c8fbdf58e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Procedura: ospitare un servizio WCF in IIS
In questo argomento vengono delineati i passaggi di base necessari per creare un servizio [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ospitato in Internet Information Services (IIS). Questo argomento presuppone la conoscenza di IIS e la comprensione dello strumento di gestione IIS per creare e gestire applicazioni IIS. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]IIS vedere [Internet Information Services](http://go.microsoft.com/fwlink/?LinkId=132449). Un servizio [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in esecuzione nell'ambiente IIS sfrutta appieno le funzionalità IIS, quali il riciclo dei processi, la chiusura per inattività, il monitoraggio dell'integrità dei processi e l'attivazione basata su messaggi. Questa opzione di hosting richiede che IIS sia configurato correttamente, ma non richiede la scrittura di codice di hosting come parte dell'applicazione. È possibile utilizzare l'hosting IIS solo con un trasporto HTTP.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]come [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interagire, vedere [servizi WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]configurazione della protezione, vedere [sicurezza](../../../../docs/framework/wcf/feature-details/security.md).  
  
 Per la copia di origine di questo esempio, vedere [IIS che ospita utilizzando il codice Inline](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Per creare un servizio ospitato da IIS  
  
1.  Confermare che IIS sia installato e in esecuzione nel computer. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l'installazione e configurazione di IIS vedere [installazione e configurazione di IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  Creare una nuova cartella per i file dell'applicazione denominata "IISHostedCalcService", assicurarsi che [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] abbia accesso al contenuto della cartella e utilizzare lo strumento di gestione IIS per creare una nuova applicazione IIS situata fisicamente in questa directory dell'applicazione. Quando si crea un alias per la directory dell'applicazione utilizzare "IISHostedCalc".  
  
3.  Creare un nuovo file "service.svc" nella directory dell'applicazione. Modificare il file, aggiungere il codice seguente @ServiceHost elemento.  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  Creare una sottodirectory App_Code all'interno della directory dell'applicazione.  
  
5.  Creare un file di codice denominato Service.cs nella sottodirectory App_Code.  
  
6.  Aggiungere le istruzioni using riportate di seguito all'inizio del file Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  Aggiungere la seguente dichiarazione dello spazio dei nomi dopo le istruzioni using.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  Definire il contratto di servizio all'interno della dichiarazione dello spazio dei nomi come mostrato nel codice seguente.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implementare il contratto di servizio dopo la sua definizione come illustrato nel codice seguente.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Creare un file denominato "Web.config" e aggiungere il codice di configurazione seguente nel file. In fase di esecuzione, l'infrastruttura [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilizza le informazioni per costruire un endpoint con cui possano comunicare le applicazioni client.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     In questo esempio vengono specificati in modo esplicito gli endpoint del file di configurazione. Se non vengono aggiunti endpoint al servizio, il runtime aggiunge gli endpoint predefiniti. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]predefinito endpoint, associazioni e comportamenti, vedere [configurazione semplificata](../../../../docs/framework/wcf/simplified-configuration.md) e [configurazione semplificata per i servizi WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
11. Per assicurarsi che il servizio sia ospitato correttamente, aprire un'istanza di Internet Explorer e passare all'URL del servizio: `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Esempio  
 Di seguito è riportato un elenco completo del codice per il servizio calcolatrice ospitato da IIS.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Vedere anche  
 [Hosting in Internet Information Services](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Servizi di hosting](../../../../docs/framework/wcf/hosting-services.md)  
 [Servizi WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Sicurezza](../../../../docs/framework/wcf/feature-details/security.md)  
 [Windows Server AppFabric con funzionalità di Hosting](http://go.microsoft.com/fwlink/?LinkId=201276)
