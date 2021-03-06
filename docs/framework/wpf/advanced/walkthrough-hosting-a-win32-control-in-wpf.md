---
title: 'Procedura dettagliata: hosting di un controllo Win32 in WPF'
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
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 566be72cf330f6da83987f5e693176552471f091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Procedura dettagliata: hosting di un controllo Win32 in WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornisce un ambiente completo per la creazione di applicazioni. Tuttavia, quando si dispone di un investimento sostanziale in [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] codice, potrebbe essere più efficiente riutilizzare almeno alcuni che il codice del [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applicazione anziché riscriverla completamente. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fornisce un meccanismo semplice per l'hosting di un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] finestra, in un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pagina.  
  
 Questo argomento viene illustrata un'applicazione, [ospita un controllo ListBox Win32 in WPF](http://go.microsoft.com/fwlink/?LinkID=159998), che ospita un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controllo casella di riepilogo. Questa procedura generale può essere estesa per l'hosting di qualsiasi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] finestra.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Requisiti  
 Questo argomento si presuppone una conoscenza di base della [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] di programmazione. Per un'introduzione a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] di programmazione, vedere [Introduzione](../../../../docs/framework/wpf/getting-started/index.md). Per un'introduzione ai [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] linguaggio di programmazione, si deve fare riferimento a uno dei numerosi manuali sull'argomento, in particolare *programmazione Windows* di Charles Petzold.  
  
 Poiché il codice di esempio che accompagna questo argomento viene implementato [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], si avvalgono di [!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)] per l'accesso di [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Familiarità con [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] è utile, ma non essenziali.  
  
> [!NOTE]
>  Questo argomento include vari esempi di codice tratti dall'esempio associato. Tuttavia, per una questione di leggibilità, il codice di esempio completo non è compreso. È possibile ottenere o visualizzare il codice completo di [ospita un controllo ListBox Win32 in WPF](http://go.microsoft.com/fwlink/?LinkID=159998).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Procedura di base  
 Questa sezione descrive la procedura di base per l'hosting di un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] finestra su un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pagina. Le sezioni rimanenti illustrano in dettaglio i vari passaggi.  
  
 La procedura di hosting base è la seguente:  
  
1.  Implementare un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pagina per ospitare la finestra. Una tecnica consiste nel creare un <xref:System.Windows.Controls.Border> elemento per riservare una sezione della pagina per la finestra di hosting.  
  
2.  Implementare una classe per ospitare il controllo che eredita da <xref:System.Windows.Interop.HwndHost>.  
  
3.  In questa classe, eseguire l'override di <xref:System.Windows.Interop.HwndHost> membro della classe <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Creare la finestra di hosting come figlio della finestra che contiene il [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pagina. Sebbene convenzionale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programmazione non è necessario eseguire in modo esplicito di usarla, la pagina di hosting è una finestra con un handle (HWND). Verrà visualizzata la pagina HWND tramite il `hwndParent` parametro del <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> metodo. La finestra ospitata deve essere creata come elemento figlio dell'oggetto HWND.  
  
5.  Dopo aver creato la finestra host, restituire l'oggetto HWND della finestra ospitata. Se si desidera ospitare uno o più [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controlli, in genere creano una finestra host come elemento figlio di HWND e verificare gli elementi figlio di controlli di tale finestra host. Il wrapping dei controlli in una finestra host fornisce un modo semplice per il [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pagina per ricevere notifiche da controlli, che si occupa determinate [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problemi relativi a notifiche attraverso il limite di HWND.  
  
6.  Gestire i messaggi selezionati inviati alla finestra host, ad esempio notifiche dai controlli figlio. È possibile ottenere questo risultato in due modi.  
  
    -   Se si preferisce per gestire i messaggi nella classe di hosting, eseguire l'override di <xref:System.Windows.Interop.HwndHost.WndProc%2A> metodo la <xref:System.Windows.Interop.HwndHost> classe.  
  
    -   Se si preferisce che i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] gestiscono i messaggi, gestire il <xref:System.Windows.Interop.HwndHost> classe <xref:System.Windows.Interop.HwndHost.MessageHook> eventi nel code-behind. Questo evento si verifica per ogni messaggio ricevuto dalla finestra ospitata. Se si sceglie questa opzione, è comunque necessario sostituire <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ma è necessario solo un'implementazione minima.  
  
7.  Eseguire l'override di <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> e <xref:System.Windows.Interop.HwndHost.WndProc%2A> metodi di <xref:System.Windows.Interop.HwndHost>. È necessario eseguire l'override di questi metodi per soddisfare il <xref:System.Windows.Interop.HwndHost> contratto, ma potrebbe essere necessario solo fornire un'implementazione minima.  
  
8.  Nel file code-behind, creare un'istanza della classe di hosting del controllo e renderlo un elemento figlio del <xref:System.Windows.Controls.Border> elemento che deve ospitare la finestra.  
  
