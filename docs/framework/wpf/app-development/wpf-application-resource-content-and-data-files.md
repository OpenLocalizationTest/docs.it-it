---
title: File di dati e di risorse dell'applicazione WPF.
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
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19fd82daabd5ed12776b2deee6bc850529a6ef23
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2017
---
# <a name="wpf-application-resource-content-and-data-files"></a>File di dati e di risorse dell'applicazione WPF.
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]le applicazioni spesso dipendono dai file che contengono dati non eseguibili, ad esempio [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], immagini, video e audio. [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] offre un supporto speciale per la configurazione, l'identificazione e l'utilizzo di questi tipi di file di dati, definiti file di dati dell'applicazione. Questo supporto si basa su un set specifico di tipi di file di dati dell'applicazione, che include:  
  
-   **File di risorse**: file di dati che vengono compilati in un file eseguibile o libreria [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
-   **File di dati**: file di dati autonomi che dispongono di un'associazione esplicita con un file eseguibile [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
-   **Sito di origine**: file di dati autonomi che non hanno alcuna associazione con un file eseguibile [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
 Un'importante distinzione da fare tra questi tre tipi di file riguarda il fatto che i file di risorse e i file di dati sono resi noti in fase di compilazione e pertanto sono conosciuti esplicitamente da un assembly. Per il sito di origine, tuttavia, un assembly non può avere alcuna conoscenza della loro del tutto, conoscenza implicita tramite un pacchetto o [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] riferimento; nel caso di quest'ultimo, non c'è garanzia che il sito di riferimento di file di origine esista effettivamente.  
  
 Per fare riferimento a file di dati dell'applicazione, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] utilizza tale [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] schema, come descritto in dettaglio in [URI di tipo Pack in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).  
  
 Questo argomento descrive come configurare e usare i file di dati dell'applicazione.  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>File di risorse  
 Se un file di dati deve essere sempre disponibile per un'applicazione, l'unico modo per garantire la disponibilità è compilarlo nell'assembly eseguibile principale dell'applicazione o in uno degli assembly a cui si fa riferimento. Questo tipo di file di dati dell'applicazione è noto come un *file di risorse*.  
  
 I file di risorse devono essere utilizzati nei casi seguenti:  
  
-   Non occorre aggiornare il contenuto del file di risorse dopo la relativa compilazione in un assembly.  
  
-   Si desidera semplificare la complessità di distribuzione dell'applicazione riducendo il numero di dipendenze dei file.  
  
-   File di dati dell'applicazione deve essere localizzabile (vedere [WPF Panoramica della globalizzazione e localizzazione](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  I file di risorse descritti in questa sezione sono diversi da file di risorse descritta [risorse XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) e diverso da quello delle risorse incorporate o collegate al [risorse dell'applicazione di gestione (.NET) ](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>Configurazione dei file di risorse  
 In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], un file di risorse è un file che è incluso in un [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] il progetto come un `Resource` elemento.  
  
```xml  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  In [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], si crea un file di risorse mediante l'aggiunta di un file a un progetto e impostare il relativo `Build Action` a `Resource`.  
  
 Quando il progetto viene compilato, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] compila la risorsa nell'assembly.  
  
### <a name="using-resource-files"></a>Uso dei file di risorse  
 Per caricare un file di risorse, è possibile chiamare il <xref:System.Windows.Application.GetResourceStream%2A> metodo il <xref:System.Windows.Application> (classe), il passaggio di un pacchetto di [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] che identifica il file di risorsa desiderata. <xref:System.Windows.Application.GetResourceStream%2A>Restituisce un <xref:System.Windows.Resources.StreamResourceInfo> oggetto, che espone il file di risorse come un <xref:System.IO.Stream> e ne descrive il tipo di contenuto.  
  
 Ad esempio, il codice seguente viene illustrato come utilizzare <xref:System.Windows.Application.GetResourceStream%2A> per caricare un <xref:System.Windows.Controls.Page> risorse di file e impostarlo come contenuto di un <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Durante la chiamata <xref:System.Windows.Application.GetResourceStream%2A> consente di accedere al <xref:System.IO.Stream>, è necessario eseguire ulteriori operazioni di conversione al tipo della proprietà verrà impostato con. È invece possibile consentire [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] occuperà di apertura e la conversione di <xref:System.IO.Stream> caricando un file di risorse direttamente nella proprietà di un tipo tramite codice.  
  
 Nell'esempio seguente viene illustrato come caricare un <xref:System.Windows.Controls.Page> direttamente in un <xref:System.Windows.Controls.Frame> (`pageFrame`) mediante il codice.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 L'esempio seguente illustra il markup equivalente del precedente esempio.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>File di codice dell'applicazione come file di risorse  
 Uno speciale set di [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] file di codice dell'applicazione è possibile fare riferimento utilizzando pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], tra cui windows, pagine, documenti dinamici e dizionari delle risorse. Ad esempio, è possibile impostare il <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> proprietà con un pacchetto di [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] che fa riferimento alla finestra o una pagina che si desidera caricare all'avvio di un'applicazione.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 È possibile eseguire questa operazione quando un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file è incluso un [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] il progetto come un `Page` elemento.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], si aggiunge un nuovo <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, o <xref:System.Windows.ResourceDictionary> a un progetto, il `Build Action` per il markup file utilizzerà `Page`.  
  
 Quando un progetto con `Page` elementi viene compilato, il [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementi vengono convertiti in formato binario e compilati in assembly associato. Di conseguenza, questi file possono essere utilizzati allo stesso modo dei file di risorse tipici.  
  
> [!NOTE]
>  Se un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file è configurato come un `Resource` elemento e non dispone di un file code-behind, non elaborato [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] viene compilato in un assembly, anziché una versione binaria del non elaborato [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>File di dati  
 Oggetto *file di contenuto* viene distribuito come file separato insieme a un assembly eseguibile. Sebbene questi file non vengano compilati in un assembly, dal canto loro gli assembly vengono compilati con i metadati che stabiliscono un'associazione con ciascun file di dati.  
  
 È necessario utilizzare i file di dati quando l'applicazione richiede un set specifico di file di dati che possono essere aggiornati senza dover ricompilare l'assembly che li utilizza.  
  
### <a name="configuring-content-files"></a>Configurazione dei file di dati  
 Per aggiungere un file di contenuto a un progetto, un file di dati dell'applicazione deve essere incluso come un `Content` elemento. Inoltre, poiché un file di contenuto non viene compilato nell'assembly, è necessario impostare il [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` elemento dei metadati per specificare che il file di contenuto viene copiato in un percorso relativo all'assembly compilato. Se si desidera che la risorsa da copiare nella cartella di output di compilazione ogni volta che viene compilato un progetto, impostare il `CopyToOutputDirectory` elemento dei metadati con il `Always` valore. In caso contrario, è possibile assicurarsi che solo la versione più recente della risorsa viene copiata nella cartella di output di compilazione tramite la `PreserveNewest` valore.  
  
 Di seguito viene illustrato un file configurato come file di dati, che viene copiato nella cartella dell'output di compilazione solo quando una nuova versione della risorsa viene aggiunta al progetto.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], si crea un file di contenuto aggiungendo un file a un progetto e impostare il relativo `Build Action` per `Content`e impostare relativo `Copy to Output Directory` per `Copy always` (uguale a `Always`) e `Copy if newer` (uguale a `PreserveNewest`).  
  
 Quando il progetto viene compilato, un <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> viene compilato attributo nei metadati dell'assembly per ciascun file di contenuto.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 Il valore di <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implica il percorso al file di contenuto relativo alla posizione nel progetto. Ad esempio, se un file di contenuto si trova in una sottocartella del progetto, le informazioni sul percorso aggiuntive verrebbero incorporate nel <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valore.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 Il <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valore è anche il valore del percorso al file di contenuto nella cartella di output di compilazione.  
  
### <a name="using-content-files"></a>Uso dei file di contenuto  
 Per caricare un file di contenuto, è possibile chiamare il <xref:System.Windows.Application.GetContentStream%2A> metodo il <xref:System.Windows.Application> (classe), il passaggio di un pacchetto di [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] che identifica il file di contenuto desiderato. <xref:System.Windows.Application.GetContentStream%2A>Restituisce un <xref:System.Windows.Resources.StreamResourceInfo> oggetto, che espone il file di contenuto come un <xref:System.IO.Stream> e ne descrive il tipo di contenuto.  
  
 Ad esempio, il codice seguente viene illustrato come utilizzare <xref:System.Windows.Application.GetContentStream%2A> per caricare un <xref:System.Windows.Controls.Page> file di contenuto e impostarlo come contenuto di un <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Durante la chiamata <xref:System.Windows.Application.GetContentStream%2A> consente di accedere al <xref:System.IO.Stream>, è necessario eseguire ulteriori operazioni di conversione al tipo della proprietà verrà impostato con. È invece possibile consentire [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] occuperà di apertura e la conversione di <xref:System.IO.Stream> caricando un file di risorse direttamente nella proprietà di un tipo tramite codice.  
  
 Nell'esempio seguente viene illustrato come caricare un <xref:System.Windows.Controls.Page> direttamente in un <xref:System.Windows.Controls.Frame> (`pageFrame`) mediante il codice.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 L'esempio seguente illustra il markup equivalente del precedente esempio.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>File del sito di origine  
 File di risorse hanno una relazione esplicita con gli assembly che vengono distribuiti insieme, come definito dal <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Talvolta, è tuttavia possibile che si debba stabilire una relazione implicita o inesistente tra un assembly e un file di dati dell'applicazione, come nei casi seguenti:  
  
-   Un file non esiste in fase di compilazione.  
  
-   I file richiesti dall'assembly non saranno noti fino alla fase di esecuzione.  
  
-   Si desidera avere la possibilità di aggiornare i file senza ricompilare l'assembly al quale sono associati.  
  
-   L'applicazione utilizza file di dati di grandi dimensioni, ad esempio audio e video, che devono essere scaricati dagli utenti unicamente su richiesta.  
  
 È possibile caricare questi tipi di file mediante l'utilizzo tradizionale [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] gli schemi, ad esempio gli schemi file:/// e http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 Tuttavia, gli schemi file:/// e http:// richiedono che l'applicazione abbia un livello di attendibilità totale. Se l'applicazione è un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] che è stato avviato da Internet o intranet e richiede solo il set di autorizzazioni consentite per le applicazioni avviate da tali percorsi, file separati possono essere caricati solo dal sito di origine (dell'applicazione posizione di avvio). I file sono noti come *sito di origine* file.  
  
 I file del sito di origine rappresentano l'unica opzione per le applicazioni parzialmente attendibili, benché non siano limitati a questo tipo di applicazione. È possibile che le applicazioni completamente attendibili debbano caricare file di dati dell'applicazione sconosciuti in fase di compilazione. Sebbene queste applicazioni possano utilizzare file:///, è probabile che i file di dati dell'applicazione vengano installati nella stessa cartella dell'assembly dell'applicazione o in una sottocartella di questo. In questo caso è più facile utilizzare un riferimento al sito di origine piuttosto che file:///, poiché l'utilizzo di file:/// richiede l'elaborazione del percorso completo del file.  
  
