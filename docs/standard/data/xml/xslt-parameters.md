---
title: Parametri XSLT
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
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e66d98501bb0bd3a5d5cd5eacc0b09405c158522
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-parameters"></a>Parametri XSLT
I parametri XSLT vengono aggiunti all'elenco <xref:System.Xml.Xsl.XsltArgumentList> mediante il metodo <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>. Un nome qualificato e un URI dello spazio dei nomi sono associati all'oggetto parametro in quel momento.  
  
### <a name="to-use-an-xslt-parameter"></a>Per usare un parametro XSLT  
  
1.  Creare un oggetto <xref:System.Xml.Xsl.XsltArgumentList> e aggiungere il parametro usando il metodo <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2.  Richiamare il parametro dal foglio di stile.  
  
3.  Passare l'oggetto <xref:System.Xml.Xsl.XsltArgumentList> al metodo <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="parameter-types"></a>Tipi di parametro  
 L'oggetto parametro dovrebbe corrispondere a un tipo W3C. Nella tabella seguente sono illustrati i tipi W3C corrispondenti e le classi Microsoft .NET equivalenti (tipo) e viene indicato se il tipo W3C è un tipo XPath o XSLT.  
  
|Tipo W3C|Classe .NET equivalente (tipo)|Tipo XPath o XSLT|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|XPath|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|XPath|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|XPath|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSLT|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XPath|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **XPathNavigator]**|XPath|  
  
 *Questo è equivalente a un set di nodi che contiene un unico nodo.  
  
 Se l'oggetto parametro non appartiene a una delle classi indicate sopra, viene convertito in base alle seguenti regole. I tipi numerici CLR vengono convertiti nel tipo <xref:System.Double>. Il tipo <xref:System.DateTime> viene convertito in <xref:System.String> e i tipi <xref:System.Xml.XPath.IXPathNavigable> in <xref:System.Xml.XPath.XPathNavigator>. **XPathNavigator []** viene convertito in <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Per tutti gli altri tipi verrà generato un errore.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente il metodo <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> viene usato per creare un parametro per contenere una data di sconto calcolata. La data di sconto è calcolata dopo 20 giorni dalla data dell'ordine.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Input  
  
##### <a name="orderxml"></a>order.xml  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a>discount.xsl  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a>Output  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Trasformazioni XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
