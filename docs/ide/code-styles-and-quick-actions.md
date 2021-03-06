---
title: "Préférences de style de code Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload: multiple
ms.openlocfilehash: 741df95afdd7c7e8b6f0ba2de75c1465cd35cc97
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="code-style-preferences"></a>Préférences de style de code

Vous pouvez définir les préférences de style de code pour vos projets C# et Visual Basic dans la boîte de dialogue **Options** accessible à partir du menu **Outils**. Sélectionnez **Éditeur de texte** > **C#** ou  **De base** > **Style de code** > **Général**. Les options définies dans cette fenêtre sont applicables à l’ordinateur local. Chaque élément de la liste affiche un aperçu de la préférence sélectionnée, comme indiqué ci-dessous.

![Options de style de code](media/code-style-quick-actions-dialog.png)

Pour chaque élément, vous pouvez définir les valeurs **Préférence** et **Gravité** en utilisant les listes déroulantes sur chaque ligne. L’option Gravité peut avoir la valeur **Aucune**, **Suggestion**, **Avertissement** ou **Erreur**. Si vous souhaitez activer les [actions rapides](../ide/quick-actions.md) pour un style de code, assurez-vous que la valeur de l’option **Gravité** n’est pas **Aucune**. L’icône en forme d’ampoule Actions rapides ![Petite icône en forme d’ampoule](media/vs2015_lightbulbsmall.png) s’affiche quand un style autre que par défaut est utilisé, et vous pouvez choisir une option dans la liste Actions rapides pour réécrire automatiquement le code avec le style par défaut.

Les paramètres de style de code pour .NET peuvent également être gérés avec un fichier [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Dans ce cas, les paramètres du fichier EditorConfig sont prioritaires sur les options sélectionnées dans la boîte de dialogue **Options**. Vous pouvez utiliser le fichier EditorConfig pour appliquer et configurer le style de codage pour l’intégralité de votre référentiel ou projet.

## <a name="see-also"></a>Voir aussi

[Actions rapides](../ide/quick-actions.md)  
[Paramètres des conventions de codage .NET pour EditorConfig](../ide/editorconfig-code-style-settings-reference.md)