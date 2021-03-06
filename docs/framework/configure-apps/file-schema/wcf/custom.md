---
title: '&lt;personalizzato&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e4b96e1274ad59ae5e63e7935d7408afd069a8c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomgt"></a>&lt;personalizzato&gt;
Specifica le impostazioni di un servizio resolver peer personalizzato.  
  
\<System. ServiceModel >  
\<associazioni >  
\<netPeerBinding >  
\<associazione >  
\<resolver >  
\<personalizzate >  
  
## <a name="syntax"></a>Sintassi  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`address`|URI che specifica l'indirizzo dell'endpoint del nodo peer che ospita il servizio resolver peer personalizzato.|  
|`resolverType`|Stringa che specifica il tipo del servizio resolver peer personalizzato.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<identità >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Specifica l'identità dei resolver peer personalizzati configurati per questo elemento. L'elemento è di tipo <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<intestazioni >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Raccolta di intestazioni di indirizzo usate per i messaggi SOAP gestiti dal resolver peer personalizzato.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<resolver >](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Resolver peer usato per risolvere un ID della rete di peer in un set di indirizzi di nodo peer che rappresenta alcuni nodi appartenenti alla rete.|  
  
## <a name="remarks"></a>Note  
 Questo elemento definisce le impostazioni di base per un servizio resolver peer personalizzato, inclusi l'indirizzo dell'endpoint del peer che ospita il servizio e le impostazioni dell'associazione specifiche. Per ulteriori informazioni sulla creazione di un sistema di risoluzione personalizzato, vedere [aggiunta di un Resolver personalizzato a un'applicazione di PeerChannel](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [Resolver del peer](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [Aggiunta di un Resolver personalizzato a un'applicazione il canale peer](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
