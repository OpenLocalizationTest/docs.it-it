---
title: 'Procedura: ordinare i risultati di query utilizzando LINQ (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c880924b8091d3af28f5353fec2083d635bb4078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a>Procedura: ordinare i risultati di query utilizzando LINQ (Visual Basic)
Language-Integrated Query (LINQ) rende più semplice accedere alle informazioni di database ed eseguire query.  
  
 Nell'esempio seguente viene illustrato come creare una nuova applicazione che esegue query su un database di SQL Server e ordina i risultati in base a più campi utilizzando la `Order By` clausola. È possibile ordine crescente o decrescente dell'ordinamento per ogni campo. Per ulteriori informazioni, vedere [clausola Order By](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Gli esempi in questo argomento usano il database di esempio Northwind. Se non si dispone di esempio Northwind nel computer di sviluppo, è possibile scaricarlo dal [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) sito Web. Per istruzioni, vedere [download dei database di esempio](https://msdn.microsoft.com/library/bb399411).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Per creare una connessione a un database  
  
1.  In Visual Studio, aprire **Esplora Server**/**Esplora Database** facendo **Esplora Server**/**Database Esplora** sul **vista** menu.  
  
2.  Fare doppio clic su **connessioni dati** in **Esplora Server**/**Esplora Database** e quindi fare clic su **Aggiungi connessione**.  
  
3.  Specificare una connessione valida al database di esempio Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Per aggiungere un progetto che contiene un file LINQ to SQL  
  
1.  In Visual Studio scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**. Selezionare Visual Basic **Windows Forms Application** come tipo di progetto.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**. Selezionare il **classi LINQ to SQL** modello di elemento.  
  
3.  Denominare il file `northwind.dbml`. Fare clic su **Aggiungi**. Il Object Relational Designer (O/R Designer) è aperto per il file Northwind. dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Per aggiungere le tabelle di eseguire query O/R Designer  
  
1.  In **Esplora Server**/**Esplora Database**, espandere la connessione al database Northwind. Espandere il **tabelle** cartella.  
  
     Se è stato chiuso O/R Designer, è possibile riaprirlo facendo doppio clic sul file Northwind. dbml aggiunto in precedenza.  
  
2.  Fare clic sulla tabella di clienti e trascinarlo nel riquadro sinistro della finestra di progettazione. Fare clic sulla tabella Orders e trascinarlo nel riquadro sinistro della finestra di progettazione.  
  
     La finestra di progettazione crea nuovi `Customer` e `Order` oggetti per il progetto. Si noti che la finestra di progettazione automaticamente rileva le relazioni tra le tabelle e crea le proprietà per gli oggetti correlati figlio. Ad esempio, IntelliSense visualizzerà che il `Customer` oggetto ha un `Orders` proprietà per tutti gli ordini relativi a quel cliente.  
  
3.  Salvare le modifiche e chiudere la finestra di progettazione.  
  
4.  Salvare il progetto.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Per aggiungere il codice per eseguire query sul database e visualizzare i risultati  
  
1.  Dal **della casella degli strumenti**, trascinare un <xref:System.Windows.Forms.DataGridView> controllo Windows Form predefinito per il progetto, Form1.  
  
2.  Fare doppio clic su Form1 per aggiungere il codice per il `Load` eventi del modulo.  
  
3.  Quando si aggiungono tabelle alla finestra di Progettazione relazionale, la finestra di progettazione aggiunge un <xref:System.Data.Linq.DataContext> oggetto al progetto. Questo oggetto contiene il codice che è necessario disporre per accedere a tali tabelle e di accedere ai singoli oggetti e raccolte per ogni tabella. Il <xref:System.Data.Linq.DataContext> oggetto per il progetto viene denominato in base al nome del file. dbml. Per questo progetto, il <xref:System.Data.Linq.DataContext> oggetto è denominato `northwindDataContext`.  
  
     È possibile creare un'istanza di <xref:System.Data.Linq.DataContext> nel codice e query vengono specificate le tabelle da O/R Designer.  
  
     Aggiungere il codice seguente per il `Load` evento per eseguire query su tabelle che vengono esposti come proprietà del contesto dati e ordinare i risultati. La query ordina i risultati in base al numero di ordini cliente, in ordine decrescente. I clienti che hanno lo stesso numero di ordini vengono ordinati in base al nome della società in senso crescente (impostazione predefinita).  
  
     [!code-vb[VbLINQToSQLHowTos#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-sort-query-results-by-using-linq_1.vb)]  
  
4.  Premere F5 per eseguire il progetto e visualizzare i risultati.  
  
## <a name="see-also"></a>Vedere anche  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Query](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
 [Metodi DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
