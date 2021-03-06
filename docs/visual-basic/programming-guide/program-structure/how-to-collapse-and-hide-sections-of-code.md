---
title: 'Procedura: comprimere e nascondere sezioni di codice (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a31f0c8af9b84e87ebe1e5191d72d19be8340f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>Procedura: comprimere e nascondere sezioni di codice (Visual Basic)
Il `#Region` direttiva consente di comprimere e nascondere sezioni di codice in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] file. Il `#Region` direttiva consente di specificare un blocco di codice che è possibile espandere o comprimere tramite la [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] editor di codice. La possibilità di nascondere in modo selettivo il codice rende i file più gestibile e più facile da leggere. Per altre informazioni, vedere [Struttura](/visualstudio/ide/outlining).  
  
 `#Region`direttive supportano la semantica dei blocchi di codice, ad esempio `#If...#End If`. Ciò significa che non possono iniziare in un blocco e terminare con un altro. inizio e fine deve essere nello stesso blocco. `#Region`direttive non sono supportate all'interno di funzioni.  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>Per comprimere e nascondere una sezione di codice  
  
-   Inserire la sezione di codice tra le `#Region` e `#End Region` istruzioni, come nell'esempio seguente:  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     Il `#Region` blocco può essere utilizzato più volte in un file di codice; pertanto, gli utenti possono definire i propri blocchi di routine e le classi che a sua volta, possono essere compressi. `#Region`blocchi possono anche essere annidati all'interno di altri `#Region` blocchi.  
  
    > [!NOTE]
    >  Nascondere il codice non impedisce che venga compilato e non influisce sulla `#If...#End If` istruzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione condizionale](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [Direttiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)  
 [Direttive #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Struttura](/visualstudio/ide/outlining)
