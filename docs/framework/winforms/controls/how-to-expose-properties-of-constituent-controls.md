---
title: "Procedura: esporre le proprietà dei controlli costitutivi"
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
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb85cb77c28ad443fb6837a5305a080c450220f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>Procedura: esporre le proprietà dei controlli costitutivi
I controlli che costituiscono un controllo composito sono detti *controlli costitutivi*. Questi controlli sono generalmente dichiarati privati e pertanto non è possibile accedere dallo sviluppatore. Se si desidera rendere disponibili le proprietà di questi controlli per gli utenti futuri, è necessario esporre all'utente. La proprietà di un controllo che costituiscono viene esposta la creazione di una proprietà nel controllo utente e usando il `get` e `set` funzioni di accesso di tale proprietà per rendere effettiva la modifica nella proprietà private del controllo che lo costituiscono.  
  
 Si consideri un controllo utente ipotetico con un pulsante che costituiscono denominato `MyButton`. In questo esempio, quando l'utente richiede la `ConstituentButtonBackColor` proprietà, il valore archiviato nel <xref:System.Windows.Forms.Control.BackColor%2A> proprietà `MyButton` viene recapitato. Quando l'utente assegna un valore di questa proprietà, tale valore viene passato automaticamente al <xref:System.Windows.Forms.Control.BackColor%2A> proprietà di `MyButton` e `set` eseguito codice che modifica il colore di `MyButton`.  
  
 Nell'esempio seguente viene illustrato come esporre il <xref:System.Windows.Forms.Control.BackColor%2A> proprietà del pulsante costituenti:  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>Per esporre una proprietà di un controllo che lo costituiscono  
  
1.  Creare una proprietà pubblica per il controllo utente.  
  
2.  Nel `get` sezione della proprietà, scrivere codice che recupera il valore della proprietà che si desidera esporre.  
  
3.  Nel `set` sezione della proprietà, scrivere codice che passa il valore della proprietà per proprietà esposta del controllo che lo costituiscono.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Forms.UserControl>  
 [Proprietà dei controlli Windows Form](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Tipi di controlli personalizzati](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
