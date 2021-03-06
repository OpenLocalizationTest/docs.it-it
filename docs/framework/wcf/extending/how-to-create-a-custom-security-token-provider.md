---
title: 'Procedura: creare un provider di token di sicurezza personalizzati'
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
helpviewer_keywords: security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0bf616b1af46c62166b0430c1b67b3a97f0613ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-security-token-provider"></a>Procedura: creare un provider di token di sicurezza personalizzati
In questo argomento viene illustrato come creare nuovi tipi di token con un provider di token di sicurezza personalizzati e come integrare il provider con un gestore di token di sicurezza personalizzati.  
  
> [!NOTE]
>  Creare un provider di token personalizzati se i token forniti dal sistema, presenti nello spazio dei nomi <xref:System.IdentityModel.Tokens>, non corrispondono ai propri requisiti.  
  
 Il provider di token di sicurezza crea una rappresentazione dei token di sicurezza in base alle informazioni presenti nelle credenziali del client o del servizio. Per usare il provider di token di sicurezza personalizzati nella protezione [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], è necessario creare credenziali personalizzate e implementazioni del gestore dei token di sicurezza.  
  
 Per ulteriori informazioni sulle credenziali personalizzate e gestore del token di sicurezza, vedere il [procedura dettagliata: creazione di Client personalizzato e credenziali del servizio](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Per ulteriori informazioni sulle credenziali, token manager, provider e autenticatore classi di protezione, vedere il [architettura di sicurezza](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f).  
  
### <a name="to-create-a-custom-security-token-provider"></a>Per creare un provider di token di sicurezza personalizzati  
  
1.  Definire una nuova classe derivata dalla classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider>.  
  
2.  Implementare il metodo <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29>. Il metodo è responsabile della creazione e della restituzione di un'istanza del token di sicurezza. Nell'esempio seguente viene creata una classe denominata `MySecurityTokenProvider` ed eseguito l'override del metodo <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29>, per restituire un'istanza della classe <xref:System.IdentityModel.Tokens.X509SecurityToken>. Il costruttore della classe richiede un'istanza della classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>Per integrare un provider di token di sicurezza personalizzati con un gestore di token di sicurezza personalizzati  
  
1.  Definire una nuova classe derivata dalla classe <xref:System.IdentityModel.Selectors.SecurityTokenManager>. L'esempio seguente deriva dalla classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>, che deriva dalla classe <xref:System.IdentityModel.Selectors.SecurityTokenManager>.  
  
2.  Eseguire l'override del metodo <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29>, se non lo si è già fatto.  
  
     Il metodo <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> è responsabile della restituzione di un'istanza della classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider> adatta al parametro <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> passato al metodo dal framework di sicurezza [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Modificare il metodo per restituire l'implementazione del provider di token di sicurezza personalizzati (creato nella procedura precedente), quando il metodo viene chiamato con un parametro del token di sicurezza appropriato. Per ulteriori informazioni sul gestore di token di sicurezza, vedere il [procedura dettagliata: creazione di Client personalizzato e credenziali del servizio](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
3.  Aggiungere logica personalizzata al metodo, per consentire la restituzione del provider di token di sicurezza personalizzati in base al parametro <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>. Nell'esempio seguente viene restituito il provider di token di sicurezza personalizzati, se i requisiti dei token vengono soddisfatti. I requisiti includono un token di sicurezza X.509 e la direzione dei messaggi (è necessario che il token venga usato per l'output dei messaggi). Per tutti gli altri casi, il codice chiama la classe di base per mantenere il comportamento fornito dal sistema per gli altri requisiti dei token di sicurezza.  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata un'implementazione completa di <xref:System.IdentityModel.Selectors.SecurityTokenProvider>, insieme a un'implementazione di <xref:System.IdentityModel.Selectors.SecurityTokenManager> corrispondente.  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [Procedura dettagliata: Creazione di Client personalizzate e le credenziali del servizio](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Procedura: creare un autenticatore del Token di sicurezza personalizzato](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Architettura di sicurezza](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
