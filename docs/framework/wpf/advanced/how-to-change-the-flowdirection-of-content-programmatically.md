---
title: "Procedura: Cambiare la proprietà FlowDirection del contenuto a livello di codice"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca4c94fe073fd618ca79d08812c42550594f445d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Procedura: Cambiare la proprietà FlowDirection del contenuto a livello di codice
In questo esempio viene illustrato come modificare a livello di codice il <xref:System.Windows.FrameworkElement.FlowDirection%2A> proprietà di un <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Esempio  
 Due <xref:System.Windows.Controls.Button> vengono creati gli elementi, ognuno dei quali rappresenta uno dei valori possibili di <xref:System.Windows.FlowDirection>. Quando un pulsante, il valore della proprietà associata viene applicato al contenuto di un <xref:System.Windows.Controls.FlowDocumentReader> denominato `tf1`.  Il valore della proprietà viene anche scritto per una <xref:System.Windows.Controls.TextBlock> denominato `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Esempio  
 Gli eventi associati ai clic sui pulsanti definiti in precedenza vengono gestiti un [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] file code-behind.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
