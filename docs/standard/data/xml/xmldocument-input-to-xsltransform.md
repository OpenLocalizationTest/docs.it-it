---
title: Input di XmlDocument in XslTransform
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 554faffb676337f8846eb6ba24152d77793b8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="xmldocument-input-to-xsltransform"></a>Input di XmlDocument in XslTransform
La classe <xref:System.Xml.XmlDocument> fornisce funzionalità di modifica per un documento XML. Se è necessario modificare il codice XML prima di inviarlo al metodo <xref:System.Xml.Xsl.XslTransform.Transform%2A>, caricare il codice XML in un <xref:System.Xml.XmlDocument>, modificarlo e inviarlo al <xref:System.Xml.Xsl.XslTransform>.  
  
> [!NOTE]
>  La classe <xref:System.Xml.Xsl.XslTransform> è obsoleta in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. È possibile eseguire le trasformazioni XSLT (Extensible Stylesheet Language for Transformations) usando la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Vedere [utilizzando la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) e [la migrazione dalla classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) per ulteriori informazioni.  
  
 <xref:System.Xml.XmlDocument> implementa l'interfaccia <xref:System.Xml.XPath.IXPathNavigable>, quindi il documento può essere passato al metodo <xref:System.Xml.Xsl.XslTransform.Transform%2A> dopo la modifica.  
  
 Grazie alla funzionalità di modifica di <xref:System.Xml.XmlDocument>, usando la classe <xref:System.Xml.XmlDocument> come input per una trasformazione si ottengono prestazioni inferiori rispetto all'utilizzo di un <xref:System.Xml.XPath.XPathDocument> per le trasformazioni XSLT (Extensible Stylesheet Language for Transformations), in quanto <xref:System.Xml.XPath.XPathDocument> è ottimizzato per le query XPath (XML Path Language) per l'archiviazione interna.  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come fornire un <xref:System.Xml.XmlDocument> al metodo <xref:System.Xml.Xsl.XslTransform>, con l'output inviato a un <xref:System.Xml.XmlReader>.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Xml.XmlDocument>  
 [Trasformazioni XSLT con la classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Classe XslTransform implementa il processore XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [XPathNavigator nelle trasformazioni](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [XPathNodeIterator nelle trasformazioni](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Input di XPathDocument in XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Input di XmlDataDocument in XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
