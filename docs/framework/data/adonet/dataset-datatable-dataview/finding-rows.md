---
title: Ricerca di righe
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
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 96a65761cb6ddf31c0bb4c14077aed37336183f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="finding-rows"></a>Ricerca di righe
È possibile eseguire ricerche di righe in base ai relativi valori della chiave di ordinamento usando i metodi <xref:System.Data.DataView.Find%2A> e <xref:System.Data.DataView.FindRows%2A> del tipo <xref:System.Data.DataView>. La distinzione maiuscole/minuscole della ricerca i valori di **trovare** e **FindRows** metodi è determinato dal **CaseSensitive** proprietà dell'oggetto sottostante <xref:System.Data.DataTable>. Per restituire un risultato, è necessario che i valori di ricerca corrispondano interamente ai valori della chiave di ordinamento esistenti.  
  
 Il **trovare** metodo restituisce un intero con indice di <xref:System.Data.DataRowView> che corrisponde ai criteri di ricerca. Se più di una riga corrisponde ai criteri di ricerca, solo l'indice della prima corrispondenza **DataRowView** viene restituito. Se non vengono trovate corrispondenze, **trovare** restituisce -1.  
  
 Per restituire i risultati di ricerca che corrispondono a più righe, utilizzare il **FindRows** metodo. **FindRows** funziona come il **trovare** metodo, ad eccezione del fatto che restituisca un **DataRowView** matrice che fa riferimento a tutte le righe corrispondenti nel **DataView**. Se viene trovata alcuna corrispondenza, il **DataRowView** matrice sarà vuota.  
  
 Utilizzare il **trovare** o **FindRows** metodi è necessario specificare un ordinamento ordinare impostando **ApplyDefaultSort** a **true** o tramite il **Ordinamento** proprietà. Se non viene specificato alcun ordinamento, verrà generata un'eccezione.  
  
 Il **trovare** e **FindRows** metodi accettano una matrice di valori come input, la cui lunghezza corrisponde al numero di colonne dell'ordinamento. In caso di ordinamento di una singola colonna, è possibile passare un unico valore. In caso di ordinamenti contenenti più colonne, viene passata una matrice di oggetti. Si noti che per l'ordinamento su più colonne, i valori della matrice di oggetti devono corrispondere all'ordine delle colonne specificate nel **ordinamento** proprietà del **DataView**.  
  
 Nell'esempio di codice riportato di seguito viene illustrato il **trovare** chiamata del metodo per un **DataView** con un ordinamento singola colonna.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 Se il **ordinamento** proprietà sono specificate più colonne, è necessario passare una matrice di oggetti con i valori di ricerca per ogni colonna nell'ordine specificato per il **ordinamento** proprietà, come nell'esempio di codice seguente.  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Provider gestiti ADO.NET e Centro per sviluppatori di set di dati](http://go.microsoft.com/fwlink/?LinkId=217917)
