---
title: "Più operazioni di copia di massa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7db77dcd58e48927e8dac9bee82f7f14cdacf196
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="multiple-bulk-copy-operations"></a>Più operazioni di copia di massa
È possibile eseguire più operazioni di copia di massa usando una singola istanza di una classe <xref:System.Data.SqlClient.SqlBulkCopy>. Se i parametri delle operazioni cambiano tra le copie (ad esempio, il nome della tabella di destinazione), è necessario aggiornarli prima delle chiamate successive a qualsiasi il **WriteToServer** metodi, come illustrato nell'esempio seguente. Se non vengono modificati in modo esplicito, tutti i valori delle proprietà rimangono identici a quelli dell'operazione di copia di massa precedente per una determinata istanza.  
  
> [!NOTE]
>  L'esecuzione di più operazioni di copia di massa con la stessa istanza di <xref:System.Data.SqlClient.SqlBulkCopy> è generalmente più efficace rispetto all'utilizzo di un'istanza distinta per ogni operazione.  
  
 Se si eseguono diverse operazioni di copia di massa usando lo stesso oggetto <xref:System.Data.SqlClient.SqlBulkCopy>, non vi sono restrizioni sulla corrispondenza o meno tra le informazioni di origine o di destinazione di ciascuna operazione. Tuttavia, è necessario verificare che le informazioni di associazione della colonna siano impostate correttamente ogni volta che si scrive sul server.  
  
> [!IMPORTANT]
>  Questo esempio non verrà eseguito a meno che non state create le tabelle di lavoro come descritto in [l'installazione di esempio copia Bulk](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Questo codice viene fornito per illustrare la sintassi per l'utilizzo di **SqlBulkCopy** solo. Se la tabella di origine e quella di destinazione risiedono nella stessa istanza di SQL Server, per copiare i dati è più semplice e rapido usare un'istruzione `INSERT … SELECT` Transact-SQL.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Operazioni di copia bulk in SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](http://go.microsoft.com/fwlink/?LinkId=217917)
