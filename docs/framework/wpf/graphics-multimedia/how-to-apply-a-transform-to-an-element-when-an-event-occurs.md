---
title: 'Procedura: applicare una trasformazione a un elemento quando si verifica un evento'
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
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 58ef8c008eea4c10228ebb10ceadb5806dfbc0f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Procedura: applicare una trasformazione a un elemento quando si verifica un evento
In questo esempio viene illustrato come applicare un <xref:System.Windows.Media.ScaleTransform> quando si verifica un evento. Il concetto illustrato è identico a quello usato per applicare altri tipi di trasformazioni. Per ulteriori informazioni sui tipi di trasformazioni disponibili, vedere il <xref:System.Windows.Media.Transform> classe o [Trasforma Panoramica](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).  
  
 È possibile applicare una trasformazione a un elemento in uno dei due modi seguenti:  
  
-   Se esegue l'operazione *non* desidera che la trasformazione per influire sul layout, utilizzare il <xref:System.Windows.UIElement.RenderTransform%2A> proprietà dell'elemento.  
  
-   Se si desidera che la trasformazione per influire sul layout, utilizzare il <xref:System.Windows.FrameworkElement.LayoutTransform%2A> proprietà dell'elemento.  
  
 Nell'esempio seguente viene applicato un <xref:System.Windows.Media.ScaleTransform> per il <xref:System.Windows.UIElement.RenderTransform%2A> proprietà di un pulsante. Quando il mouse viene spostato su di esso, il <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> le proprietà del <xref:System.Windows.Media.ScaleTransform> sono impostate su `2`, causando il pulsante di aumento delle dimensioni. Quando il mouse viene spostato dal pulsante, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> e <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> sono impostate su `1`, causando il pulsante per tornare alla dimensione originale.  
  
## <a name="example"></a>Esempio  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Cenni preliminari sulle trasformazioni](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Procedure relative](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Cenni preliminari sugli eventi indirizzati](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
