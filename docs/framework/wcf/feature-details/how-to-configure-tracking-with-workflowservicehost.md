---
title: 'Procedura: configurare il rilevamento con WorkflowServiceHost'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42b5621275b9d27983619d18990e3d8e22c4e9db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Procedura: configurare il rilevamento con WorkflowServiceHost
In questo argomento viene illustrato come configurare il rilevamento di un flusso di lavoro [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] ospitato in <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Viene configurato tramite un file Web.config specificando un comportamento del servizio.  
  
### <a name="configure-tracking-in-configuration"></a>Configurare il rilevamento nella configurazione  
  
1.  Aggiungere <xref:System.Activities.Tracking.EtwTrackingParticipant> usando l'elemento <`behavior`> in un file di configurazione, come indicato nell'esempio seguente.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    >  L'esempio di configurazione precedente usa la configurazione semplificata. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Semplificata la configurazione](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     L'esempio di configurazione precedente aggiunge un elemento <xref:System.Activities.Tracking.EtwTrackingParticipant> e specifica un nome del profilo di rilevamento. I profili di rilevamento vengono creati in un elemento <`trackingProfile`> all'interno di un elemento <`tracking`>. Il profilo di rilevamento contiene query di rilevamento che consentono a un partecipante del rilevamento di eseguire la sottoscrizione agli eventi del flusso di lavoro generati quando lo stato di un'istanza del flusso di lavoro viene modificato al runtime. Nell'esempio seguente viene illustrato come creare un profilo di rilevamento.  
  
    ```xml  
    <system.serviceModel>  
        <tracking>   
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>   
       </tracking>  
    </system.serviceModel>  
    ```  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]i profili di rilevamento, vedere [profili di rilevamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]rilevamento in generale, vedere [flusso di lavoro rilevamento e traccia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Configurare il rilevamento nel codice  
  
1.  Aggiungere l'elemento <xref:System.Activities.Tracking.EtwTrackingParticipant> usando il comportamento <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> nel codice, come illustrato nell'esempio riportato di seguito.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     L'esempio di codice precedente aggiunge un elemento <xref:System.Activities.Tracking.EtwTrackingParticipant> e specifica un nome del profilo di rilevamento. I profili di rilevamento vengono creati in un elemento <`trackingProfile`> all'interno di un elemento <`tracking`> come illustrato nella sezione precedente.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]i profili di rilevamento, vedere [profili di rilevamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]rilevamento in generale, vedere [flusso di lavoro rilevamento e traccia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Per un esempio di configurazione del rilevamento a livello di codice vedere [configurazione del rilevamento per un flusso di lavoro](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione semplificata per i servizi WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [Servizi flusso di lavoro](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Profili di rilevamento](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
