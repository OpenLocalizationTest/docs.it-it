---
title: 'Procedura: usare ChannelFactory'
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
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37ad5181ad140c3ef3ea8ba5b3774fd44310dca7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-channelfactory"></a>Procedura: usare ChannelFactory
La classe generica <xref:System.ServiceModel.ChannelFactory%601> viene usata in scenari avanzati che richiedono la creazione di una channel factory utilizzabile per creare più di un canale.  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>Per creare e usare la classe ChannelFactory  
  
1.  Creare ed eseguire un servizio [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][La progettazione e implementazione di servizi](../../../../docs/framework/wcf/designing-and-implementing-services.md), [configurazione dei servizi](../../../../docs/framework/wcf/configuring-services.md), e [servizi di Hosting](../../../../docs/framework/wcf/hosting-services.md).  
  
2.  Utilizzare il [strumento ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) per generare il contratto (interfaccia) per il client.  
  
3.  Nel codice client, usare la classe <xref:System.ServiceModel.ChannelFactory%601> per creare più listener endpoint.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
