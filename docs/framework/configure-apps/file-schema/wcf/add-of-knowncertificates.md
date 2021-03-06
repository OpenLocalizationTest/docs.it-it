---
title: '&lt;add&gt; di &lt;knownCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 30b3216842b602745ad40d1743175350aba78296
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltknowncertificatesgt"></a>&lt;add&gt; di &lt;knownCertificates&gt;
Aggiunge un certificato X.509 alla raccolta di certificati conosciuti.  
  
 \<System. ServiceModel >  
\<i comportamenti >  
\<serviceBehaviors >  
\<comportamento >  
\<serviceCredentials >  
\<issuedTokenAuthentication >  
\<knownCertificates >  
\<add>  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<knownCertificates>   
   <add findValue="String"  
      storeLocation="CurrentUser/LocalMachine"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|findValue|Stringa. Valore da cercare.|  
|storeLocation|Enumerazione. Uno di due percorsi dell'archivio in cui cercare.|  
|storeName|Enumerazione. Uno degli archivi di sistema in cui cercare.|  
|x509FindType|Enumerazione. Uno dei campi certificato in cui cercare.|  
  
## <a name="findvalue-attribute"></a>Attributo findValue  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|String|Il valore dipende dal campo di ricerca specificato dall'attributo X509FindType. Ad esempio, se viene eseguita la ricerca di un'identificazione digitale, il valore deve essere una stringa di numeri esadecimali.|  
  
## <a name="x509findtype-attribute"></a>Attributo x509FindType  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|Enumerazione|I valori includono: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.|  
  
## <a name="storelocation-attribute"></a>Attributo storeLocation  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|Enumerazione|CurrentUser o LocalMachine.|  
  
## <a name="storename-attribute"></a>Attributo storeName  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|Enumerazione|I valori includono: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople e TrustedPublisher.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|Rappresenta una raccolta di certificati X.509 forniti da un servizio token di sicurezza (STS, Security Token Service) per la convalida dei token di sicurezza.|  
  
## <a name="remarks"></a>Note  
 L'emissione di un token di autenticazione prevede tre fasi. Nella prima fase, un client sta tentando di accedere a un servizio viene reindirizzato a un *secure token service*. Nella seconda fase, il servizio token di sicurezza autentica il client e quindi rilascia a quest'ultimo un token, in genere un token SAML (Security Assertions Markup Language), che il client restituisce in seguito al servizio. Nella terza fase, il servizio ricerca nel token appena ricevuto i dati da usare per autenticare il token stesso e, pertanto, il client. Affinché il token venga autenticato è necessario che il servizio riconosca il certificato usato dal servizio token di sicurezza.  
  
 Il [ \<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) elemento è il repository per i certificati di tale servizio token di sicurezza. Per aggiungere i certificati, usare il [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md). Inserire un [ \<aggiungere > elemento \<knownCertificates > elemento](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) per ogni certificato, come illustrato nell'esempio seguente.  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 Per impostazione predefinita, i certificati devono essere ottenuti da un servizio token di sicurezza. Questi certificati "riconosciuti" garantiscono che solo i client autorizzati siano in grado di accedere a un determinato servizio.  
  
 Per le condizioni necessarie per un client da autenticare presso un servizio federato, nonché ulteriori informazioni sull'utilizzo di questo elemento di configurazione, vedere [procedura: configurare le credenziali in un servizio federativo](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md). Per ulteriori informazioni sugli scenari federati, vedere [federazione e i token emessi](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene aggiunto il certificato al repository per i certificati STS.  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <serviceCredentials>  
   <issuedTokenAuthentication>  
    <knownCertificates>  
     <add findValue="www.contoso.com" storeLocation="LocalMachine"   
           storeName="CertificateAuthority"  
           x509FindType="FindByIssuerName" />  
     </knownCertificates>  
    </issuedTokenAuthentication>  
   </serviceCredentials>  
  </behavior>  
 </serviceBehaviors>  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [\<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)  
 [Utilizzo dei certificati](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Federazione e token emessi](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [Procedura: configurare le credenziali in un servizio federativo](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Protezione di servizi e client](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
