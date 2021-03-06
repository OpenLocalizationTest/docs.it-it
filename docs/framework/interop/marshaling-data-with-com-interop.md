---
title: "dati di marshalling con interoperabilità COM"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2def27790a1727bda524b8c14a93f7b78127a569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-com-interop"></a>dati di marshalling con interoperabilità COM
Grazie all'interoperabilità COM, è possibile usare oggetti COM dal codice gestito ed esporre oggetti gestiti a COM. Il supporto per il marshalling dei dati verso e da COM è estensivo e garantisce sempre il comportamento di marshalling corretto.  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] include i seguenti strumenti di interoperabilità COM:  
  
-   [Utilità di importazione della libreria dei tipi (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), che consente di convertire una libreria dei tipi COM in un assembly di interoperabilità, dal quale, con il servizio di marshalling di interoperabilità, vengono generati wrapper per il marshalling dei dati tra memoria gestita e non gestita.  
  
-   [Utilità di esportazione della libreria dei tipi (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), che consente di generare una libreria dei tipi COM da un assembly e un wrapper per l'esecuzione del marshalling durante le chiamate ai metodi.  
  
 Nelle sezioni seguenti collegano ad argomenti che descrivono i processi per la personalizzazione di wrapper di interoperabilità quando è possibile o necessario fornire altre informazioni sui tipi al gestore di marshalling.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
[Procedura: creare wrapper manualmente](how-to-create-wrappers-manually.md)   
Viene descritto come creare manualmente un wrapper COM nel codice sorgente gestito. 
 
 [Procedura: Eseguire la migrazione di codice gestito da DCOM a WCF](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 Viene descritto come eseguire la migrazione di codice gestito DCOM a WCF per la soluzione più sicura.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di dati COM](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)  
 Fornisce i tipi di dati gestiti e non gestiti corrispondenti.  
  
 [Personalizzazione di wrapper COM richiamabili](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)  
 Viene descritto come eseguire in modo esplicito il marshalling di tipi di dati tramite il <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributo in fase di progettazione.  
  
 [Personalizzazione dei Runtime Callable Wrapper](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)  
 Descrive come regolare il comportamento del marshalling dei tipi in un assembly di interoperabilità e come definire manualmente i tipi COM.  
  
 [Interoperabilità COM avanzata](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)  
 Contiene collegamenti per accedere ad altre informazioni sull'inclusione di componenti COM nell'applicazione .NET Framework.  
  
 [Riepilogo della conversione da assembly a libreria dei tipi](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)  
 Descrive il processo di conversione eseguito in caso di esportazione da assembly a libreria dei tipi.  
  
 [Riepilogo della conversione da libreria dei tipi ad assembly](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)  
 Descrive il processo di conversione eseguito in caso di importazione da libreria dei tipi ad assembly.  
  
 [Interoperabilità tramite tipi generici](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)  
 Descrive le azioni supportate quando si usano tipi generici per l'interoperabilità COM.
