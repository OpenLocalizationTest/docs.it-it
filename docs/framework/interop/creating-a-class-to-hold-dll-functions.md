---
title: Creazione di una classe che contenga le funzioni di DLL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3c3542e46168f5903ff0425740a29f16253733
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-class-to-hold-dll-functions"></a>Creazione di una classe che contenga le funzioni di DLL
Il wrapping di una funzione di DLL frequentemente usata in una classe gestita è un modo efficace per incapsulare la funzionalità della piattaforma. Anche se non è obbligatorio in tutti i casi, è preferibile fornire un wrapper di classe, perché la definizione delle funzioni di DLL è un'attività complessa e soggetta a errori. In caso di programmazione in C# o in Visual Basic, è necessario dichiarare le funzioni di DLL in una classe o in un modulo Visual Basic.  
  
 All'interno di una classe si definisce un metodo statico per ogni funzione di DLL che si vuole chiamare. La definizione può includere informazioni aggiuntive, come il set di caratteri o la convenzione di chiamata usata per passare gli argomenti del metodo. Se si omettono queste informazioni, verranno usate le impostazioni predefinite. Per un elenco completo delle opzioni di dichiarazione e delle relative impostazioni predefinite, vedere [Creazione di prototipi nel codice gestito](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
 Una volta effettuato il wrapping, sarà possibile chiamare i metodi della funzione così come si chiamano i metodi di qualsiasi altra funzione statica. Con platform invoke, la funzione esportata sottostante viene gestita automaticamente.  
  
 Quando si progetta una classe gestita che supporti platform invoke, è necessario tenere in considerazione le relazioni tra le classi e le funzioni di DLL. Ad esempio, è possibile eseguire queste operazioni:  
  
-   Dichiarare funzioni di DLL in una classe esistente.  
  
-   Creare una classe distinta per ciascuna funzione di DLL, mantenendo le funzioni isolate e facilmente rintracciabili.  
  
-   Creare una sola classe per un insieme di funzioni di DLL correlate, al fine di formare raggruppamenti logici e ridurre l'overhead.  
  
 È possibile assegnare alla classe e ai relativi metodi i nomi che si preferiscono. Per alcuni esempi che mostrano come costruire dichiarazioni basate su .NET da usare con platform invoke, vedere , vedere [Marshalling dei dati con platform invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di funzioni di DLL non gestite](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [Identificazione delle funzioni nelle DLL](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [Creazione di prototipi nel codice gestito](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Chiamata a una funzione di DLL](../../../docs/framework/interop/calling-a-dll-function.md)