> [!NOTE]
>  Sito di origine file non vengono memorizzati nella cache con un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] su un computer client, mentre i file di contenuto. Di conseguenza, vengono scaricati solo se esplicitamente richiesto. Se un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] applicazione dispone di file multimediali di grandi dimensioni, configurarli come sito di origine indica l'avvio dell'applicazione iniziale è molto più veloce e i file vengono scaricati solo su richiesta.  
  
### <a name="configuring-site-of-origin-files"></a>Configurazione dei file del sito di origine  
 Se il sito di origine sconosciuto o non esistente in fase di compilazione, è necessario utilizzare distribuzione tradizionali meccanismi per assicurare che i file necessari sono disponibili in fase di esecuzione, incluso l'utilizzo di uno il `XCopy` programma della riga di comando o il [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Se si conosce in fase di compilazione i file si trovi nel sito di origine, ma si desidera evitare una dipendenza esplicita, è possibile aggiungere tali file in un [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] il progetto come `None` elemento. Come con i file di contenuto, è necessario impostare il [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` attributo per specificare che il file del sito di origine viene copiato in un percorso relativo all'assembly compilato, specificando il `Always` valore o `PreserveNewest` valore.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], si crea un sito di file di origine tramite l'aggiunta di un file a un progetto e impostare il relativo `Build Action` a `None`.  
  
 Quando il progetto viene compilato, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] copia i file specificati nella cartella di output di compilazione.  
  
