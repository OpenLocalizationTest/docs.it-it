---
title: "Annullare le attività asincrone rimanenti dopo che ne è completa (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 698ccf5901a77438368b9bf768b88ca6f90fdcbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Annullare le attività asincrone rimanenti dopo che ne è completa (Visual Basic)
È possibile usare il metodo <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> insieme a <xref:System.Threading.CancellationToken> per annullare tutte le attività rimanenti dopo il completamento di un'attività. Il metodo `WhenAny` accetta un argomento che rappresenta una raccolta di attività. Il metodo avvia tutte le attività e restituisce una singola attività. La singola attività è completa quando una qualsiasi attività nella raccolta è completata.  
  
 Questo esempio illustra come usare un token di annullamento in combinazione con `WhenAny` per terminare il completamento della prima attività della raccolta di attività e annullare le rimanenti attività. Ogni attività scarica il contenuto di un sito Web. L'esempio visualizza la lunghezza del contenuto del primo download da completare e annulla gli altri download.  
  
> [!NOTE]
>  Per eseguire gli esempi, è necessario avere installato Visual Studio 2012 o versioni successive e .NET Framework 4.5 o versioni successive nel computer.  
  
## <a name="downloading-the-example"></a>Download dell'esempio  
 È possibile scaricare il progetto completo di Windows Presentation Foundation (WPF) da [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (Esempio di attività asincrona: ottimizzazione dell'applicazione) e seguire la procedura seguente.  
  
1.  Decomprimere il file scaricato e quindi avviare Visual Studio.  
  
2.  Nella barra dei menu scegliere **File**, **Apri**, **Progetto/Soluzione**.  
  
3.  Nel **Apri progetto** la finestra di dialogo, aprire la cartella che contiene il codice di esempio che è stato decompresso e quindi aprire il file di soluzione (sln) per AsyncFineTuningVB.  
  
4.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **CancelAfterOneTask** e scegliere **Imposta come progetto di avvio**.  
  
5.  Premere F5 per eseguire il progetto.  
  
     Premere CTRL + F5 per eseguire il progetto senza il debug.  
  
6.  Eseguire il programma più volte per verificare che diversi download terminino prima.  
  
 Se non si desidera scaricare il progetto, è possibile esaminare il file. Xaml. vb alla fine di questo argomento.  
  
## <a name="building-the-example"></a>Compilazione dell'esempio  
 Nell'esempio di questo argomento viene aggiunto al progetto che è stato sviluppato in [annullare un'attività asincrona o un elenco di attività](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) per annullare un elenco di attività. L'esempio usa la stessa interfaccia utente, sebbene il pulsante **Annulla** non viene usato in modo esplicito.  
  
 Per compilare l'esempio passo a passo, seguire le istruzioni nella sezione "Download dell'esempio", ma scegliere **CancelAListOfTasks** come **progetto di avvio**. Aggiungere al progetto le modifiche illustrate in questo argomento.  
  
 Nel file del file di **CancelAListOfTasks** del progetto, avviare la transizione spostando le fasi di elaborazione per ogni sito Web del ciclo in `AccessTheWebAsync` al metodo asincrono seguenti.  
  
```vb  
' ***Bundle the processing steps for a website into one async method.  
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
    ' GetAsync returns a Task(Of HttpResponseMessage).   
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
    ' Retrieve the website contents from the HttpResponseMessage.  
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
    Return urlContents.Length  
End Function  
```  
  
 In `AccessTheWebAsync`, questo esempio usa una query, il metodo <xref:System.Linq.Enumerable.ToArray%2A> e il metodo `WhenAny` per creare e avviare una matrice di attività. L'applicazione di `WhenAny` alla matrice restituisce una singola attività che, quando attesa, restituisce la prima attività per raggiungere il completamento della matrice di attività.  
  
 Modificare `AccessTheWebAsync` nel modo seguente. Gli asterischi contrassegnano le modifiche nel file del codice.  
  
1.  Aggiungere un commento o eliminare il ciclo.  
  
2.  Creare una query che, quando eseguita, produce una raccolta di attività generiche. Ogni chiamata a `ProcessURLAsync` restituisce un oggetto <xref:System.Threading.Tasks.Task%601> dove `TResult` è un numero intero.  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  Chiamare `ToArray` per eseguire la query e avviare le attività. L'applicazione del metodo `WhenAny` nel passaggio successivo esegue la query e avvia le attività senza usare `ToArray`, ma altri metodi non farebbero lo stesso. La procedura più sicura consiste nel forzare l'esecuzione della query in modo esplicito.  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Chiamare `WhenAny` sulla raccolta di attività. `WhenAny` restituisce `Task(Of Task(Of Integer))` o `Task<Task<int>>`.  Ovvero `WhenAny` restituisce un'attività che include un singolo `Task(Of Integer)` o `Task<int>` quando è attesa. L'attività singola è la prima attività della raccolta da completare. L'attività completata per prima viene assegnata a `firstFinishedTask`. Il tipo di `firstFinishedTask` è <xref:System.Threading.Tasks.Task%601> dove `TResult` è un numero intero perché è il tipo restituito di `ProcessURLAsync`.  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  In questo esempio, si è interessati solo all'attività che termina per prima. Usare quindi <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> per annullare le attività rimanenti.  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  Infine, attendere `firstFinishedTask` per recuperare la lunghezza del contenuto scaricato.  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 Eseguire il programma più volte per verificare che diversi download terminino prima.  
  
## <a name="complete-example"></a>Esempio completo  
 Il codice seguente è il file vb o MainWindow.xaml.cs completo per l'esempio. Gli asterischi contrassegnano gli elementi che sono stati aggiunti per questo esempio.  
  
 Si noti che è necessario aggiungere un riferimento per <xref:System.Net.Http>.  
  
 È possibile scaricare il progetto da [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (Esempio di attività asincrona: ottimizzazione dell'applicazione).  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Download complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        '' Comment out or delete the loop.  
        ''For Each url In urlList  
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).   
        ''    ' Argument ct carries the message if the Cancel button is chosen.   
        ''    ' Note that the Cancel button can cancel all remaining downloads.  
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ''    ' Retrieve the website contents from the HttpResponseMessage.  
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ''    resultsTextBox.Text &=  
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        ''Next  
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToArray to execute the query and start the download tasks.   
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' ***Call WhenAny and then await the result. The task that finishes   
        ' first is assigned to firstFinishedTask.  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
        ' ***Cancel the rest of the downloads. You just want the first one.  
        cts.Cancel()  
  
        ' ***Await the first completed task and display the results  
        ' Run the program several times to demonstrate that different  
        ' websites can finish first.  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
    End Function  
  
    ' ***Bundle the processing steps for a website into one async method.  
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        Return urlContents.Length  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Ottimizzazione dell'applicazione Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Programmazione asincrona con Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) (Esempio di attività asincrona: Ottimizzazione dell'applicazione)
