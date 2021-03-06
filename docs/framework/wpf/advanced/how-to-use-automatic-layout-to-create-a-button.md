---
title: 'Procedura: Usare un layout automatico per creare un pulsante'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d55dc1330c21e7eb9f7cfd7f554234dccd6f274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>Procedura: Usare un layout automatico per creare un pulsante
Questo esempio descrive come usare un approccio basato sul layout automatico per la creazione di un pulsante in un'applicazione localizzabile.  
  
 Localizzazione di un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] può richiedere molto tempo. Spesso sono necessari il ridimensionamento e il riposizionamento degli elementi, oltre alla traduzione del testo. In passato ogni lingua che un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] è stato adattato per la regolazione obbligatoria. Ora con le funzionalità di [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] è possibile progettare gli elementi che riducono l'esigenza di modifiche. Viene chiamato l'approccio alla scrittura di applicazioni che possono essere più facilmente ridimensionare e riposizionare `automatic layout`.  
  
 I seguenti due [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] esempi di creano applicazioni che creano un pulsante, uno con testo in lingua inglese e uno con del testo in spagnolo. Il codice è lo stesso ad eccezione del testo. Il pulsante si regola per adattarsi al testo.  
  
## <a name="example"></a>Esempio  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 La figura seguente mostra l'output degli esempi di codice.  
  
 ![Lo stesso pulsante con testo in lingue diverse](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Pulsante a ridimensionamento automatico  
  
## <a name="see-also"></a>Vedere anche  
 [Cenni preliminari sull'utilizzo del layout automatico](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Usare una griglia per il layout automatico](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
