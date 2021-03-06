---
title: "Funzionalità di sicurezza con associazioni personalizzate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9d252dca363c952dde44b499363e285d4bb7eb82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="security-capabilities-with-custom-bindings"></a>Funzionalità di sicurezza con associazioni personalizzate
Per eseguire la maggior parte delle attività di sicurezza comuni, è possibile utilizzare una delle associazioni fornite dal sistema. Se è necessario un maggiore controllo, tuttavia, è possibile creare un'associazione personalizzata con un oggetto <xref:System.ServiceModel.Channels.SecurityBindingElement>, come viene spiegato in questi argomenti. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]associazioni personalizzate, vedere [associazioni personalizzate](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Modalità di autenticazione di SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 Vengono descritte le modalità di autenticazione possibili con un'associazione personalizzata.  
  
 [Procedura: creare un'associazione personalizzata usando SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Vengono descritti i passaggi di base per la creazione di un'associazione personalizzata con un elemento di sicurezza.  
  
 [Procedura: creare un elemento SecurityBindingElement per una modalità di autenticazione specificato](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Viene descritto come creare un elemento di sicurezza per una modalità di autenticazione specificata.  
  
 [Procedura: disattivare sessioni protette in una classe WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Viene descritto come disattivare sessioni protette durante la creazione di un servizio federativo.  
  
 [Procedura: abilitare il rilevamento riproduzione messaggio](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 Viene descritto come determinare il verificarsi di un attacco di tipo replay.  
  
 [Procedura: creare una credenziale di supporto](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 Viene descritto come fornire una credenziale di supporto a un servizio, se il servizio lo richiede.  
  
 [Procedura: impostare una conferma della firma](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 Vengono descritti i passaggi necessari per confermare le firme durante la firma digitale dei messaggi.  
  
 [Procedura: impostare un numero massimo di sfasamento](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 Viene descritto come impostare la differenza oraria massima consentita tra un servizio e un client.  
  
 [Procedura: disabilitare la crittografia di firme digitali](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 Viene descritto come la disattivazione della crittografia di firme digitali possa influire positivamente sulle prestazioni.  
  
## <a name="reference"></a>Riferimento  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<sicurezza >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Informazioni sul livello di protezione](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [Protezione di servizi e client](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Associazioni e protezione](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Cenni preliminari sulla sicurezza](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Associazioni fornite dal sistema](../../../../docs/framework/wcf/system-provided-bindings.md)
