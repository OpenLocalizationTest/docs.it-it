---
title: Stili e modelli di RepeatButton
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4895757e909d5e15fd6540b19e1eeec414e1f4e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="repeatbutton-syles-and-templates"></a>Stili e modelli di RepeatButton
In questo argomento vengono descritti gli stili e modelli per il <xref:System.Windows.Controls.Primitives.RepeatButton> controllo. È possibile modificare il valore predefinito <xref:System.Windows.Controls.ControlTemplate> per fornire al controllo un aspetto univoco. Per altre informazioni, vedere [Personalizzazione dell'aspetto di un controllo esistente mediante la creazione di un oggetto ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="repeatbutton-parts"></a>Parti di RepeatButton  
 Il <xref:System.Windows.Controls.Primitives.RepeatButton> controllo non dispone di parti denominate.  
  
## <a name="repeatbutton-states"></a>Stati di RepeatButton  
 Nella tabella seguente sono elencati gli stati visivi per la <xref:System.Windows.Controls.Primitives.RepeatButton> controllo.  
  
|Nome VisualState|Nome VisualStateGroup|Descrizione|  
|-|-|-|  
|Normale|CommonStates|Lo stato predefinito.|  
|MouseOver|CommonStates|Il puntatore del mouse è posizionato sul controllo.|  
|Premuto|CommonStates|Il controllo è premuto.|  
|Disabilitato|CommonStates|Il controllo è disabilitato.|  
|Con stato attivo|FocusStates|Il controllo ha lo stato attivo.|  
|Con stato non attivo|FocusStates|Il controllo non ha lo stato attivo.|  
|Valido|ValidationStates|Il controllo Usa il <xref:System.Windows.Controls.Validation> classe e <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `false`.|  
|InvalidFocused|ValidationStates|Il <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `true` ha il controllo ha lo stato attivo.|  
|InvalidUnfocused|ValidationStates|Il <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> proprietà associata è `true` ha il controllo non è attivo.|  
  
## <a name="repeatbutton-controltemplate-example"></a>Esempio di ControlTemplate RepeatButton  
 Nell'esempio seguente viene illustrato come definire un <xref:System.Windows.Controls.ControlTemplate> per il <xref:System.Windows.Controls.Primitives.RepeatButton> controllo.  
  
 [!code-xaml[ControlTemplateExamples#RepeatButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]  
  
 L'esempio precedente usa una o più delle seguenti risorse.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Per l'esempio completo, vedere [Esempio di applicazione di stili con ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Stili e modelli di Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Personalizzazione dei controlli](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Applicazione di stili e modelli](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Personalizzazione dell'aspetto di un controllo esistente mediante la creazione di un oggetto ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
