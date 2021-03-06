---
title: Interfacce di hosting CLR aggiunte in .NET Framework 4 e 4.5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 65d80734bfbe16c8b5052f8de1e4c6280b663707
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Interfacce di hosting CLR aggiunte in .NET Framework 4 e 4.5
Questa sezione vengono descritte le interfacce non gestite host consente di integrare common language runtime (CLR) nei [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]e versioni successive nelle relative applicazioni. Queste interfacce forniscono metodi per un host configurare e caricare il runtime in un processo.  
  
 A partire dal [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], hosting tutte le interfacce hanno le caratteristiche seguenti:  
  
-   Utilizzano la gestione della durata (`AddRef` e `Release`), incapsulamento (contesto implicito) e `QueryInterface` da COM.  
  
-   Non utilizzano i tipi COM, ad esempio `BSTR`, `SAFEARRAY`, o `VARIANT`.  
  
-   Non sono presenti modelli di apartment, aggregazione o attivazione del Registro di sistema che utilizzano il [funzione CoCreateInstance](http://go.microsoft.com/fwlink/?LinkId=142894).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [ICLRAppDomainResourceMonitor (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Fornisce metodi che controllano un dominio di applicazione e CPU.  
  
 [ICLRDomainManager (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Consente all'host specificare la gestione del dominio applicazione che verrà utilizzata per inizializzare il dominio applicazione predefinito e per specificare le proprietà di inizializzazione.  
  
 [ICLRGCManager2 (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Fornisce il [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodo, che consente a un host impostare le dimensioni del segmento di garbage collection e la dimensione massima della generazione del sistema di garbage collection 0 su valori minori `DWORD`.  
  
 [ICLRMetaHost (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 Fornisce metodi che restituiscono una versione specifica di CLR, elencano tutti i runtime installati, l'elenco di tutti i runtime in-process, restituiscono l'interfaccia di attivazione e individuano la versione CLR utilizzata per compilare un assembly.  
  
 [ICLRMetaHostPolicy (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Fornisce il [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodo che fornisce un'interfaccia CLR in base ai criteri, assembly gestito, versione e file di configurazione.  
  
 [ICLRRuntimeInfo (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Fornisce metodi che restituiscono informazioni su una specifica del runtime, compresi versione, directory e stato di caricamento.  
  
 [ICLRStrongName (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Fornisce una base funzioni statiche globali per la firma degli assembly con nomi sicuri. Tutti i [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) restituiscono valori HRESULT COM standard.  
  
 [ICLRStrongName2 (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Fornisce la possibilità di creare nomi sicuri tramite il gruppo di SHA-2 degli algoritmi di Hash di protezione (SHA-256, SHA-384 e SHA-512).  
  
 [ICLRTask2 (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Fornisce tutte le funzionalità del [ICLRTask (interfaccia)](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); inoltre, fornisce metodi che consentono l'interruzione di thread per ritardare il thread corrente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Interfacce di Hosting CLR deprecate e coclassi](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Descrive le interfacce di hosting fornite con .NET Framework versioni 1.0 e 1.1.  
  
 [Interfacce di Hosting CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 Descrive le interfacce di hosting fornite con le versioni di .NET Framework 2.0, 3.0 e 3.5.  
  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 Viene introdotto l'hosting di .NET Framework.
