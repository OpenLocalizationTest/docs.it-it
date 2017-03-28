---
title: Organizzazione e test di progetti con la riga di comando di .NET Core | Microsoft Docs
description: Questa esercitazione illustra come organizzare e testare i progetti .NET Core dalla riga di comando.
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 52ff1be3-d92e-4477-9c84-8c1771e87ab5
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 3f401907a59d5427cbcfaa0b785931a7ed82110f
ms.lasthandoff: 03/07/2017

---

# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Organizzazione e test di progetti con la riga di comando di .NET Core

Questa esercitazione segue [Introduzione all'uso di .NET Core su Windows/Linux/macOS dalla riga di comando](./using-with-xplat-cli.md) e illustra come andare oltre gli scenari semplici di tipo "hello world" e preparare la strada per applicazioni più avanzate e organizzate.

## <a name="using-folders-to-organize-code"></a>Uso di cartelle per organizzare il codice

Si supponga di voler introdurre alcuni nuovi tipi su cui lavorare. A tale scopo è possibile aggiungere altri file assicurandosi di assegnare spazi dei nomi che possono essere inclusi nel file *Program.cs*.

```
/MyProject
|__Program.cs
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
```

Questa è un'ottima soluzione quando le dimensioni del progetto sono relativamente piccole. Se tuttavia si ha un'applicazione più grande con molti tipi di dati diversi e potenzialmente con più livelli, può essere opportuno organizzare i dati in maniera logica. A questo punto entrano in gioco le cartelle. È possibile seguire [il progetto di esempio NewTypes](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild) descritto in questa guida o creare file e cartelle personalizzati.

Per iniziare, creare una nuova cartella sotto la radice del progetto. `/Model` è la cartella scelta in questo esempio.

```
/NewTypes
|__/Model
|__Program.cs
|__NewTypes.csproj
```

Aggiungere ora alcuni nuovi tipi nella cartella:

```
/NewTypes
|__/Model
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__Program.cs
|__NewTypes.csproj
```

Come per i file presenti in una stessa directory, assegnare a tutti i tipi lo stesso spazio dei nomi in modo da poterli includere in `Program.cs`.

### <a name="example-pet-types"></a>Esempio: Tipi di animali domestici

In questo esempio vengono creati due nuovi tipi, `Dog` e `Cat`, che implementano un'interfaccia comune, `IPet`.

Struttura di cartelle:

```
/NewTypes
|__/Pets
   |__Dog.cs
   |__Cat.cs
   |__IPet.cs
|__Program.cs
|__NewTypes.csproj
```

`IPet.cs`:
```csharp
using System;

namespace Pets
{
    public interface IPet
    {
        string TalkToOwner();
    }
}
```

`Dog.cs`:
```csharp
using System;

namespace Pets
{
    public class Dog : IPet
    {
        public string TalkToOwner() => "Woof!";
    }
}
```

`Cat.cs`:
```csharp
using System;

namespace Pets
{
    public class Cat : IPet
    {
        public string TalkToOwner() => "Meow!";
    }
}
```

`Program.cs`:
```csharp
using System;
using Pets;
using System.Collections.Generic;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            List<IPet> pets = new List<IPet>
            {
                new Dog(),
                new Cat()  
            };
            
            foreach (var pet in pets)
            {
                Console.WriteLine(pet.TalkToOwner());
            }
        }
    }
}
```

`NewTypes.csproj`:
```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />
  
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>
  
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

E se si esegue questo codice:

```
$ dotnet restore
$ dotnet run
Woof!
Meow!
```

È possibile aggiungere nuovi tipi di animali domestici (come `Bird`) estendendo il progetto.

## <a name="testing-your-console-app"></a>Test dell'applicazione console

È probabile che a un certo punto si decida di testare i progetti. Ecco un buon metodo per eseguire questa operazione:

1. Spostare l'origine del progetto esistente in una nuova cartella `src`.

   ```
   /Project
   |__/src
   ```

2. Creare una directory `/test` e quindi `cd` al suo interno.

   ```
   /Project
   |__/src
   |__/test
   ```

3. Inizializzare la directory con un comando `dotnet new xunit`. In questo caso si presuppone l'uso di xUnit, ma è possibile anche usare MS Test sostituendo `xunit` con `mstest`.
   
### <a name="example-extending-the-newtypes-project"></a>Esempio: Estensione del progetto NewTypes

Ora che il sistema del progetto è stato creato, è possibile creare il progetto di test e iniziare a scrivere i test. A partire da questo punto, nella guida verrà usato ed esteso [il progetto NewTypes di esempio](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/NewTypesMsBuild). Inoltre, verrà usato il framework di test [xUnit](https://xunit.github.io/). È possibile proseguire o creare un sistema personalizzato basato su più progetti con test.

La struttura dell'intero progetto avrà un aspetto simile al seguente:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

È necessario verificare che nel progetto di test siano presenti due nuovi elementi:

1. Un file *NewTypesTests.csproj* corretto con:

   * Un riferimento a `xunit`
   * Un riferimento a `dotnet-test-xunit`
   * Un riferimento allo spazio dei nomi corrispondente al codice sottoposto a test

   Ciò può essere compilato digitando `dotnet new xunit` al prompt dei comandi nella directory *NewTypesTests* e aggiungendo un riferimento di progetto al progetto `NewTypes`.

    `NewTypesTests/NewTypesTests.csproj`:
    ```xml
    <Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />

      <PropertyGroup>
        <OutputType>Exe</OutputType>
        <TargetFramework>netcoreapp1.0</TargetFramework>
      </PropertyGroup>

      <ItemGroup>
        <Compile Include="**\*.cs" />
        <EmbeddedResource Include="**\*.resx" />
      </ItemGroup>

      <ItemGroup>
        <PackageReference Include="Microsoft.NETCore.App">
          <Version>1.0.1</Version>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Sdk">
          <Version>1.0.0-alpha-20161104-2</Version>
          <PrivateAssets>All</PrivateAssets>
        </PackageReference>
        <PackageReference Include="Microsoft.NET.Test.Sdk">
          <Version>15.0.0-preview-20161024-02</Version>
        </PackageReference>
        <PackageReference Include="xunit">
          <Version>2.2.0-beta3-build3402</Version>
        </PackageReference>
        <PackageReference Include="xunit.runner.visualstudio">
          <Version>2.2.0-beta4-build1188</Version>
        </PackageReference>
        <ProjectReference Include="../../src/NewTypes/NewTypes.csproj"/>
      </ItemGroup>

      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

2. Classe di test xUnit.

    `PetTests.cs`: 
    ```csharp
    using System;
    using Xunit;
    using Pets;
    public class PetTests
    {
        [Fact]
        public void DogTalkToOwnerTest()
        {
            string expected = "Woof!";
            string actual = new Dog().TalkToOwner();
            
            Assert.Equal(expected, actual);
        }
        
        [Fact]
        public void CatTalkToOwnerTest()
        {
            string expected = "Meow!";
            string actual = new Cat().TalkToOwner();
            
            Assert.Equal(expected, actual);
        }
    }
    ```
   
A questo punto è possibile eseguire i test. Il comando [`dotnet test`](../tools/dotnet-test.md) esegue il Test Runner specificato nel progetto. Assicurarsi di iniziare dalla directory di livello più alto.
 
```
$ cd test/NewTypesTests
$ dotnet restore
$ dotnet test
```
 
L'output dovrebbe essere simile al seguente:
 
```
xUnit.net .NET CLI test runner (64-bit win10-x64)
  Discovering: NewTypesTests
  Discovered:  NewTypesTests
  Starting:    NewTypesTests
  Finished:    NewTypesTests
=== TEST EXECUTION SUMMARY ===
   NewTypesTests  Total: 2, Errors: 0, Failed: 0, Skipped: 0, Time: 0.144s
SUMMARY: Total: 1 targets, Passed: 1, Failed: 0.
```
