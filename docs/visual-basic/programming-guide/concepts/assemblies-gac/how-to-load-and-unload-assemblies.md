---
title: 'Procedura: caricamento e scaricare gli assembly (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd52a1094dba16c7e1bcba5bface9e13747cd4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Procedura: caricamento e scaricare gli assembly (Visual Basic)
Gli assembly cui il programma fa riferimento verranno caricati automaticamente in fase di compilazione, ma è anche possibile caricare assembly specifici nel dominio dell'applicazione corrente in fase di esecuzione. Per altre informazioni, vedere: [Procedura: Caricare assembly in un dominio dell'applicazione](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Non è possibile scaricare un singolo assembly senza scaricare tutti i domini dell'applicazione che lo contengono. Anche se l'assembly esce dall'ambito, il file effettivo dell'assembly rimane caricato finché non vengono scaricati tutti i domini dell'applicazione che lo contengono.  
  
 Se si vogliono scaricare alcuni assembly ma non altri, è consigliabile creare un nuovo dominio dell'applicazione, eseguire il codice all'interno del dominio, e quindi scaricare tale dominio dell'applicazione. Per altre informazioni, vedere [Procedura: Scaricare un dominio dell'applicazione](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Per caricare un assembly in un dominio dell'applicazione  
  
1.  Usare uno dei numerosi metodi di caricamento contenuti nelle classi <xref:System.AppDomain> e <xref:System.Reflection>. Per altre informazioni, vedere: [Procedura: Caricare assembly in un dominio dell'applicazione](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Per scaricare un dominio dell'applicazione  
  
1.  Non è possibile scaricare un singolo assembly senza scaricare tutti i domini dell'applicazione che lo contengono. Per scaricare i domini dell'applicazione, usare il metodo `Unload` da <xref:System.AppDomain>. Per altre informazioni, vedere [Procedura: Scaricare un dominio dell'applicazione](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni di base sulla programmazione](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Assembly e Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Procedura: Caricare assembly in un dominio dell'applicazione](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
