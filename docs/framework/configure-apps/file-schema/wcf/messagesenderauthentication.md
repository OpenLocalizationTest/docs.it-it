---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a008919cc068ca5cdd841ec67f1a7194bbffcd8c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="ltmessagesenderauthenticationgt"></a>&lt;messageSenderAuthentication&gt;
Specifica impostazioni di autenticazione per certificato peer usato dal mittente di un messaggio.  
  
 \<System. ServiceModel >  
\<i comportamenti >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials >  
\<peer >  
\<messageSenderAuthentication >  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`certificateValidationMode`|Enumerazione facoltativa. Specifica una delle cinque modalità usate per convalidare credenziali. L'attributo è di tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode>. Se impostato su `Custom`, è necessario fornire anche un `customCertificateValidator`.|  
|`customCertificateValidatorType`|Stringa facoltativa. Specifica un tipo e un assembly usati per convalidare un tipo personalizzato. Questo attributo deve essere impostato quando `certificateValidationMode` è impostato su `Custom`. L'attributo è di tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator>. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] fornisce un validator del certificato peer predefinita che verifica il certificato peer a fronte dell'archivio Persone attendibili. Verifica inoltre che il certificato sia concatenato a una radice valida. È possibile implementare una convalida personalizzata per specificare un comportamento diverso e usare questo attributo per puntare alla convalida personalizzata.|  
|`revocationMode`|Enumerazione facoltativa. Specifica la modalità di revoca dei certificati. L'attributo è di tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>. Il sistema verifica che il certificato peer non sia stato revocato cercandolo nell'elenco dei certificati revocati. Questo controllo può essere eseguito controllando in linea o in un elenco di revoche memorizzato nella cache. È possibile disattivare il controllo di revoca impostando l'attributo su NoCheck.|  
|`trustedStoreLocation`|Enumerazione facoltativa. Specifica il percorso dell'archivio dati attendibile in cui il certificato peer viene convalidato dal sistema di sicurezza [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. L'attributo è di tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<peer >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|Specifica le credenziali correnti per un nodo peer.|  
  
## <a name="remarks"></a>Note  
 Se è stata scelta l'autenticazione dei messaggi, sarà necessario configurare questo elemento. Per i canali di output, ogni messaggio viene firmato utilizzando il certificato fornito dal [ \<certificato >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md). Prima che vengano recapitati all'applicazione, tutti i messaggi vengono controllati a fronte delle credenziali del messaggio usando la convalida specificata dall'attributo `customCertificateValidatorType` di questo elemento. La convalida può accettare o rifiutare la credenziale.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [Utilizzo dei certificati](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Rete peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Autenticazione dei messaggi del canale peer](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Autenticazione personalizzata canale peer](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Protezione delle applicazioni del canale Peer](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
