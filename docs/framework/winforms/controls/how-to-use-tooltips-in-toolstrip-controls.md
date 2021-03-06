---
title: 'Procedura: utilizzare descrizioni comandi nei controlli ToolStrip'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc52dd1b629829564532fd93650737f51e5d7f24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Procedura: utilizzare descrizioni comandi nei controlli ToolStrip
È possibile visualizzare un <xref:System.Windows.Forms.ToolTip> per il <xref:System.Windows.Forms.ToolStrip> controllo impostando il controllo di cui si desidera <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> proprietà `true`.  
  
### <a name="to-display-a-tooltip"></a>Per visualizzare una descrizione  
  
-   Impostare il <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> proprietà del controllo da `true`.  
  
     Il valore predefinito di <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> è `true`e il valore predefinito di <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> è `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Utilizzare la proprietà ToolTipText per il testo della descrizione di un oggetto di ToolStripButton  
  
1.  Impostare il <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> proprietà del pulsante su `true`.  
  
2.  Impostare il <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> proprietà del pulsante su `false`.  
  
     Il `AutoToolTip` proprietà `true` per impostazione predefinita per <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, e <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     Oggetto <xref:System.Windows.Forms.ToolStripButton> utilizza relativo `Text` proprietà per il <xref:System.Windows.Forms.ToolTip> testo per impostazione predefinita. Utilizzare questa procedura per visualizzare il testo personalizzato in un <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Se si imposta <xref:System.Windows.Forms.ToolStripItemDisplayStyle> a <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> o <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, sul pulsante verrà visualizzato alcun testo, ma verrà comunque visualizzata la descrizione comando.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [Panoramica sul controllo ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
