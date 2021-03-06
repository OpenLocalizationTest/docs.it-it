---
title: "Funzionalità del linguaggio XAML 2009"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 6299a29cb79650eb59df3f198c3ea3fcd49d0076
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-2009-language-features"></a>Funzionalità del linguaggio XAML 2009
XAML 2009 è il termine abbreviato per le nuove funzionalità del linguaggio XAML che estendono la specifica del linguaggio XAML esistente. XAML 2009 introduce varie nuove direttive e costrutti. Sono incluse[x:Arguments Directive](../../../docs/framework/xaml-services/x-arguments-directive.md), [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md), [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md), [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)e i tipi nativi per primitive di linguaggio comuni, ad esempio `x:Char`.  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Supporto XAML 2009 in WPF e Visual Studio  
 In WPF è possibile usare le funzionalità di XAML 2009, ma solo per il codice XAML non compilato dal markup WPF. Il codice XAML compilato dal markup e il modulo BAML di XAML non supportano attualmente le parole chiave e le funzionalità di XAML 2009.  
  
 Si noti che per le tecniche esistenti per il caricamento di XAML separato in WPF esistono anche possibili restrizioni ai tipi CLR e al sistema di tipi che sono più restrittive rispetto a quelle per XAML compilato dal markup. Per altre informazioni vedere [Sicurezza (WPF)](../../../docs/framework/wpf/security-wpf.md) o [Strategia di sicurezza di WPF - Sicurezza della piattaforma](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 introduce anche funzionalità aggiuntive che modificano i costrutti XAML 2006 precedenti o che modificano i moduli del markup di base.  
  
### <a name="xkey-as-an-object-element"></a>x:Key come un elemento oggetto  
 XAML 2009 può supportare `x:Key` come un oggetto (un elemento proprietà con valore dell'elemento oggetto). Tuttavia, XAML 2006 supportava solo `x:Key` come attributo. Vedere la sezione "XAML 2009" di [x:Key Directive](../../../docs/framework/xaml-services/x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns su elementi proprietà  
 XAML 2009 può supportare definizioni (xmlns) dello spazio dei nomi XAML su elementi proprietà. Tuttavia, XAML 2006 supporta solo definizioni xmlns su elementi oggetto.  
  
### <a name="event-attributes"></a>Attributi dell'evento  
 Per gli attributi supportati dagli eventi, XAML 2006 presuppone che sia coinvolta la compilazione del markup e invia gli eventi alla compilazione del markup. XAML 2009 supporta un modulo di markup che assomiglia a un'estensione di markup, che rinvia il collegamento di eventi fino all'analisi e al caricamento in fase di esecuzione di XAML. Le applicazioni WPF e gli scenari XAML per l'interfaccia utente tuttavia in genere non usano questa funzionalità. WPF e la relativa implementazione XAML 2006 usano la combinazione del collegamento del gestore eventi per eventi indirizzati, definiti al livello <xref:System.Windows.UIElement> , e il passaggio del compilatore di markup per la maggior parte dell'elaborazione di attributi evento. Il compilatore di markup preelabora anche gli attributi dell'evento trovati in XAML in cui le operazioni di compilazione dichiarano di usare il compilatore di markup.  
  
## <a name="see-also"></a>Vedere anche  
 [Cenni preliminari su XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