9. Comunicare con la finestra di hosting inviandole [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] messaggi e gestione delle finestre figlio, ad esempio le notifiche inviate mediante controlli.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementare il layout di pagina  
 Il layout per il [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pagina che contiene il controllo casella di riepilogo è costituita da due aree. Il lato sinistro della pagina ospita diversi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i controlli che forniscono un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] che consente di modificare il [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controllo. L'angolo superiore destro della pagina include un'area quadrata per il controllo ListBox ospitato.  
  
 Il codice per implementare questo layout è piuttosto semplice. L'elemento radice è un <xref:System.Windows.Controls.DockPanel> che dispone di due elementi figlio. Il primo è un <xref:System.Windows.Controls.Border> elemento che contiene il controllo casella di riepilogo. Occupa un quadrato 200x200 nell'angolo superiore destro della pagina. Il secondo è un <xref:System.Windows.Controls.StackPanel> elemento che contiene un set di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i controlli che visualizzano le informazioni e consentono di modificare il controllo ListBox impostando proprietà di interoperatività esposte. Per ognuno degli elementi figlio del <xref:System.Windows.Controls.StackPanel>, vedere il materiale di riferimento per i diversi elementi utilizzati per informazioni dettagliate su questi elementi sono o le operazioni eseguite, questi sono elencati nell'esempio di codice riportato di seguito, ma non potranno essere illustrati in questo argomento (di base modello di interazione non richiede alcuna di esse, vengono forniti per aggiungere alcune interattività all'esempio).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementare una classe per l'hosting del controllo Microsoft Win32  
 La parte centrale di questo esempio è la classe che ospita effettivamente il controllo, ControlHost.cs. Eredita da <xref:System.Windows.Interop.HwndHost>. Il costruttore accetta due parametri, altezza e larghezza, che corrisponde all'altezza e larghezza di <xref:System.Windows.Controls.Border> elemento che contiene il controllo casella di riepilogo. Questi valori vengono utilizzati in un secondo momento per assicurarsi che le dimensioni del controllo corrisponda il <xref:System.Windows.Controls.Border> elemento.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 È anche presente un insieme di costanti. Queste costanti sono in gran parte tratte da Winuser. h e consentono di utilizzare nomi convenzionali, quando si chiama [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funzioni.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Eseguire l'override di BuildWindowCore per creare la finestra Microsoft Win32  
 Si esegue l'override di questo metodo per creare il [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] finestra che verrà ospitata dalla pagina e stabilire la connessione tra la finestra e la pagina. Poiché questo esempio include l'hosting di un controllo ListBox vengono create due finestre. Il primo è la finestra effettivamente ospitato dal [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pagina. Il controllo ListBox viene creato come elemento figlio di questa finestra.  
  
 Lo scopo di questo approccio è semplificare il processo di ricezione di notifiche dal controllo. La <xref:System.Windows.Interop.HwndHost> classe consente di elaborare i messaggi inviati alla finestra di hosting. Se si ospita un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controllare direttamente, si ricevono i messaggi inviati al ciclo di messaggi interni del controllo. È possibile visualizzare il controllo e inviare a esso messaggi ma non ricevere le notifiche che il controllo invia alla propria finestra padre. Ciò significa, tra l'altro, che non è possibile in alcun modo rilevare quando l'utente interagisce con il controllo. Creare invece una finestra host e impostare il controllo come elemento figlio di tale finestra. Ciò consente di elaborare i messaggi per la finestra host, incluse le notifiche inviate a essa dal controllo. Per comodità, dal momento che la finestra host è poco più di un semplice wrapper per il controllo, il pacchetto verrà restituito come un controllo ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Creare la finestra host e il controllo ListBox  
 È possibile utilizzare [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] per creare una finestra host per il controllo tramite la creazione e registrazione di una classe di finestra e così via. Tuttavia, un approccio molto più semplice consiste nel creare una finestra con la classe della finestra "statica" predefinita. Questo approccio rende disponibile la procedura della finestra necessaria per ricevere le notifiche dal controllo e richiede codice minimo.  
  
 L'oggetto HWND del controllo è esposto tramite una proprietà di sola lettura di modo che la pagina host possa usarlo per inviare messaggi al controllo.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Il controllo ListBox viene creato come elemento figlio della finestra host. L'altezza e la larghezza di entrambe le finestre sono impostate sui valori passati dal costruttore, come illustrato in precedenza. Ciò garantisce che le dimensioni della finestra host e del controllo siano identiche all'area riservata nella pagina.  Dopo aver create le finestre, nell'esempio viene restituito un <xref:System.Runtime.InteropServices.HandleRef> oggetto che contiene l'HWND della finestra host.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implementare DestroyWindow e WndProc  
 Oltre a <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, inoltre, è necessario eseguire l'override di <xref:System.Windows.Interop.HwndHost.WndProc%2A> e <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> metodi del <xref:System.Windows.Interop.HwndHost>. In questo esempio, i messaggi per il controllo sono gestiti dal <xref:System.Windows.Interop.HwndHost.MessageHook> gestore, pertanto l'implementazione di <xref:System.Windows.Interop.HwndHost.WndProc%2A> e <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> è minimo. In caso di <xref:System.Windows.Interop.HwndHost.WndProc%2A>, impostare `handled` a `false` per indicare che il messaggio non è stato gestito e restituiscono 0. Per <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, eliminare semplicemente la finestra.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Ospitare il controllo nella pagina  
 Per ospitare il controllo nella pagina, creare innanzitutto una nuova istanza di `ControlHost` classe. Passare l'altezza e larghezza dell'elemento bordo che contiene il controllo (`ControlHostElement`) per il `ControlHost` costruttore. Questo garantisce che le dimensioni di ListBox siano corrette. Ospitare il controllo nella pagina quindi assegnando il `ControlHost` dell'oggetto per il <xref:System.Windows.Controls.Decorator.Child%2A> proprietà dell'host <xref:System.Windows.Controls.Border>.  
  
 Nell'esempio viene associato un gestore per il <xref:System.Windows.Interop.HwndHost.MessageHook> evento del `ControlHost` per ricevere messaggi dal controllo. Questo evento viene generato per ogni messaggio inviato alla finestra ospitata. In questo caso, si tratta dei messaggi inviati alla finestra che esegue il wrapping del controllo ListBox effettivo, incluse le notifiche dal controllo. L'esempio chiama SendMessage per ottenere informazioni dal controllo e ne modifica il contenuto. I dettagli di come la pagina comunica con il controllo sono illustrati nella sezione successiva.  
  
> [!NOTE]
>  Si noti che sono disponibili due [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] dichiarazioni per SendMessage. Ciò è necessario perché una viene utilizzato il `wParam` parametro da passare una stringa e l'altro utilizza per passare un numero intero. È necessaria una dichiarazione separata per ogni firma per assicurare che venga eseguito correttamente il marshalling dei dati.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementare la comunicazione tra il controllo e la pagina  
 Modificare il controllo mediante l'invio [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] messaggi. Il controllo comunica quando l'utente interagisce con esso inviando notifiche alla propria finestra host. Il [ospita un controllo ListBox Win32 in WPF](http://go.microsoft.com/fwlink/?LinkID=159998) esempio include un'interfaccia utente che fornisce alcuni esempi del funzionamento:  
  
-   Accodare un elemento all'elenco.  
  
-   Eliminare l'elemento selezionato dall'elenco.  
  
-   Visualizzare il testo dell'elemento attualmente selezionato.  
  
-   Visualizzare il numero di elementi nell'elenco.  
  
 L'utente può anche selezionare un elemento nella casella di riepilogo facendo clic su di esso, esattamente come accade per un convenzionale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dell'applicazione. I dati visualizzati vengono aggiornati ogni vota che l'utente modifica lo stato della casella di riepilogo, selezionando, aggiungendo o accodando un elemento.  
  
 Per accodare elementi, inviare alla casella di riepilogo un messaggio LB_ADDSTRING. Per eliminare gli elementi, inviare LB_GETCURSEL per ottenere l'indice della selezione corrente e quindi LB_DELETESTRING per eliminare l'elemento. L'esempio invia anche LB_GETCOUNT e usa il valore restituito per aggiornare la visualizzazione che mostra il numero di elementi. Entrambe queste istanze di SendMessage utilizzano uno del [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] dichiarazioni illustrate nella sezione precedente.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Quando l'utente seleziona un elemento o modifica la selezione, il controllo invia una notifica alla finestra host mediante l'invio di un messaggio WM_COMMAND che genera il <xref:System.Windows.Interop.HwndHost.MessageHook> evento per la pagina. Il gestore riceve le stesse informazioni della routine della finestra principale della finestra host. Inoltre, viene passato un riferimento a un valore booleano, `handled`. Impostare `handled` a `true` per indicare che il messaggio è stato gestito e che necessita di alcuna ulteriore elaborazione.  
  
 WM_COMMAND viene inviato per diversi motivi, pertanto è necessario esaminare l'ID della notifica per determinare se si tratta di un evento che è opportuno gestire. L'ID è contenuto in word alto del `wParam` parametro. Poiché [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] does non dispone di una macro HIWORD, l'esempio Usa gli operatori bit per bit per estrarre l'ID. Se l'utente ha effettuato o modificato la selezione, l'ID sarà LBN_SELCHANGE.  
  
 Quando viene ricevuto LBN_SELCHANGE, il codice di esempio ottiene l'indice dell'elemento selezionato inviando al controllo un messaggio LB_GETCURSEL. Per ottenere il testo, creare innanzitutto un <xref:System.Text.StringBuilder>. Quindi inviare al controllo un messaggio LB_GETTEXT. Passare il vuoto <xref:System.Text.StringBuilder> oggetto come il `wParam` parametro. Quando viene restituito SendMessage, <xref:System.Text.StringBuilder> conterrà il testo dell'elemento selezionato. Questo utilizzo di SendMessage richiede ancora un altro [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] dichiarazione.  
  
 Infine, impostare `handled` a `true` per indicare che il messaggio è stato gestito.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Windows.Interop.HwndHost>  
 [Interoperatività di WPF e Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Procedura dettagliata: Prima applicazione desktop WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
