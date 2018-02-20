---
title: Introduire une variable locale dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 997220d3b1a7305f84f61ee5fd4c205d1157f1b2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introduire une variable locale dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de générer immédiatement une variable locale pour remplacer une expression existante.

**Quand :** vous disposez d’un code pouvant être facilement réutilisé ultérieurement s’il figurait dans une variable locale.

**Pourquoi :** vous pourriez copier et coller le code plusieurs fois pour l’utiliser dans différents emplacements, mais il est préférable d’effectuer l’opération une fois, d’enregistrer le résultat dans une variable locale puis d’utiliser la variable locale de manière globale.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance l’expression que vous souhaitez assigner à une nouvelle variable locale.

   - C# :

    ![Code C# mis en surbrillance](media/local-highlight-cs.png)

   - Visual Basic :

    ![Code VB mis en surbrillance](media/local-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
     - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
     - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Introduire un aperçu local](media/local-preview-cs.png)

1. Sélectionnez **Introduire un élément local pour (toutes les occurrences de '*expression*'** à partir du menu déroulant.

   > [!TIP]
   > Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.

   La variable locale est créée avec le type déduit de son utilisation. Renommez la nouvelle variable locale.

   - C# :

      ![Résultat de l’implémentation de l’interface (C#)](media/local-result-cs.png)

   - Visual Basic :

      ![Résultat de l’implémentation de l’interface (VB)](media/local-result-vb.png)

   > [!NOTE]
   > Vous pouvez utiliser l’option de menu **...toutes les occurrences de...** pour remplacer chaque instance de l’expression sélectionnée, et pas seulement celle que vous avez spécifiquement mise en surbrillance.

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)