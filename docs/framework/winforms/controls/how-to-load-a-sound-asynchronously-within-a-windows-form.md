---
title: 'Procedura: Caricare in modo asincrono un suono in un Windows Form'
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
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4ff6670c8e4d8ab735323fe13549e34c6cfd55f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a>Procedura: Caricare in modo asincrono un suono in un Windows Form
Nell'esempio di codice seguente viene caricato un suono in modo asincrono da un URL e quindi viene riprodotto in un nuovo thread.  
  
## <a name="example"></a>Esempio  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Riferimenti agli assembly System e System.Windows.Forms.  
  
-   Sostituzione del nome del file `"http://www.tailspintoys.com/sounds/stop.wav"` con un nome file valido.  
  
 Per informazioni sulla compilazione di questo esempio dalla riga di comando per [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] o [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], vedere [Compilazione dalla riga di comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) o [Compilazione dalla riga di comando con csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). È anche possibile compilare questo esempio in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] incollando il codice in un nuovo progetto.  Vedere anche [Procedura: Compilare ed eseguire un esempio di codice Windows Form completo tramite Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Le operazioni sui file devono essere racchiuse tra blocchi di gestione delle eccezioni appropriati.  
  
 Le seguenti condizioni possono generare un'eccezione:  
  
-   Il nome del percorso non è valido. Ad esempio, contiene caratteri non validi o solo uno spazio vuoto (classe <xref:System.ArgumentException>).  
  
-   Il percorso è di sola lettura (classe <xref:System.IO.IOException>).  
  
-   Il nome del percorso è `Nothing` (classe <xref:System.ArgumentNullException>).  
  
-   Il nome del percorso è troppo lungo (classe <xref:System.IO.PathTooLongException>).  
  
-   Il percorso non è valido (classe <xref:System.IO.DirectoryNotFoundException>).  
  
-   Il percorso contiene solo due punti ":" (classe <xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Non basarsi sul nome del file per prendere decisioni in merito al relativo contenuto. È possibile ad esempio che il file `Form1.vb` non sia un file di origine di Visual Basic. Prima di usare i dati nell'applicazione verificare tutti gli input.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [Procedura: Riprodurre un suono da un Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
