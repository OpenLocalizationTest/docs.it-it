---
title: "Classe e proprietà dell'eccezione"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 253a9846e484aa4e54c3433b0bbc8623519bbb7e
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2017
---
# <a name="exception-class-and-properties"></a>Classe e proprietà dell'eccezione

La classe <xref:System.Exception> è la classe di base da cui vengono ereditate le eccezioni. Ad esempio, la gerarchia della classe <xref:System.InvalidCastException> è illustrata di seguito:

```
Object
  Exception
    SystemException
       InvalidCastException
```

La classe <xref:System.Exception> include le proprietà seguenti che facilitano la comprensione di un'eccezione.

| Nome proprietà | Descrizione |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary> contenente dati arbitrari in coppie chiave-valore. |
| <xref:System.Exception.HelpLink> | Può contenere un URL (o URN) di un file della Guida che offre informazioni dettagliate sulla causa di un'eccezione. |
| <xref:System.Exception.InnerException> | Questa proprietà può essere usata per creare e mantenere una serie di eccezioni durante la gestione delle eccezioni. È possibile usarla per creare una nuova eccezione contenente le eccezioni rilevate in precedenza. L'eccezione originale può essere acquisita dalla seconda eccezione nella proprietà <xref:System.Exception.InnerException>, consentendo al codice che gestisce la seconda eccezione di esaminare le informazioni aggiuntive. Ad esempio, si supponga di avere un metodo che riceve un argomento non formattato correttamente.  Il codice tenta di leggere l'argomento, ma viene generata un'eccezione. Il metodo rileva l'eccezione e genera <xref:System.FormatException>. Per migliorare la capacità del chiamante di determinare il motivo per il quale viene generata un'eccezione, è a volte utile che un metodo rilevi un'eccezione generata da una routine di supporto e quindi generi un'eccezione più indicativa dell'errore che si è verificato. Sarà possibile creare un'eccezione nuova e più significativa in cui il riferimento all'eccezione interna può essere impostato sull'eccezione originale. Questa eccezione più significativa può quindi essere inviata al chiamante. Si noti che con questa funzionalità è possibile creare una serie di eccezioni collegate che termina con l'eccezione che è stata generata per prima. |
| <xref:System.Exception.Message> | Offre informazioni dettagliate sulla causa di un'eccezione.
| <xref:System.Exception.Source> | Ottiene o imposta il nome dell'oggetto o dell'applicazione che ha generato l'errore. |
| <xref:System.Exception.StackTrace>| Contiene un'analisi dello stack che può essere usata per determinare dove si è verificato un errore. L'analisi dello stack include il nome del file di origine e il numero di riga del programma, se sono disponibili informazioni di debug. |

La maggior parte delle classi che ereditano da <xref:System.Exception> non implementano membri aggiuntivi né offrono funzionalità supplementari, ma si limitano a ereditare da <xref:System.Exception>. Per questa ragione, le informazioni più importanti per un'eccezione si trovano nella gerarchia delle classi delle eccezioni, nel nome dell'eccezione e nelle informazioni contenute nell'eccezione.

Si consiglia di generare e intercettare solo oggetti che derivano da <xref:System.Exception>, ma è possibile generare qualsiasi oggetto che deriva dalla <xref:System.Object> classe come un'eccezione. Si noti che non tutti i linguaggi supportano la generazione e il rilevamento degli oggetti che non derivano da <xref:System.Exception>.
  
## <a name="see-also"></a>Vedere anche  
[Eccezioni](index.md)
