---
title: Partizionamento dei dati (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32b95887e05767513dd818743dd1726149503b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-c"></a>Partizionamento dei dati (C#)
Il partizionamento in LINQ è l'operazione di divisione di una sequenza di input in due sezioni senza ridisposizione degli elementi e la successiva restituzione di una delle sezioni.  
  
 La figura seguente illustra i risultati di tre diverse operazioni di partizionamento in una sequenza di caratteri. La prima operazione restituisce i primi tre elementi nella sequenza. La seconda operazione ignora i primi tre elementi e restituisce gli elementi rimanenti. La terza operazione ignora i primi due elementi nella sequenza e restituisce i tre elementi successivi.  
  
 ![Operazioni di partizionamento LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Nella sezione seguente sono elencati i metodi degli operatori di query standard che eseguono la partizione delle sequenze.  
  
## <a name="operators"></a>Operatori  
  
|Nome dell'operatore|Descrizione|Sintassi di espressione della query C#|Altre informazioni|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|Ignora gli elementi fino a una posizione specificata in una sequenza.|Non applicabile.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Ignora gli elementi in base a una funzione di predicato fino a quando un elemento non soddisfa la condizione.|Non applicabile.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Accetta gli elementi fino a una posizione specificata in una sequenza.|Non applicabile.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Accetta gli elementi in base a una funzione di predicato fino a quando un elemento non soddisfa la condizione.|Non applicabile.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Linq>  
 [Cenni preliminari sugli operatori di query standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
