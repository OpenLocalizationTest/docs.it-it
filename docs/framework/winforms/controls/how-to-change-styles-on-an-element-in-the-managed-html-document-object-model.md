---
title: 'Procedura: modificare gli stili di un elemento nel Document Object Model HTML gestito'
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
helpviewer_keywords: managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 968dd4210e13e301ba2f0ca24617df23706cefc0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Procedura: modificare gli stili di un elemento nel Document Object Model HTML gestito
È possibile utilizzare gli stili HTML per controllare l'aspetto di un documento e i relativi elementi. <xref:System.Windows.Forms.HtmlDocument>e <xref:System.Windows.Forms.HtmlElement> supporta <xref:System.Windows.Forms.HtmlElement.Style%2A> le proprietà che accettano stringhe di formato seguente:  
  
 `name1:value1;...;nameN:valueN;`  
  
 Ecco un `DIV` con una stringa che imposta il tipo di carattere Arial e tutto il testo da visualizzare in grassetto:  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 Il problema con la modifica degli stili mediante il <xref:System.Windows.Forms.HtmlElement.Style%2A> proprietà è difficoltà di aggiungere e rimuovere singole impostazioni di stile dalla stringa. Ad esempio, diventa una procedura complessa per poter eseguire il rendering di testo precedente in corsivo ogni volta che l'utente posiziona il cursore sul `DIV`e intraprendere corsivo quando il cursore viene spostato il `DIV`. Tempo diventerebbe un problema se si desidera modificare un numero elevato di stili in questo modo.  
  
 La procedura seguente contiene codice che consente di gestire facilmente stili in documenti HTML e gli elementi. La procedura è richiesta la conoscenza di come eseguire attività di base in Windows Form, ad esempio la creazione di un nuovo progetto e aggiungendo un controllo a un form.  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Per elaborare le modifiche di stile in un'applicazione Windows Form  
  
1.  Creare un nuovo progetto Windows Form.  
  
2.  Creare un nuovo file di classe di estensione appropriato per il linguaggio di programmazione.  
  
3.  Copia il `StyleGenerator` codice nella sezione esempio di questo argomento della classe nel file di classe e salvare il codice.  
  
4.  Salvare il codice HTML seguente in un file denominato htm.  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  Aggiungere un <xref:System.Windows.Forms.WebBrowser> controllo denominato `webBrowser1` al form principale del progetto.  
  
6.  Aggiungere il codice seguente al file di codice del progetto.  
  
    > [!IMPORTANT]
    >  Verificare che il `webBrowser1_DocumentCompleted` gestore dell'evento è configurato come un listener per il <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> evento. In [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], fare doppio clic su di <xref:System.Windows.Forms.WebBrowser> controllo; in un editor di testo, configurare il listener a livello di codice.  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  Eseguire il progetto. Spostare il cursore sulla prima `DIV` e osservare gli effetti del codice.  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente mostra il codice completo per il `StyleGenerator` (classe), che analizza un valore di stile esistente, supporta l'aggiunta, modifica e rimozione di stili e restituisce un nuovo valore di stile con le modifiche richieste.  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Forms.HtmlElement>
