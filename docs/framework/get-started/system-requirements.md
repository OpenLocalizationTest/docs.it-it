---
title: Requisiti di sistema di .NET Framework
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b08bd7b78a8606f61c266da51f4079f0b5f4aac6
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2017
---
# <a name="net-framework-system-requirements"></a>Requisiti di sistema di .NET Framework

Le tabelle in questo argomento forniscono hardware, sistema operativo e i requisiti software per .NET Framework 4.5 e alle versioni intermedie (4.5.1 e 4.5.2), il [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e delle versioni intermedie (4.6.1 e 4.6.2) e il 4.7 di .NET Framework e il relativo punto versione (4.7.1). Gli ambienti di sviluppo che consentono di sviluppare app per .NET Framework dispongono di un set di requisiti separato.

Per informazioni su download e collegamenti, vedere [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md) (Installazione di .NET Framework per sviluppatori).

Per informazioni sul ciclo di vita del supporto delle versioni di .NET Framework, vedere [Ciclo di vita del supporto Microsoft](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO).

## <a name="hardware-requirements"></a>Requisiti hardware

|                          |        |
| ------------------------ | ------ |
| **Processore**            | 1 GHz  |
| **RAM**                  | 512 MB |
| **Spazio su disco (minimo)** |        |
| 32 bit                   | 4,5 GB |
| 64 bit                   | 4,5 GB |

## <a name="installation-requirements"></a>Requisiti di installazione

Per l'installazione di .NET Framework è necessario avere privilegi di amministratore. Se non si hanno diritti di amministratore nel computer in cui si vuole installare .NET Framework, contattare l'amministratore di rete.

## <a name="supported-client-operating-systems"></a>Sistemi operativi client supportati

| Sistema operativo | Edizioni supportate | Preinstallato con il sistema operativo | Installabile separatamente |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Aggiornare rientrano creatori di Windows 10 | 32 e 64 bit | .NET framework 4.7.1 | |
| Windows 10 Creators Update | 32 e 64 bit | .NET Framework 4.7 | .NET framework 4.7.1 | 
| Aggiornamento dell'anniversario di Windows 10 | 32 e 64 bit | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|.NET Framework 4.7<br/><br/>.NET framework 4.7.1 |
| Aggiornamento di novembre di Windows 10 | 32 bit e 64 bit | [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] | |
| Windows 10 | 32 bit e 64 bit | [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] | [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32 bit, 64 bit e ARM | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/>.NET framework 4.7.1 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32 bit, 64 bit e ARM | [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] |
| Windows 7 SP1|32 e 64 bit | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/>.NET framework 4.7.1|
| Windows Vista SP2|32 e 64 bit | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |
| Windows XP |32 e 64 bit | -- | .NET Framework 4 |

 **Note:**

- Nei sistemi Windows 7, .NET Framework richiede Windows 7 SP1. Se si ha Windows 7 ma non è ancora stato installato Service Pack 1, è necessario farlo prima di installare .NET Framework.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] è supportato nell'Ambiente preinstallazione di Windows (Windows PE). Non tutte le funzionalità sono supportate in Windows PE.

- .NET Framework 4 supporta inoltre la piattaforma IA64.

- Per tutte le piattaforme, si consiglia di eseguire l'aggiornamento al Service Pack di Windows più recente e di installare gli aggiornamenti critici disponibili nel [sito Web Windows Update](http://go.microsoft.com/fwlink/?LinkId=168461) per garantire la massima compatibilità e sicurezza.

- Nei sistemi operativi a 64 bit, .NET Framework supporta sia WOW64 (elaborazione a 32 bit su un computer a 64 bit) che l'elaborazione nativa a 64 bit.

## <a name="supported-server-operating-systems"></a>Sistemi operativi server supportati

| Sistema operativo | Edizioni supportate | Preinstallato con il sistema operativo | Installabile separatamente |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows Server, versione 1709 | 64 bit | .NET framework 4.7.1 | -- |
| Windows Server 2016 | 64 bit | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] | .NET Framework 4.7<br/><br/> .NET framework 4.7.1 |
| Windows Server 2012 R2 | 64 bit | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/> .NET framework 4.7.1 |
| Windows Server 2012 (64-bit edition) | 64 bit| [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows Server 2008 R2 SP1|64 bit | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET Framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows Server 2008 SP2|32 e 64 bit | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |

 **Note:**

- In [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] è incluso [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], pertanto non è necessario installarlo separatamente. Analogamente, in [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] è incluso [!INCLUDE[net_v451](../../../includes/net-v451-md.md)].

- .NET Framework offre supporto limitato per il ruolo di Server Core con Windows Server 2008 R2 SP1 o versione successiva. Vedere [la funzionalità Server Core .NET](https://msdn.microsoft.com/library/ee391632.aspx) per un elenco di API non supportate.

- .NET Framework non è supportato in Windows Server 2008 R2 per sistemi basati su Itanium.

- .NET Framework non è supportato nel ruolo Server Core in Windows Server 2008 SP2.

- Per tutte le piattaforme, si consiglia di eseguire l'aggiornamento al Service Pack di Windows più recente e installare gli aggiornamenti critici disponibili nel [sito Web Windows Update](http://go.microsoft.com/fwlink/?LinkId=168461) per garantire la massima compatibilità e sicurezza. Su alcuni sistemi operativi potrebbe essere necessaria l'installazione dell'ultimo Windows Service Pack.

- Nei sistemi operativi a 64 bit, .NET Framework supporta sia WOW64 (elaborazione a 32 bit su un computer a 64 bit) che l'elaborazione nativa a 64 bit.

## <a name="see-also"></a>Vedere anche

[Guida all'installazione](../../../docs/framework/install/index.md)   
[Introduzione](../../../docs/framework/get-started/index.md)   
[Risolvere i problemi relativi alle installazioni e alle disinstallazioni bloccate di .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
