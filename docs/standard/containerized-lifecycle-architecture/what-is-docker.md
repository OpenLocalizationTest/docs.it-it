---
title: "Che cos'è Docker?"
description: Ciclo di vita dell'applicazione nei contenitori Docker con strumenti e piattaforma Microsoft
keywords: Docker, microservizi, ASP.NET, contenitore
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 7b429f84f7714454d49be1cfa4f450d99fc47f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="what-is-docker"></a>Che cos'è Docker?

[Docker](https://www.docker.com/) è un [progetto open source](https://github.com/docker/docker) per automatizzare la distribuzione di applicazioni come portabile, autosufficiente contenitori che è possibile eseguire nel cloud o locale (vedere Figura 1 - 2). Docker è anche un [società](https://www.docker.com/) che Alza di livello e sviluppa questa tecnologia, l'utilizzo in collaborazione con fornitori di Windows, inclusi Microsoft di cloud, Linux e.

![](./media/image2.png)

Figura 1-2: Docker consente di distribuire contenitori di tutti i livelli del cloud ibrido

Contenitori di docker immagine è possono eseguire in modo nativo in Linux e Windows. Tuttavia, le immagini di Windows è possono eseguire solo negli host Windows e le immagini Linux può essere eseguito solo gli host Linux, vale a dire un server host o una macchina virtuale.

Gli sviluppatori possono utilizzare gli ambienti di sviluppo per Windows, Linux o Mac OS. Nel computer di sviluppo, lo sviluppatore viene eseguito un host Docker in cui Docker vengono distribuite le immagini, tra cui l'app e le relative dipendenze. Gli sviluppatori che lavorano nel Mac, Linux o utilizzano un host Docker basati su Linux, e possono creare immagini solo per i contenitori di Linux. (Sviluppatori che lavorano nel Mac, è possono modificare il codice o eseguire l'interfaccia della riga di comando di Docker \[CLI\] da macOS, ma in questo modo, i contenitori non vengono eseguiti direttamente in macOS.) Gli sviluppatori che lavorano in Windows è possono creare immagini per i contenitori di Windows o Linux.

Per ospitare i contenitori in ambienti di sviluppo e gli strumenti di sviluppo aggiuntive, viene fornito Docker [Docker Community Edition (CE)](https://www.docker.com/community-edition) per Windows o per macOS. Questi prodotti installano la macchina virtuale necessaria (host Docker) per ospitare i contenitori. Docker rende inoltre disponibili [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), che è progettato per lo sviluppo enterprise e viene usato dai team IT che compilano, spedizione ed eseguire applicazioni business-critical di grandi dimensioni nell'ambiente di produzione.

Per eseguire [contenitori di Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), sono disponibili due tipi di runtime:

-   **Contenitore di Windows Server** questo runtime fornisce isolamento dell'applicazione attraverso una tecnologia di isolamento dei processi e dello spazio dei nomi. Un contenitore di Windows Server condivide un kernel con l'host contenitore e tutti i contenitori in esecuzione nell'host.

-   **Contenitore di Hyper-V** espande l'isolamento fornito dai contenitori di Windows Server eseguendo ciascun contenitore in una macchina virtuale altamente ottimizzata. In questa configurazione il kernel dell'host contenitore non viene condiviso con i contenitori di Hyper-V, che fornisce un migliore isolamento.

Le immagini per questi contenitori vengono create nello stesso modo e funzionano allo stesso. La differenza consiste nella creazione del contenitore dall'immagine, l'esecuzione di un contenitore di Hyper-V richiede un parametro aggiuntivo. Per informazioni dettagliate, vedere [contenitori di Hyper-V](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-vms"></a>Confronto tra contenitori di Docker con le macchine virtuali

Figura 1-3 viene illustrato un confronto tra le macchine virtuali e Docker contenitori.

Poiché i contenitori richiedono molto meno risorse (ad esempio, non richiedono un sistema operativo completo), sono facili da distribuire e avvio veloce. Questo rende possibile avere maggiore densità, vale a dire che è possibile eseguire più servizi nella stessa unità di hardware, riducendo i costi.

Come effetto collaterale dell'esecuzione di sullo stesso kernel, meno isolamento rispetto a macchine virtuali.

L'obiettivo principale di un'immagine è che rende l'ambiente (dipendenze) uguali tra le diverse distribuzioni. Ciò significa che è possibile eseguire il debug nel computer e quindi distribuirla in un altro computer con lo stesso ambiente garantito.

Un'immagine contenitore è un modo per un'app o un servizio del pacchetto e distribuirlo in modo affidabile e riproducibile. In questo senso, Docker non solo una tecnologia, è anche una filosofia e un processo.

Quando si usa Docker, è Impossibile ascoltare gli sviluppatori ad esempio, "Funziona nel computer, perché non in produzione?" È possibile semplicemente ad esempio, "Viene eseguito in Docker," perché l'applicazione del pacchetto Docker può essere eseguito in qualsiasi ambiente supportato da Docker, e verrà eseguito il modo in cui che si intendeva in tutte le destinazioni di distribuzione (sviluppo, QA, gestione temporanea, produzione, ecc.).

![](./media/image3.png)

Figura 1-3: confronto di macchine virtuali tradizionali ai contenitori di Docker


>[!div class="step-by-step"]
[Precedente] [Avanti] (docker terminology.md) (index.md)
