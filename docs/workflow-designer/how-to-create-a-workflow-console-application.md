---
title: "Comment : créer une Application Console de Workflow | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 94058f15911ed0f72023ea4cd10c9a935f13ba44
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-a-workflow-console-application"></a>Procédure : créer une application console de workflow
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] vous permet de créer des workflows pour l'exécution de processus système ou humains. Le Concepteur de flux de travail Windows fournit l’aire de conception pour la création de ces flux de travail. Le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] peut être utilisé pour créer des workflows depuis [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou il peut être intégré dans d'autres applications pour réhéberger le concepteur.

 Cette rubrique décrit comment utiliser le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] pour créer un workflow dans une application console.

### <a name="to-create-a-workflow-console-application"></a>Pour créer une application console de workflow

1.  Démarrez [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

2.  Sur le **fichier** menu, pointez sur **nouveau**, puis sélectionnez **projet...** .

     La boîte de dialogue **Nouveau projet** s'affiche.

3.  Dans le **modèles installés** volet, sélectionnez **Workflow** à partir de le le **Visual C#** ou **Visual Basic** regroupements, en fonction de votre langue de préférence.

4.  Dans le volet central, sélectionnez **Application Console de Workflow**.

5.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

6.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.

7.  Dans le **Solution** , entrez le nom de la nouvelle solution. Cliquez sur **OK** pour créer l’application.

    > [!NOTE]
    > Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter**, puis  **Nouveau projet...**  pour ouvrir le **nouveau projet** boîte de dialogue. Procédez comme décrit ci-dessus dans cette procédure.

8.  Le modèle de projet crée une définition de workflow en XAML et la définition d'application console se trouve dans le code source. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] s'ouvre et affiche la zone de dessin du workflow que vous avez créé.

9. Pour composer un workflow, faites glisser les activités ou autres éléments de flux de travail à partir de la **boîte à outils** vers l’aire de conception de votre flux de travail.

## <a name="see-also"></a>Voir aussi

- [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)