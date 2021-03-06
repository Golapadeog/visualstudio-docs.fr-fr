---
title: "Guide pratique pour référencer un kit SDK de projet MSBuild | Microsoft Docs"
ms.custom: 
ms.date: 01/25/2018
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: jeffkl
ms.author: jeffkl
manager: angerlic
ms.workload:
- multiple
ms.openlocfilehash: 28027b21d3f562e3eda94dc91de16ddb38362d3c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-use-msbuild-project-sdks"></a>Guide pratique pour utiliser les kits SDK de projet MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15.0 a introduit le concept de « kit SDK de projet », qui simplifie l’utilisation de kits SDK nécessitant l’importation des propriétés et des cibles.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```  
  
Durant l’évaluation du projet, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ajoute des importations implicites au début et à la fin de votre projet :

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>  
```  

## <a name="referencing-a-project-sdk"></a>Référencement d’un kit SDK de projet
 Il existe trois manières de référencer un kit SDK de projet.

1. Utilisez l'attribut `Sdk` sur l'élément `<Project/>` :
    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```
    Une importation implicite est ajoutée au début et à la fin du projet, comme expliqué ci-dessus.  Le format de l’attribut `Sdk` est `Name[/Version]`, où Version est une donnée facultative.  Par exemple, vous pouvez spécifier `My.Custom.Sdk/1.2.3`.

2. Utilisez l'élément `<Sdk/>` de niveau supérieur :
    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```
   Une importation implicite est ajoutée au début et à la fin du projet, comme expliqué ci-dessus.  L'attribut `Version` n'est pas requis.

3. Utilisez l’élément `<Import/>` à un endroit quelconque de votre projet :
    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```
   L’inclusion explicite des importations dans votre projet vous permet d’avoir un contrôle total de l’ordre.

   Quand vous utilisez l’élément `<Import/>`, vous pouvez également spécifier un attribut `Version` facultatif.  Par exemple, vous pouvez spécifier `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Méthode de résolution des kits SDK de projet
Durant l’évaluation de l’importation, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] résout dynamiquement le chemin d’accès au kit SDK de projet en fonction du nom et de la version que vous avez spécifiés.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] contient également une liste des programmes de résolution de kits SDK inscrits, qui sont des plug-ins permettant de localiser les kits SDK de projet sur votre ordinateur.  Ces plug-ins sont les suivants :

1. Un programme de résolution basé sur NuGet qui interroge vos flux de packages configurés pour localiser les packages NuGet qui correspondent à l’ID et à la version du kit SDK que vous avez spécifié.<br/>
   Ce programme de résolution est uniquement actif si vous avez spécifié une version facultative, et il peut être utilisé pour tout kit SDK de projet personnalisé.  
2. Un programme de résolution d’interface CLI .NET qui résout les kits SDK installés avec l’interface CLI .NET.<br/>
   Ce programme de résolution localise les kits SDK de projet tels que `Microsoft.NET.Sdk` et `Microsoft.NET.Sdk.Web` qui font partie du produit.
3. Un programme de résolution par défaut qui résout les kits SDK installés avec MSBuild.

Le programme de résolution de kits SDK basé sur NuGet prend en charge la spécification d’une version dans votre fichier [global.json](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json), ce qui vous permet de contrôler la version du kit SDK de projet à partir d’un seul emplacement, et non de chaque projet individuel :

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```
Seule une version de chaque kit SDK de projet peut être utilisée durant une build.  Si vous référencez deux versions différentes du même kit SDK de projet, MSBuild émet un avertissement.  Il est recommandé de ne **pas** spécifier de version dans vos projets si une version est spécifiée dans votre fichier `global.json`.  

## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [Personnaliser votre build](../msbuild/customize-your-build.md)   
