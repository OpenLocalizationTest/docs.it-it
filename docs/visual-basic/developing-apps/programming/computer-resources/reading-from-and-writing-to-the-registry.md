---
title: Lettura e scrittura nel Registro di sistema (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db564b428d585829b220674271f4636bfcc68562
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2017
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Lettura e scrittura nel Registro di sistema (Visual Basic)
Questo argomento descrive attività e concetti correlati al Registro di sistema.  
  
 Durante la programmazione in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] è possibile scegliere di accedere al Registro di sistema usando le funzioni di [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] o le classi del Registro di sistema di .NET Framework. Il Registro di sistema contiene informazioni provenienti dal sistema operativo nonché informazioni provenienti dalle applicazioni presenti nel computer. L'uso del Registro di sistema può compromettere la sicurezza poiché consente l'accesso inappropriato alle risorse di sistema o alle informazioni protette.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Procedura: Creare una chiave del Registro di sistema e impostarne il valore](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Viene descritto come usare i metodi `CreateSubKey` e `SetValue` dell'oggetto `My.Computer.Registry` per creare una chiave del Registro di sistema e impostarne il valore.  
  
 [Procedura: Leggere un valore da una chiave del Registro di sistema](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Viene descritto come usare il metodo `GetValue` dell'oggetto `My.Computer.Registry` per leggere un valore da una chiave del Registro di sistema.  
  
 [Procedura: Eliminare una chiave del Registro di sistema](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Viene descritto come usare il metodo `DeleteSubKey` della proprietà `My.Computer.Registry.CurrentUser` per eliminare una chiave del Registro di sistema.  
  
 [Lettura e scrittura nel Registro di sistema mediante lo spazio dei nomi Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Viene descritto come usare le classi `Registry` e `RegistryKey` di [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] per accedere al Registro di sistema.  
  
 [Sicurezza e Registro di sistema](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Vengono illustrati i problemi di sicurezza che riguardano il Registro di sistema.  
  
## <a name="related-sections"></a>Sezioni correlate  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Vengono elencati e illustrati i membri dell'oggetto `My.Computer.Registry`.  
  
 <xref:Microsoft.Win32.Registry>  
 Viene presentata una panoramica della classe `Registry`, oltre a collegamenti a singoli membri e chiavi.
