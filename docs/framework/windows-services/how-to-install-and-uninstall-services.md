---
title: 'Procedura: installare e disinstallare servizi'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: d52512ef98596e1e3d5f0acb3b1bbc0eebffe867
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-and-uninstall-services"></a>Procedura: installare e disinstallare servizi
Se si sta sviluppando un servizio Windows con .NET Framework, è possibile installare rapidamente l'applicazione di servizio tramite un'utilità della riga di comando denominata InstallUtil.exe. Se uno sviluppatore vuole rilasciare un servizio Windows che gli utenti possono installare e disinstallare, può usare InstallShield. Vedere [la distribuzione di Windows Installer](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Se si vuole disinstallare un servizio dal computer, non seguire i passaggi di questo articolo. In alternativa, individuare il programma o il pacchetto software è installato il servizio e quindi scegliere **Aggiungi/Rimuovi programmi** nel Pannello di controllo per disinstallare tale programma. Si noti che molti servizi sono parte integrante di Windows. Se vengono rimossi, il sistema potrebbe diventare instabile.  
  
 Per usare i passaggi descritti in questo articolo, è necessario prima aggiungere un programma di installazione del servizio al servizio Windows. Vedere [procedura dettagliata: creazione di un'applicazione in Progettazione componenti del servizio](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 I progetti del servizio Windows non possono essere eseguiti direttamente dall'ambiente di sviluppo di Visual Studio premendo F5, perché è necessario installare il servizio prima dell'esecuzione del progetto.  
  
> [!TIP]
>  È possibile avviare **Esplora Server** e verificare che il servizio è stato installato o disinstallato. Per ulteriori informazioni, vedere Procedura: accedere e inizializzare Esplora Server-Esplora Database.  
  
### <a name="to-install-your-service-manually"></a>Per installare il servizio manualmente  
  
1.  Di Windows **avviare** menu o **avviare** scegliere **Visual Studio** , **Visual Studio Tools**, **Developer Prompt dei comandi**.  
  
     Verrà visualizzato un prompt dei comandi di Visual Studio.  
  
2.  Accedere alla directory in cui si trova il file eseguibile compilato del progetto.  
  
3.  Eseguire InstallUtil.exe dal prompt dei comandi con l'eseguibile del progetto come parametro:  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Se si usa il prompt dei comandi di Visual Studio, InstallUtil.exe sarà nel percorso di sistema. In caso contrario, è possibile aggiungerlo al percorso o usare il percorso completo per richiamarlo. Questo strumento viene installato con .NET Framework e il percorso è `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Ad esempio, per la versione a 32 bit di .NET Framework 4 o 4.5.*, se la directory di installazione di Windows è C:\Windows, il percorso è `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. Per la versione a 64 bit di .NET Framework 4 o 4.5. \*, il percorso predefinito è `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Per disinstallare il servizio manualmente  
  
1.  Di Windows **avviare** menu o **avviare** scegliere **Visual Studio**, **Visual Studio Tools**, **Developer Prompt dei comandi**.  
  
     Verrà visualizzato un prompt dei comandi di Visual Studio.  
  
2.  Eseguire InstallUtil.exe dal prompt dei comandi con l'output del progetto come parametro:  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  In alcuni casi, dopo avere eliminato il file eseguibile di un servizio, è possibile che il servizio sia ancora presente nel Registro di sistema. In tal caso, utilizzare il comando [sc delete](http://technet.microsoft.com/library/cc742045.aspx) per rimuovere la voce per il servizio dal Registro di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione alle applicazioni di servizio Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Procedura: creare servizi Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Procedura: aggiungere programmi di installazione all'applicazione di servizio](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Installutil.exe (Strumento Programma di installazione)](../../../docs/framework/tools/installutil-exe-installer-tool.md)
