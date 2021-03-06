---
title: "Progettazione e implementazione di attività personalizzate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 944f8d7c015d2522ae4fb8f0805ca6a40d494a75
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="designing-and-implementing-custom-activities"></a>Progettazione e implementazione di attività personalizzate
Le attività personalizzate in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] vengono create assemblando le attività fornite dal sistema nelle attività composte o creando nuovi tipi che derivano dall'oggetto <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> o <xref:System.Activities.NativeActivity>. Contenuto della sezione viene illustrato come creare attività personalizzate con uno dei metodi.  
  
> [!IMPORTANT]
>  Le attività personalizzate vengono visualizzate per impostazione predefinita nella finestra di progettazione del flusso di lavoro come un semplice rettangolo con il nome dell'attività. Per fornire una rappresentazione visiva personalizzata dell'attività nella finestra di progettazione del flusso di lavoro è inoltre necessario creare una finestra di progettazione personalizzata. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Tramite gli ActivityDesigner personalizzati e modelli](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Opzioni di creazione di attività](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 Viene illustrata la creazione di stili disponibili in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].  
  
 [Uso di un'attività personalizzata](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 Viene descritto come aggiungere un'attività personalizzata a un progetto flusso di lavoro.  
  
  [Creazione di attività asincrone](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 Viene illustrato come creare attività asincrone.  
  
 [Configurazione della convalida di attività](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 Viene illustrato come usare la convalida delle attività per identificare e segnalare errori nella configurazione di un'attività prima della relativa esecuzione.  
  
 [Creazione di un'attività in fase di esecuzione](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 Viene illustrato come creare attività in fase di esecuzione usando <xref:System.Activities.DynamicActivity>.  
  
 [Proprietà di esecuzione del flusso di lavoro](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 Viene illustrato come usare le proprietà di esecuzione del flusso di lavoro per aggiungere proprietà specifiche del contesto all'ambiente di un'attività.  
  
 [Uso di delegati di attività](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 Viene illustrato come creare e usare attività che contengono delegati di attività.  
  
 [Localizzazione di attività](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 Viene illustrato come usare la localizzazione di risorse di tipo stringa nelle attività.  
  
 [Uso di estensioni di attività](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 Viene descritto come creare e usare le estensioni di attività.  
  
 [Utilizzo di feed OData da un flusso di lavoro](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 Vengono descritti i diversi metodi per chiamare WCF Data Services da un flusso di lavoro.  
  
 [Ambito e visibilità della definizione di attività](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 Vengono descritte le opzioni e le regole per definire l'ambito dei dati e la visibilità dei membri per le attività.
