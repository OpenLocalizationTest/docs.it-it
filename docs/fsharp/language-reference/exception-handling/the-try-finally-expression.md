---
title: 'Eccezioni: espressione try...finally (F#)'
description: 'Informazioni su come F # '' try... finally'' espressione consente di eseguire il codice di pulitura, anche se un blocco di codice genera un''eccezione.'
keywords: visual f#, f#, programmazione funzionale
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: af06b20c-8d87-4496-a0aa-6fdfe8b3a786
ms.openlocfilehash: 2e2445c42bf8129ea81beef56cb725ac0e37d202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-tryfinally-expression"></a>Eccezioni: espressione try...finally

Il `try...finally` espressione consente di eseguire il codice di pulitura, anche se un blocco di codice genera un'eccezione.


## <a name="syntax"></a>Sintassi

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Note
Il `try...finally` espressione può essere utilizzata per eseguire il codice in *expression2* nella sintassi precedente, indipendentemente dal fatto che viene generata un'eccezione durante l'esecuzione di *expression1*.

Il tipo di *expression2* non contribuiscono al valore dell'intera espressione; il tipo restituito quando non si verifica un'eccezione è l'ultimo valore in *expression1*. Quando si verifica un'eccezione, viene restituito alcun valore e il flusso di controllo trasferisce al gestore di eccezioni corrispondente successivo lo stack di chiamate. Se non viene trovato alcun gestore eccezioni, il programma termina. Prima che venga eseguito il codice in un gestore corrispondente o il programma termina, il codice di `finally` ramo viene eseguito.

Il codice seguente illustra l'uso del `try...finally` espressione.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

L'output alla console è come indicato di seguito.

```
Closing stream
Exception handled.
```

Come si vede dall'output, il flusso è stato chiuso prima che è stata gestita l'eccezione esterna e il file `test.txt` contiene il testo `test1`, indica che i buffer sono stati scaricati e scritti su disco, anche se l'eccezione ha trasferito controllo al gestore dell'eccezione esterna.

Si noti che il `try...with` costrutto è distinto dal costrutto di `try...finally` costruire. Pertanto, se il codice richiede sia un `with` blocco e un `finally` blocco, è necessario nidificare i due costrutti, come nell'esempio di codice seguente.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

Nel contesto di espressioni di calcolo, incluse le espressioni di sequenza e flussi di lavoro asincroni **try... finally** espressioni possono avere un'implementazione personalizzata. Per ulteriori informazioni, vedere [espressioni di calcolo](../computation-expressions.md).


## <a name="see-also"></a>Vedere anche
[Gestione delle eccezioni](index.md)

[Eccezioni: espressione `try...with`](the-try-with-expression.md)