### <a name="using-site-of-origin-files"></a>Uso dei file del sito di origine  
 Per caricare un file di origine del sito, è possibile chiamare il <xref:System.Windows.Application.GetRemoteStream%2A> metodo il <xref:System.Windows.Application> classe, passando un pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] che identifica il sito desiderato di file di origine. <xref:System.Windows.Application.GetRemoteStream%2A>Restituisce un <xref:System.Windows.Resources.StreamResourceInfo> oggetto, che espone il sito di file di origine come un <xref:System.IO.Stream> e ne descrive il tipo di contenuto.  
  
 Ad esempio, il codice seguente viene illustrato come utilizzare <xref:System.Windows.Application.GetRemoteStream%2A> per caricare un <xref:System.Windows.Controls.Page> sito di origine di file e impostarlo come contenuto di un <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Durante la chiamata <xref:System.Windows.Application.GetRemoteStream%2A> consente di accedere al <xref:System.IO.Stream>, è necessario eseguire ulteriori operazioni di conversione al tipo della proprietà verrà impostato con. È invece possibile consentire [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] occuperà di apertura e la conversione di <xref:System.IO.Stream> caricando un file di risorse direttamente nella proprietà di un tipo tramite codice.  
  
 Nell'esempio seguente viene illustrato come caricare un <xref:System.Windows.Controls.Page> direttamente in un <xref:System.Windows.Controls.Frame> (`pageFrame`) mediante il codice.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 L'esempio seguente illustra il markup equivalente del precedente esempio.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Ricompilazione in seguito alla modifica del tipo di compilazione  
 Dopo avere modificato il tipo di compilazione di un file di dati dell'applicazione, è necessario ricompilare l'intera applicazione affinché le modifiche vengano applicate. Se ci si limita a compilare l'applicazione, le modifiche non vengono applicate.  
  
## <a name="see-also"></a>Vedere anche  
 [URI di tipo pack in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
