---
title: Gestione degli errori HTTP Web WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 156960a6594f5475e339b36e5dabf46f26d13d62
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-web-http-error-handling"></a>Gestione degli errori HTTP Web WCF
La gestione degli errori HTTP Web di [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] consente di restituire errori da servizi HTTP Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] che specificano un codice di stato HTTP e restituiscono dettagli dell'errore utilizzando lo stesso formato dell'operazione (ad esempio, XML o JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Gestione degli errori HTTP Web WCF  
 La classe <xref:System.ServiceModel.Web.WebFaultException> definisce un costruttore che consente di specificare un codice di stato HTTP. Questo codice di stato viene quindi restituito al client. Versione generica della classe <xref:System.ServiceModel.Web.WebFaultException>, <xref:System.ServiceModel.Web.WebFaultException%601> consente di restituire un tipo definito dall'utente che contiene informazioni sull'errore verificatosi. Questo oggetto personalizzato viene serializzato utilizzando il formato specificato dall'operazione e restituito al client. Nell'esempio riportato di seguito viene illustrato il modo in cui restituire un codice di stato HTTP.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 Nell'esempio seguente viene illustrato come restituire un codice di stato HTTP e informazioni aggiuntive in un tipo definito dall'utente. `MyErrorDetail` è un tipo definito dall'utente che contiene informazioni aggiuntive sull'errore che si è verificato.  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 Il codice precedente restituisce una risposta HTTP con il codice di stato proibito e un corpo che contiene un'istanza dell'oggetto `MyErrorDetails`. Il formato dell'oggetto `MyErrorDetails` viene determinato dagli elementi indicati di seguito.  
  
-   Valore del parametro `ResponseFormat` dell'attributo <xref:System.ServiceModel.Web.WebGetAttribute> o <xref:System.ServiceModel.Web.WebInvokeAttribute> specificato nell'operazione del servizio.  
  
-   Valore di <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
-   Valore della proprietà <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> accedendo a <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]informazioni su come questi valori influisce sulla formattazione dell'operazione, vedere [formattazione di HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> è un'eccezione <xref:System.ServiceModel.FaultException> e pertanto può essere utilizzata come modello di programmazione di eccezione dell'errore per i servizi che espongono endpoint SOAP e HTTP Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Modello di programmazione HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Formattazione di HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [Definizione e specifica degli errori](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [Gestione di eccezioni ed errori](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Invio e ricezione degli errori](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
