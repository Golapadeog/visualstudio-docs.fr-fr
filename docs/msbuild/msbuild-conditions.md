---
title: "Conditions MSBuild | Microsoft Docs"
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
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 37aaadd72bab46b74409848723c84baa83f574fc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="msbuild-conditions"></a>Conditions MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] prend en charge un ensemble spécifique de conditions pouvant être appliquées chaque fois qu’un attribut `Condition` est autorisé. Le tableau suivant décrit ces conditions.  
  
|Condition|Description|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|A la valeur `true` si `stringA` équivaut à `stringB`.<br /><br /> Exemple :<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|  
|'`stringA`' != '`stringB`'|A la valeur `true` si `stringA` est différent de `stringB`.<br /><br /> Exemple :<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|  
|\<, >, \<=, >=|Évalue les valeurs numériques des opérandes. Retourne `true` si l’évaluation relationnelle a la valeur true. Les opérandes doivent être un nombre décimal ou hexadécimal. Les nombres hexadécimaux doivent commencer par « 0x ». **Remarque :** au format XML, les caractères `<` et `>` doivent être insérés dans une séquence d’échappement. Le symbole `<` est représenté sous la forme `&lt;`. Le symbole `>` est représenté sous la forme `&gt;`.|  
|Exists(« `stringA` »)|A la valeur `true` si un fichier ou un dossier du nom `stringA` existe.<br /><br /> Exemple :<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|  
|HasTrailingSlash (« `stringA` »)|A la valeur `true` si la chaîne spécifiée contient une barre oblique inverse finale (\\) ou une barre oblique (/).<br /><br /> Exemple :<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Les guillemets simples ne sont pas requis pour les chaînes alphanumériques simples ou les valeurs booléennes, mais ils le sont pour les valeurs vides.|  
|!|A la valeur `true` si l’opérande a la valeur `false`.|  
|Et|A la valeur `true` si les deux opérandes ont la valeur `true`.|  
|Ou|A la valeur `true` si l’un des opérandes au moins a la valeur `true`.|  
|()|Mécanisme de regroupement qui prend la valeur `true` si les expressions qu’il contient ont la valeur `true`.|  
|$if$ ( %expression% ), $else$, $endif$|Vérifie si la condition `%expression%` spécifiée correspond à la valeur de chaîne du paramètre de modèle personnalisé transmis. Si la condition `$if$` prend la valeur `true`, ses instructions sont exécutées ; dans le cas contraire, la condition `$else$` est vérifiée. Si la condition `$else$` a la valeur `true`, ses instructions sont exécutées. Dans le cas contraire, la condition `$endif$` met fin à l’évaluation de l’expression.<br /><br /> Pour obtenir des exemples d’utilisation, consultez le blog [Visual Studio Project/Item Template Parameter Logic (Logique des paramètres de modèles de projet/élément de Visual Studio)](http://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic).|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)   
 [Constructions conditionnelles MSBuild](../msbuild/msbuild-conditional-constructs.md)   
 [Procédure pas à pas : création d’un fichier projet MSBuild en partant de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
