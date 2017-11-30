---
title: Oggetti Attributes1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86fa2556e6b8fb82e31a7d4753354aa2dff627ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="attributes"></a><span data-ttu-id="435ab-102">Attributi</span><span class="sxs-lookup"><span data-stu-id="435ab-102">Attributes</span></span>
<span data-ttu-id="435ab-103"><xref:System.Attribute?displayProperty=nameWithType>è una classe di base utilizzata per definire gli attributi personalizzati.</span><span class="sxs-lookup"><span data-stu-id="435ab-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="435ab-104">Gli attributi sono le annotazioni possono essere aggiunti a elementi di programmazione, ad esempio assembly, tipi, membri e parametri.</span><span class="sxs-lookup"><span data-stu-id="435ab-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="435ab-105">Essi vengono archiviate nei metadati dell'assembly e accessibile in fase di esecuzione usando l'API di reflection.</span><span class="sxs-lookup"><span data-stu-id="435ab-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="435ab-106">Ad esempio, il Framework definisce il <xref:System.ObsoleteAttribute>, che può essere applicato a un tipo o un membro per indicare che il tipo o membro è stato deprecato.</span><span class="sxs-lookup"><span data-stu-id="435ab-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="435ab-107">Gli attributi possono avere uno o più proprietà che contengono dati aggiuntivi relativi all'attributo.</span><span class="sxs-lookup"><span data-stu-id="435ab-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="435ab-108">Ad esempio, `ObsoleteAttribute` potrebbe contenere informazioni aggiuntive sulla versione in cui un tipo o membro è stato deprecato e la descrizione delle nuove API sostituendo l'API obsoleta.</span><span class="sxs-lookup"><span data-stu-id="435ab-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="435ab-109">Alcune proprietà di un attributo deve essere specificata quando è applicato l'attributo.</span><span class="sxs-lookup"><span data-stu-id="435ab-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="435ab-110">Questi sono definiti per le proprietà obbligatorie o gli argomenti obbligatori, poiché vengono rappresentati come parametri posizionali di costruttore.</span><span class="sxs-lookup"><span data-stu-id="435ab-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="435ab-111">Ad esempio, il <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> proprietà del <xref:System.Diagnostics.ConditionalAttribute> è una proprietà obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="435ab-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="435ab-112">Proprietà che non è necessario specificare quando è applicato l'attributo sono dette proprietà facoltative (o gli argomenti facoltativi).</span><span class="sxs-lookup"><span data-stu-id="435ab-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="435ab-113">Sono rappresentati dalle proprietà impostabili.</span><span class="sxs-lookup"><span data-stu-id="435ab-113">They are represented by settable properties.</span></span> <span data-ttu-id="435ab-114">I compilatori forniscono una sintassi speciale per impostare queste proprietà quando viene applicato un attributo.</span><span class="sxs-lookup"><span data-stu-id="435ab-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="435ab-115">Ad esempio, il <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> proprietà rappresenta un argomento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="435ab-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="435ab-116">**✓ SI** denominare le classi di attributo personalizzato con il suffisso "Attributo".</span><span class="sxs-lookup"><span data-stu-id="435ab-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="435ab-117">**✓ SI** applicare il <xref:System.AttributeUsageAttribute> per gli attributi personalizzati.</span><span class="sxs-lookup"><span data-stu-id="435ab-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="435ab-118">**✓ SI** fornire proprietà impostabili per gli argomenti facoltativi.</span><span class="sxs-lookup"><span data-stu-id="435ab-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="435ab-119">**✓ SI** forniscono proprietà solo get per gli argomenti obbligatori.</span><span class="sxs-lookup"><span data-stu-id="435ab-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="435ab-120">**✓ SI** forniscono i parametri del costruttore per inizializzare le proprietà corrispondenti per gli argomenti obbligatori.</span><span class="sxs-lookup"><span data-stu-id="435ab-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="435ab-121">Ogni parametro deve avere lo stesso nome (anche se con maiuscole/minuscole) della proprietà corrispondente.</span><span class="sxs-lookup"><span data-stu-id="435ab-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="435ab-122">**X evitare** fornendo i parametri del costruttore per inizializzare le proprietà corrispondenti per gli argomenti facoltativi.</span><span class="sxs-lookup"><span data-stu-id="435ab-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="435ab-123">In altre parole, non dispone delle proprietà che è possibile impostare con un costruttore e un setter.</span><span class="sxs-lookup"><span data-stu-id="435ab-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="435ab-124">Questa linea guida rende molto esplicite gli argomenti sono facoltativi e che sono necessari e si evita due modi per eseguire la stessa operazione.</span><span class="sxs-lookup"><span data-stu-id="435ab-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="435ab-125">**X evitare** l'overload di costruttori di attributo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="435ab-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="435ab-126">Presenza di un solo costruttore chiaramente comunica all'utente cui gli argomenti sono obbligatori e facoltativi.</span><span class="sxs-lookup"><span data-stu-id="435ab-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="435ab-127">**✓ SI** bloccare le classi di attributo personalizzato, se possibile.</span><span class="sxs-lookup"><span data-stu-id="435ab-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="435ab-128">In questo modo la ricerca per l'attributo più velocemente.</span><span class="sxs-lookup"><span data-stu-id="435ab-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="435ab-129">*Parti © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*</span><span class="sxs-lookup"><span data-stu-id="435ab-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="435ab-130">*State ristampate dall'autorizzazione di Pearson Education, Inc. da [linee guida: convenzioni, idiomi e modelli per le librerie .NET di riutilizzabile, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina e Brad Abrams, pubblicato il 22 ottobre 2008 di Addison-Wesley Professional come parte della serie di sviluppo di Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="435ab-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435ab-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="435ab-131">See Also</span></span>  
 [<span data-ttu-id="435ab-132">Linee guida per la progettazione di Framework</span><span class="sxs-lookup"><span data-stu-id="435ab-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="435ab-133">Linee guida di utilizzo</span><span class="sxs-lookup"><span data-stu-id="435ab-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)