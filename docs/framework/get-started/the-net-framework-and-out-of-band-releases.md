---
title: .NET Framework e rilascio fuori programma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1785c222238a58893edf71352839b40ea8db29f7
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2017
---
# <a name="the-net-framework-and-out-of-band-releases"></a>.NET Framework e rilascio fuori programma
L'evoluzione di .NET Framework includerà diverse piattaforme, tra cui app Windows Phone e Windows Store, nonché app desktop e Web tradizionali, e consentirà di ottimizzare il riutilizzo del codice. Oltre ai regolari rilasci di .NET Framework, verranno rese disponibili nuove funzionalità fuori banda per migliorare lo sviluppo per più piattaforme o introdurre alcune novità. In questo argomento verrà illustrato l'orientamento futuro di .NET Framework e dei rilasci fuori banda.  
  
## <a name="advantages-of-oob-releases"></a>Vantaggi dei rilasci fuori banda  
 La distribuzione di nuovi componenti o aggiornamenti ai componenti fuori banda consente a Microsoft di fornire aggiornamenti più frequenti a .NET Framework. Inoltre, sarà possibile raccogliere e rispondere ai feedback dei clienti più rapidamente.  
  
 Se si usa una funzionalità fuori banda nell'app, gli utenti non devono installare la versione più recente di .NET Framework per eseguirla, poiché gli assembly fuori banda vengono distribuiti con il pacchetto dell'app.  
  
## <a name="how-oob-packages-are-distributed"></a>Modalità di distribuzione dei pacchetti fuori banda  
I rilasci fuori banda per i componenti di base common language runtime (CLR) vengono forniti tramite il [NuGet](https://www.nuget.org/), che è una gestione pacchetti per .NET. NuGet consente di cercare e aggiungere facilmente librerie ai progetti .NET Framework da Esplora soluzioni in Visual Studio. NuGet è incluso in tutte le edizioni di Visual Studio a partire da Visual Studio 2012. Per verificare se NuGet è installato, individuare **Gestione pacchetti di librerie** dal menu **Strumenti** di Visual Studio. Se non è installato:  
  
1.  Nella barra dei menu di Visual Studio scegliere **Strumenti**, **Estensioni e aggiornamenti** (in Visual Studio 2010, scegliere **Gestione estensioni**).  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Scegliere **Online** e **Gestione pacchetti NuGet**, quindi fare clic su **Scarica**.  
  
3.  Al termine del download, riavviare Visual Studio.  
  
 Per istruzioni di installazione dettagliate, vedere [Installazione di NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) nel sito Web NuGet Docs. Per altre informazioni su NuGet, vedere la [documentazione di NuGet](http://docs.nuget.org/).  
  
## <a name="using-a-nuget-oob-package"></a>Utilizzo di un pacchetto NuGet fuori banda  
 Dopo aver installato NuGet, sarà possibile cercare e aggiungere riferimenti ai pacchetti NuGet utilizzando Esplora soluzioni di Visual Studio:  
  
1.  Aprire il menu di scelta rapida per il progetto in Visual Studio, quindi scegliere **Gestisci pacchetti NuGet**. Questa opzione è disponibile anche nel menu **Progetto**.  
  
2.  Nel riquadro sinistro scegliere **Online**.  
  
3.  Se si desidera usare i pacchetti della versione provvisoria, nell'elenco a discesa del riquadro centrale scegliere **Includi versione provvisoria** anziché **Solo stabile**.  
  
4.  Nel riquadro di destra usare la casella **Cerca** per individuare il pacchetto che si desidera usare. Alcuni pacchetti Microsoft sono identificati dal logo Microsoft .NET Framework e in tutti Microsoft viene identificato come editore.  
  
 ![Gestione pacchetti NuGet](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")  
  
 Come accennato in precedenza, quando si distribuisce un'app che utilizza un pacchetto fuori banda, all'interno di quest'ultimo verranno forniti gli assembly fuori banda.  
  
## <a name="types-of-oob-releases"></a>Tipi di rilasci fuori banda  
 In genere, un pacchetto fuori banda contiene una o più versioni preliminari e una versione stabile. La licenza fornita con una versione preliminare non consente in genere la ridistribuzione, ma permette di provare un pacchetto e fornire feedback. Il feedback è incorporato in qualsiasi aggiornamento apportato al pacchetto. Una versione finale viene distribuita come pacchetto stabile con NuGet e include una licenza che consente di ridistribuire il pacchetto NuGet con l'app. I pacchetti stabili sono supportati da Microsoft. Microsoft fornisce il supporto IntelliSense insieme ad altri tipi di documentazione come i post di blog e le risposte dei forum per tutti i pacchetti. Inoltre, il codice sorgente può essere disponibile solo con alcuni pacchetti. Per ricevere annunci relativi ai pacchetti nuovi e aggiornati, è possibile sottoscrivere il [blog di .NET Framework](http://blogs.msdn.com/b/dotnet/).  
  
 Per trovare sia i pacchetti provvisori che quelli stabili, scegliere **Includi versione provvisoria** in Gestisci pacchetti NuGet.  
  
 Se si vuole ricevere una notifica del rilascio di pacchetti stabili, sottoscrivere il [feed di .NET Framework](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../../docs/framework/get-started/index.md)
