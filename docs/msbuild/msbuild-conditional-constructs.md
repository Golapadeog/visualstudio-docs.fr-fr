---
title: Constructions conditionnelles MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f018ec733248f6663e2cf2292599df9d2afdc81c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-conditional-constructs"></a>Constructions conditionnelles MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit un mécanisme de traitement de type « soit/soit » avec les éléments [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) et [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## <a name="using-the-choose-element"></a>Utilisation de l’élément Choose  
 L’élément `Choose` contient une série d’éléments `When` avec des attributs `Condition` qui sont testés du haut vers le bas, jusqu’à ce qu’un élément avec la valeur `true` soit trouvé. Si plusieurs éléments `When` ont la valeur `true`, seul le premier est utilisé. Un élément `Otherwise` (si présent) est évalué si aucune condition d’un élément `When` n’a la valeur `true`.  
  
 Les éléments `Choose` peuvent être utilisés comme des éléments enfants des éléments `Project`, `When` et `Otherwise`. Les éléments `When` et `Otherwise` peuvent avoir des éléments enfants `ItemGroup`, `PropertyGroup` ou `Choose`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise les éléments `Choose` et `When` pour un traitement de type « soit/soit ». Les propriétés et les éléments du projet sont définis en fonction de la valeur de la propriété `Configuration`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Choose, élément (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [When, élément (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise, élément (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)