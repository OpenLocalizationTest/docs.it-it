---
title: 'Procedura: impostare l''altezza di una finestra da una pagina'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29de47eceae4b8927f2701ca0bbda2ecc7243919
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>Procedura: impostare l'altezza di una finestra da una pagina
In questo esempio viene illustrato come impostare l'altezza della finestra da un <xref:System.Windows.Controls.Page>.  
  
## <a name="example"></a>Esempio  
 Oggetto <xref:System.Windows.Controls.Page> possibile impostare l'altezza della finestra host impostando <xref:System.Windows.Controls.Page.WindowHeight%2A>. Questa proprietà consente di <xref:System.Windows.Controls.Page> senza che abbiano una conoscenza esplicita del tipo di finestra che lo ospita.  
  
> [!NOTE]
>  Per impostare l'altezza di una finestra utilizzando <xref:System.Windows.Controls.Page.WindowHeight%2A>, <xref:System.Windows.Controls.Page> deve essere il figlio di una finestra.  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
