---
title: Disegno di testo formattato
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
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cad79f26a48f3f5e905b2f2ac7de9191dd8539f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="drawing-formatted-text"></a>Disegno di testo formattato
In questo argomento viene fornita una panoramica delle funzionalità del <xref:System.Windows.Media.FormattedText> oggetto. che offre un controllo di basso livello per il disegno di testo nelle applicazioni [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
  
## <a name="technology-overview"></a>Informazioni generali sulla tecnologia  
 Il <xref:System.Windows.Media.FormattedText> oggetto consente di disegnare testo su più righe in cui ogni carattere del testo può essere formattato singolarmente. L'esempio seguente mostra un testo a cui sono stati applicati diversi formati.  
  
 ![Testo visualizzato usando l'oggetto FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Testo visualizzato con il metodo FormattedText  
  
> [!NOTE]
>  Per gli sviluppatori che eseguono la migrazione dall'API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], nella tabella della sezione [Migrazione Win32](#win32_migration) sono elencati i flag DrawText di [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e gli elementi corrispondenti in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Motivi per l'uso del testo formattato  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] include più controlli per la creazione di testo sullo schermo. Ogni controllo è destinato a uno scenario diverso e dispone di un proprio elenco di funzionalità e limitazioni. In generale, il <xref:System.Windows.Controls.TextBlock> elemento deve essere utilizzato quando il supporto limitato del testo è richiesto, ad esempio una frase breve in un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>può essere utilizzato quando è richiesto il supporto minimo del testo. Per altre informazioni, vedere [Documenti in WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 Il <xref:System.Windows.Media.FormattedText> oggetto fornisce più funzionalità rispetto di formattazione del testo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] controlli testo e può essere utile nei casi in cui si desidera utilizzare il testo come elemento decorativo. Per altre informazioni, vedere la sezione seguente [Conversione del testo formattato in una geometria](#converting_formatted_text).  
  
 Inoltre, il <xref:System.Windows.Media.FormattedText> oggetto è utile per la creazione di orientati al testo <xref:System.Windows.Media.DrawingVisual>-oggetti derivati. <xref:System.Windows.Media.DrawingVisual>è una classe leggera di disegno che viene utilizzata per eseguire il rendering delle forme, immagini o testo. Per altre informazioni, vedere [Esempio di hit test mediante DrawingVisual](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Uso dell'oggetto FormattedText  
 Per creare il testo formattato, chiamare il <xref:System.Windows.Media.FormattedText.%23ctor%2A> costruttore per creare un <xref:System.Windows.Media.FormattedText> oggetto. Dopo aver creato la stringa di testo formattato iniziale, è possibile applicare una gamma di stili di formattazione.  
  
 Utilizzare il <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> proprietà per vincolare il testo da una larghezza specifica. Il testo andrà a capo automaticamente per evitare di superare la larghezza specificata. Utilizzare il <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> proprietà per vincolare il testo da un'altezza specifica. Saranno visualizzati dei puntini di sospensione ("...") nel caso in cui il testo superi l'altezza specificata.  
  
 ![Testo visualizzato usando l'oggetto FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Testo visualizzato con ritorno a capo automatico e puntini di sospensione  
  
 È possibile applicare vari stili di formattazione a uno o più caratteri. Ad esempio, è possibile chiamare entrambi il <xref:System.Windows.Media.FormattedText.SetFontSize%2A> e <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metodi per modificare la formattazione dei primi cinque caratteri nel testo.  
  
 L'esempio di codice seguente crea un <xref:System.Windows.Media.FormattedText> dell'oggetto e quindi applica diversi stili di formattazione al testo.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unità di misura delle dimensioni del carattere  
 Come con altri oggetti di testo in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applicazioni, il <xref:System.Windows.Media.FormattedText> oggetto utilizza device independent pixel come unità di misura. Tuttavia, la maggior parte delle applicazioni [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] usa i punti come unità di misura. Se si desidera usare il testo visualizzato in una scala di punti nelle applicazioni [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], sarà necessario convertire le [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] in punti. Nell'esempio di codice seguente viene illustrato come eseguire questa conversione.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Conversione del testo formattato in una geometria  
 È possibile convertire il testo formattato in <xref:System.Windows.Media.Geometry> oggetti, che consente di creare altri tipi di testo visivamente interessante. Ad esempio, è possibile creare un <xref:System.Windows.Media.Geometry> oggetto in base alla struttura di una stringa di testo.  
  
 ![Struttura di testo con pennello sfumato lineare](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Struttura di testo con pennello sfumato lineare  
  
 Gli esempi seguenti illustrano diverse modalità di creazione di effetti visivi interessanti tramite la modifica del tratto, del riempimento e dell'evidenziazione del testo convertito.  
  
 ![Testo con colori diversi per tratto e riempimento](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Esempio di impostazione di tratto e riempimento in colori diversi  
  
 ![Testo con tratto con immagine applicato alla traccia](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Esempio di un pennello immagine applicato al tratto  
  
 ![Testo con tratto con immagine applicato alla traccia](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Esempio di un pennello immagine applicato al tratto ed evidenziazione  
  
 Quando il testo viene convertito in un <xref:System.Windows.Media.Geometry> dell'oggetto, non è più un insieme di caratteri, non è possibile modificare i caratteri nella stringa di testo. Tuttavia, è possibile intervenire sull'aspetto del testo convertito modificandone le proprietà del tratto e del riempimento. Il tratto fa riferimento alla struttura del testo convertito, mentre il riempimento fa riferimento all'area all'interno della struttura del testo convertito. Per altre informazioni, vedere [Creare testo con contorni](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 È anche possibile convertire il testo formattato in un <xref:System.Windows.Media.PathGeometry> dell'oggetto e utilizzare l'oggetto per evidenziare il testo. Ad esempio, è possibile applicare un'animazione per il <xref:System.Windows.Media.PathGeometry> dell'oggetto in modo che segua la struttura del testo formattato.  
  
 Nell'esempio seguente viene formattato il testo che è stato convertito in un <xref:System.Windows.Media.PathGeometry> oggetto. Un'ellisse animata segue il percorso dei tratti del testo di cui è stato eseguito il rendering.  
  
 ![Sfera che segue la geometria del percorso del testo](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
Sfera che segue la geometria del percorso del testo  
  
 Per altre informazioni, vedere [Procedura: Creare animazioni PathGeometry per il testo](http://msdn.microsoft.com/en-us/29f8051e-798a-463f-a926-a099a99e9c67).  
  
 È possibile creare altri utilizzi interessanti del testo formattato dopo che è stato convertito in un <xref:System.Windows.Media.PathGeometry> oggetto. Ad esempio, è possibile ritagliare video da visualizzare all'interno del testo.  
  
 ![Video visualizzato nella geometria del percorso del testo](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Video visualizzato nella geometria del percorso del testo  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migrazione Win32  
 Le funzionalità di <xref:System.Windows.Media.FormattedText> per il disegno di testo sono simili alle funzionalità del [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] funzione DrawText. Per gli sviluppatori che eseguono la migrazione dall'API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], nella tabella seguente sono elencati i flag DrawText di [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e gli elementi corrispondenti in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Flag DrawText|Elemento corrispondente in WPF|Note|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilizzare il <xref:System.Windows.Media.FormattedText.Height%2A> proprietà per calcolare una [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] posizione DrawText 'y'.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Utilizzare il <xref:System.Windows.Media.FormattedText.Height%2A> e <xref:System.Windows.Media.FormattedText.Width%2A> proprietà per calcolare il rettangolo di output.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilizzare il <xref:System.Windows.Media.FormattedText.TextAlignment%2A> proprietà con il valore impostato su <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Nessuno|Non richiesto La larghezza dello spazio e il rendering dell'ultima riga sono uguali a quelli del controllo di modifica del framework.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilizzare il <xref:System.Windows.Media.FormattedText.Trimming%2A> proprietà con il valore <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Utilizzare <xref:System.Windows.TextTrimming.WordEllipsis> ottenere [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS e terminano con puntini di sospensione, in questo caso, i puntini di sospensione carattere si verifica solo su parole che non rientrano in una singola riga.|  
|DT_EXPAND_TABS|Nessuno|Non richiesto Le tabulazioni vengono espanse automaticamente per interrompersi ogni 4 em, all'incirca a una larghezza di 8 caratteri indipendenti dalla lingua.|  
|DT_EXTERNALLEADING|Nessuno|Non richiesto L'interlinea esterna è sempre inclusa nell'interlinea. Utilizzare il <xref:System.Windows.Media.FormattedText.LineHeight%2A> proprietà per creare l'interlinea definita dall'utente.|  
|DT_HIDEPREFIX|Nessuno|Non supportato. Rimuovere '&' dalla stringa prima di costruire il <xref:System.Windows.Media.FormattedText> oggetto.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Impostazione predefinita per l'allineamento del testo. Utilizzare il <xref:System.Windows.Media.FormattedText.TextAlignment%2A> proprietà con il valore impostato su <xref:System.Windows.TextAlignment.Left>. (solo WPF).|  
|DT_MODIFYSTRING|Nessuno|Non supportata.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Il ritaglio non viene eseguito automaticamente. Se si desidera ritagliare il testo, utilizzare il <xref:System.Windows.Media.Visual.VisualClip%2A> proprietà.|  
|DT_NOFULLWIDTHCHARBREAK|Nessuno|Non supportata.|  
|DT_NOPREFIX|Nessuno|Non richiesto Il carattere "&" nelle stringhe viene sempre considerato un carattere normale.|  
|DT_PATHELLIPSIS|Nessuno|Utilizzare il <xref:System.Windows.Media.FormattedText.Trimming%2A> proprietà con il valore <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Nessuno|Non supportato. Se si desidera utilizzare caratteri di sottolineatura per il testo, ad esempio un tasto di scelta rapida o un collegamento, usare il <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> metodo.|  
|DT_PREFIXONLY|Nessuno|Non supportata.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilizzare il <xref:System.Windows.Media.FormattedText.TextAlignment%2A> proprietà con il valore impostato su <xref:System.Windows.TextAlignment.Right>. (solo WPF).|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Impostare la proprietà <xref:System.Windows.Media.FormattedText.FlowDirection%2A> su <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Nessuno|Non richiesto <xref:System.Windows.Media.FormattedText>gli oggetti si comportano come un controllo a riga singola, a meno che entrambi i <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> proprietà è impostata o il testo contiene un ritorno a capo/avanzamento riga (CR/LF).|  
|DT_TABSTOP|Nessuno|Nessun supporto per le posizioni delle tabulazioni definite dall'utente.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Non richiesto Il testo è giustificato nella parte superiore per impostazione predefinita. Gli altri valori di posizionamento verticale possono essere definiti tramite il <xref:System.Windows.Media.FormattedText.Height%2A> proprietà per calcolare una [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] posizione DrawText 'y'.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilizzare il <xref:System.Windows.Media.FormattedText.Height%2A> proprietà per calcolare una [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] posizione DrawText 'y'.|  
|DT_WORDBREAK|Nessuno|Non richiesto Le parole vengono interrotte automaticamente con <xref:System.Windows.Media.FormattedText> oggetti. Non è possibile disabilitare questa impostazione.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilizzare il <xref:System.Windows.Media.FormattedText.Trimming%2A> proprietà con il valore <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Media.FormattedText>  
 [Documenti in WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Funzionalità tipografiche di WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Creare testo con contorni](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)  
 [Procedura: Creare animazioni PathGeometry per il testo](http://msdn.microsoft.com/en-us/29f8051e-798a-463f-a926-a099a99e9c67)
