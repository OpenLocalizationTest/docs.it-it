---
title: Generics (Guida per programmatori C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 0dc2fcee3903b80816c98bab47e2b9a2e5ef78b0
ms.openlocfilehash: de81058173b0985577474e8601aa84d4e83336a5
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="generics-c-programming-guide"></a>Generics (Guida per programmatori C#)
I generics sono stati aggiunti alla versione 2.0 del linguaggio C# e di Common Language Runtime (CLR). I generics introducono in .NET Framework il concetto dei parametri di tipo, che consentono di progettare classi e metodi che rinviano la specifica di uno o più tipi finché non si dichiara la classe o il metodo e si crea un'istanza dal codice client. Ad esempio, usando un parametro di tipo generico T è possibile scrivere un'unica classe che altro codice client può usare senza rischiare cast di runtime o operazioni di boxing, come illustrato di seguito:  
  
 [!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a>Panoramica sui generics  
  
-   Usare i tipi generici per ottimizzare il riutilizzo del codice, l'indipendenza dai tipi e le prestazioni.  
  
-   L'uso più comune dei generics consiste nel creare classi di raccolte.  
  
-   La libreria di classi .NET Framework contiene diverse nuove classi di raccolte generiche nello spazio dei nomi <xref:System.Collections.Generic>. Queste classi devono essere usate ogni volta che sia possibile al posto di classi come <xref:System.Collections.ArrayList> nello spazio dei nomi <xref:System.Collections>.  
  
-   È possibile creare interfacce, classi, metodi, eventi e delegati generici.  
  
-   Le classi generiche possono essere limitate in modo da abilitare l'accesso ai metodi per particolari tipi di dati.  
  
-   Le informazioni sui tipi usati in un tipo di dati generico possono essere ottenute usando la reflection in fase di esecuzione.  
  
## <a name="related-sections"></a>Sezioni correlate  
 Per ulteriori informazioni:  
  
-   [Introduzione ai generics](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [Vantaggi dei generics](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [Parametri di tipo generico](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [Vincoli sui parametri di tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [Classi generiche](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [Interfacce generiche](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [Metodi generici](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [Delegati generici](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [Differenze tra modelli C++ e generics C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [Generics e reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [Generics in fase di esecuzione](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [Generics nella libreria di classi .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a>Specifiche del linguaggio C#  
 Per altre informazioni, vedere la [specifica del linguaggio C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Collections.Generic>   
 [Guida per programmatori C#](../../../csharp/programming-guide/index.md)   
 [Tipi](../../../csharp/programming-guide/types/index.md)   
 [\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)   
 [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)

