---
title: Navigazione del set di nodi con XPathNavigator
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ac0135227599d6a72813bcf57b209705545da66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="node-set-navigation-using-xpathnavigator"></a>Navigazione del set di nodi con XPathNavigator
È possibile navigare nei nodi in un oggetto <xref:System.Xml.XPath.XPathDocument> o <xref:System.Xml.XmlDocument> usando i metodi di navigazione del set di nodi della classe <xref:System.Xml.XPath.XPathNavigator>. È possibile navigare in tutti i nodi o un set di nodi selezionato restituito da uno dei metodi di selezione della classe <xref:System.Xml.XPath.XPathNavigator>.  
  
## <a name="element-node-set-navigation"></a>Navigazione del set di nodi di tipo element  
 La classe <xref:System.Xml.XPath.XPathNavigator> fornisce diversi metodi usati per navigare nei nodi di tipo element. Nella tabella seguente vengono illustrati i metodi di navigazione disponibili e viene fornita una descrizione delle modalità di spostamento. Non sono inclusi i metodi usati per esplorare i nodi Attribute e Namespace.  
  
 Per ulteriori informazioni sulla selezione di nodi in un <xref:System.Xml.XPath.XPathNavigator> , vedere [selezione, valutazione e corrispondenza di dati XML con XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md). Per ulteriori informazioni sullo spostamento di nodi attribute e namespace, vedere [attributo e Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md).  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> nella stessa posizione dell'oggetto <xref:System.Xml.XPath.XPathNavigator> specificato.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> su un nodo figlio del nodo corrente.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> sul primo nodo di pari livello del nodo corrente.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> sul primo nodo figlio del nodo corrente.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> sull'elemento specificato in base all'ordine con cui è riportato nel documento.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> sul nodo che dispone di un attributo di tipo `ID`, il cui valore corrisponde alla stringa <xref:System.String> indicata.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> sul successivo nodo di pari livello del nodo corrente.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> sul nodo padre del nodo corrente.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> sul precedente nodo di pari livello del nodo corrente.|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|Sposta il tipo <xref:System.Xml.XPath.XPathNavigator> sul nodo radice del documento XML.|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a>Navigazione dei nodi di tipo Comment e Processing Instruction  
 I seguenti metodi della classe <xref:System.Xml.XPath.XPathNavigator> sono validi per passare ai commenti o alle istruzioni di elaborazione da altri nodi all'interno un documento XML.  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Elaborazione di dati XML con il modello di dati XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Attributo Namespace navigazione dei nodi e con XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [Estrazione di dati XML con XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [Accesso sicuro ai dati XML tipizzati con XPathNavigator](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
