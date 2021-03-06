---
title: 'Procedura: progettare un layout di Windows Form che risponda correttamente alla localizzazione'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3584b1a5751257c558d5e000135478966605f9c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Procedura: progettare un layout di Windows Form che risponda correttamente alla localizzazione
La creazione di form pronti per la localizzazione accelera notevolmente lo sviluppo per i mercati internazionali. È possibile usare il controllo <xref:System.Windows.Forms.TableLayoutPanel> per implementare layout che rispondano correttamente man mano che i controlli vengono ridimensionati in seguito alle modifiche dei valori della proprietà <xref:System.Windows.Forms.Control.Text%2A>.  
  
## <a name="example"></a>Esempio  
 In questo form viene illustrato come creare un layout che viene modificato proporzionalmente quando si traducono i valori stringa visualizzati in altre lingue. Questo processo di traduzione è denominato *localizzazione*. Per altre informazioni, vedere [Localizzazione](../../../../docs/standard/globalization-localization/localization.md).  
  
 In Visual Studio è disponibile supporto completo per questa attività.  Vedere anche [Procedura dettagliata: creazione di un layout dalle proporzioni adattabili per la localizzazione](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [Procedura: Allineare ed estendere un controllo in un controllo TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Procedura dettagliata: disposizione dei controlli in Windows Form usando FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [Procedura: Inserire righe e colonne in un controllo TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
4.  [Procedura: Modificare colonne e righe in un controllo TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
5.  [Procedura dettagliata: esecuzione di attività comuni usando gli smart tag nei controlli Windows Form](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [Procedura dettagliata: disposizione di controlli in Windows Form usando TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [Procedura dettagliata: disposizione di controlli Windows Form usando spaziatura, margini e la proprietà AutoSize](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [Procedura: Supportare la localizzazione in Windows Form usando la proprietà AutoSize e il controllo TableLayoutPanel](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [Procedura dettagliata: creazione di un Windows Form ridimensionabile per l'inserimento di dati](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Riferimenti agli assembly System, System.Data, System.Drawing e System.Windows.Forms.  
  
 Per informazioni sulla compilazione di questo esempio dalla riga di comando per [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], vedere [Compilazione dalla riga di comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) o [Compilazione dalla riga di comando con csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). È anche possibile compilare questo esempio in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] incollando il codice in un nuovo progetto.  Vedere anche [Procedura: Compilare ed eseguire un esempio di codice Windows Forms completo con Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Localizzazione](../../../../docs/standard/globalization-localization/localization.md)
