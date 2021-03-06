---
title: Funzioni inline (F#)
description: 'Informazioni sull''utilizzo di F # funzioni inline sono integrate direttamente nel codice chiamante.'
keywords: visual f#, f#, programmazione funzionale
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a>Funzioni inline

*Funzioni inline* sono funzioni che vengono integrate direttamente nel codice chiamante.


## <a name="using-inline-functions"></a>Utilizzo delle funzioni Inline
Quando si utilizzano parametri di tipo statico, le funzioni che sono parametri dai parametri di tipo devono essere inline. In questo modo si garantisce che il compilatore può risolvere questi parametri di tipo. Quando si utilizzano parametri di tipo generico normale, non è non implica tale restrizione.

Diverso da abilitare l'utilizzo di vincoli di membro, funzioni inline possono essere utili per l'ottimizzazione di codice. Tuttavia, utilizzo eccessivo di funzioni inline può provocare il codice meno resistente alle modifiche apportate alle ottimizzazioni del compilatore e l'implementazione di funzioni della libreria. Per questo motivo, è consigliabile non utilizzare le funzioni inline per l'ottimizzazione a meno che non si sono tentato di altre tecniche di ottimizzazione. Rendere inline una funzione o metodo talvolta possono migliorare le prestazioni, ma non è sempre il caso. Pertanto, si devono usare anche le misurazioni delle prestazioni per verificare che effettua una funzione inline in realtà hanno un effetto positivo.

Il `inline` modificatore può essere applicato a funzioni al livello superiore, a livello di modulo o a livello di metodo in una classe.

Esempio di codice seguente viene illustrata una funzione inline a livello superiore, un metodo di istanza inline e un metodo statico inline.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a>Funzioni inline e l'inferenza del tipo
La presenza di `inline` interessa l'inferenza del tipo. Infatti, funzioni inline possono avere risolti staticamente parametri di tipo, mentre non le funzioni non inline. Esempio di codice seguente viene illustrato un caso in cui `inline` è utile perché si sta usando una funzione che ha un parametro di tipo risolti staticamente il `float` operatore di conversione.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

Senza il `inline` modificatore, l'inferenza del tipo impone la funzione per accettare un tipo specifico, in questo caso `int`. Ma con il `inline` modificatore, la funzione viene dedotto anche avere un parametro di tipo risolti staticamente. Con il `inline` modificatore, il tipo viene dedotto come riportato di seguito:

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

Ciò significa che la funzione accetta qualsiasi tipo che supporta una conversione **float**.


## <a name="see-also"></a>Vedere anche
[Funzioni](index.md)

[Vincoli](../generics/constraints.md)

[Parametri di tipo risolti staticamente](../generics/statically-resolved-type-parameters.md)
