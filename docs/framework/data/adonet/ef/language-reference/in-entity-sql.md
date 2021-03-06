---
title: IN (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 553b2037ef9b1eead3a3f4745d0cb6fdfcde27ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2017
---
# <a name="in-entity-sql"></a>IN (Entity SQL)
Determina se un valore corrisponde a qualsiasi valore in una raccolta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Argomenti  
 `value`  
 Qualsiasi espressione valida che restituisce il valore di cui trovare la corrispondenza.  
  
 [ NOT ]  
 Specifica la negazione del risultato `Boolean` di IN.  
  
 `expression`  
 Qualsiasi espressione valida che restituisce la raccolta da testare per trovare una corrispondenza. Tutte le espressioni devono essere dello stesso tipo o di un tipo di base o derivato comune di `value`.  
  
## <a name="return-value"></a>Valore restituito  
 `true` se il valore viene trovato nella raccolta; null se il valore è null o se la raccolta è null; in caso contrario `false`. L'utilizzo di NOT IN consente di negare i risultati di IN.  
  
## <a name="example"></a>Esempio  
 Nella query Entity SQL seguente viene usato l'operatore IN per determinare se un valore corrisponde a qualsiasi valore in una raccolta. La query è basata sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1.  Seguire la procedura indicata in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Passare la query seguente come argomento al metodo `ExecuteStructuralTypeQuery` :  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento a Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
