---
title: 'Procedura: disattivare la crittografia delle firme digitali'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce72cb4d71bcc08980104158940a15ea6ecd0c6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Procedura: disattivare la crittografia delle firme digitali
Per impostazione predefinita, un messaggio viene firmato e la firma viene crittografata digitalmente. Per controllare questo comportamento è necessario creare un'associazione personalizzata con un'istanza della classe <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e impostare la proprietà `MessageProtectionOrder` della classe su un valore dell'enumerazione <xref:System.ServiceModel.Security.MessageProtectionOrder>. Il valore predefinito è <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Questo processo può richiedere fino al 30 percento in più del tempo necessario per eseguire la firma e la crittografia in base alla dimensione globale del messaggio (minore è la dimensione del messaggio, maggiore sarà l'impatto sulle prestazioni). La disattivazione della crittografia della firma può tuttavia consentire a un utente malintenzionato di intuire il contenuto del messaggio poiché l'elemento di firma contiene il codice hash del testo normale di ogni parte firmata del messaggio. Ad esempio, anche se il corpo del messaggio viene crittografato per impostazione predefinita, la firma non crittografata contiene il codice hash del corpo del messaggio prima della crittografia. Se il set di valori possibili per la parte firmata e crittografata è limitato, un utente malintenzionato può essere in grado di dedurre il contenuto analizzando il valore hash. La crittografia della firma consente di ridurre il rischio di attacchi.  
  
 È consigliabile quindi disattivare la crittografia della firma soltanto quando il valore del contenuto è basso o il set di valori possibili del contenuto è ampio e non deterministico e il livello delle prestazioni è più importante rispetto alla riduzione del rischio di attacchi descritto sopra.  
  
> [!NOTE]
>  Se il messaggio non contiene alcun elemento crittografato, l'elemento di firma non viene crittografato, anche quando la proprietà <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> è impostata su <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Questo comportamento si verifica anche con le associazioni fornite dal sistema. Per tutte le associazioni fornite dal sistema l'ordine di protezione dei messaggi è impostato su `SignBeforeEncryptAndEncryptSignature`. Il codice WSDL generato da [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] conterrà comunque l'asserzione `<sp:EncryptSignature>`.  
  
### <a name="to-disable-digital-signing"></a>Per disattivare la firma digitale  
  
1.  Creare un oggetto <xref:System.ServiceModel.Channels.CustomBinding>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Procedura: creare un'associazione personalizzata usando SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Aggiungere un elemento <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> alla raccolta di associazioni.  
  
3.  Impostare la proprietà <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> su <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> oppure impostare la proprietà <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> su <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di sicurezza con associazioni personalizzate](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
