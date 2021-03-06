---
title: Numeri a virgola mobile
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3e8ac8b5a97c62bb173fba57ac8aeb26a1dad42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="floating-point-numbers"></a>Numeri a virgola mobile
In questo argomento vengono descritti alcuni dei problemi rilevati di frequente dagli sviluppatori con l'uso di numeri a virgola mobile in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Questi problemi sono causati dalla modalità che i computer archiviano numeri a virgola mobile e non sono specifici di un determinato provider, ad esempio <xref:System.Data.SqlClient> o <xref:System.Data.OracleClient>.  
  
 I numeri a virgola mobile in genere non hanno una rappresentazione binaria esatta Al contrario, il computer archivia un'approssimazione del numero. In momenti differenti è possibile che vengano usati numeri diversi di cifre binarie per rappresentare il numero. Quando un numero a virgola mobile viene convertito da una rappresentazione a un'altra, le cifre meno significative di tale numero possono variare leggermente. La conversione si verifica un genere quando viene eseguito il cast di un numero da un tipo a un altro. La variazione si verifica se la conversione avviene all'interno di un database, tra tipi che rappresentano valori del database oppure tra tipi. A causa di queste modifiche, i numeri che logicamente sarebbero uguali potrebbero presentare modifiche nelle cifre meno significative, generando in questo modo valori diversi. Il numero di cifre di precisione nel numero può essere maggiore o minore del previsto. Quando viene formattato come stringa, il numero potrebbe non presentare il valore previsto.  
  
 Per minimizzare questi effetti, è necessario usare la corrispondenza più vicina disponibile tra tipi numerici. Se ad esempio si usa [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], il valore numerico esatto può variare se si converte un valore Transact-SQL di tipo reale in un valore di tipo float. Nel [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], la conversione un <xref:System.Single> per un <xref:System.Double> può anche produrre risultati imprevisti. In entrambi questi casi, una strategia efficace consiste nel fare in modo che tutti i valori dell'applicazione utilizzino lo stesso tipo numerico. È anche possibile usare un tipo decimale a precisione fissa o eseguire il cast dei numeri a virgola mobile in un tipo decimale a precisione fissa prima di usarli.  
  
 Per risolvere i problemi con il confronto di uguaglianza, è consigliabile scrivere il codice dell'applicazione in modo che le variazioni delle cifre meno significative vengano ignorate. Ad esempio, anziché eseguire un confronto per verificare l'uguaglianza tra due numeri, sottrarre un numero dall'altro. Se la differenza rientra in un margine accettabile di arrotondamento, l'applicazione può considerare i numeri come se fossero identici.  
  
## <a name="see-also"></a>Vedere anche  
 [Causa della possibile perdita di precisione dei numeri a virgola mobile](http://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](http://go.microsoft.com/fwlink/?LinkId=217917)
