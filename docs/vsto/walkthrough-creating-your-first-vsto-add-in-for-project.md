---
title: "Procédure pas à pas : Création de votre complément VSTO pour Project | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1e1b768a8d812d3a4c0222bbb3e762c0f5046f56
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-project"></a>Procédure pas à pas : création de votre premier complément VSTO pour Project
  Cette procédure pas à pas vous montre comment créer un complément VSTO pour Microsoft Office Project. Les fonctionnalités que vous créez dans ce type de solution sont accessibles à l’application proprement dite, quels que soient les projets ouverts. Pour plus d’informations, consultez [présentation du développement de Solutions Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un projet de complément VSTO Project  
  
-   Écriture de code qui utilise le modèle objet de Project pour ajouter une tâche à un nouveau projet  
  
-   Génération et exécution du projet pour le tester  
  
-   Nettoyage du projet terminé, pour que le complément VSTO ne s’exécute plus automatiquement sur votre ordinateur de développement  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] ou [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
  
#### <a name="to-create-a-new-project-in-visual-studio"></a>Pour créer un projet dans Visual Studio  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
3.  Dans le volet Modèles, développez **Visual C#** ou **Visual Basic**, puis développez **Office/SharePoint**.  
  
4.  Sous le nœud développé **Office/SharePoint** , sélectionnez le nœud **Compléments Office** .  
  
5.  Dans la liste des modèles de projet, sélectionnez **Complément Project 2010** ou **Complément Project 2013**.  
  
6.  Dans la zone **Nom** , tapez **FirstProjectAddIn**.  
  
7.  Cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet **FirstProjectAddIn** et ouvre le fichier de code **ThisAddIn** dans l’éditeur.  
  
## <a name="writing-code-that-adds-a-new-task-to-a-project"></a>Écriture de code qui ajoute une nouvelle tâche à un projet  
 L'étape suivante consiste à ajouter du code au fichier de code ThisAddIn. Le nouveau code utilise le modèle objet de Project pour ajouter une nouvelle tâche à un projet. Par défaut, le fichier de code ThisAddIn contient le code généré suivant :  
  
-   Une définition partielle de la classe `ThisAddIn` . Cette classe fournit un point d’entrée pour votre code et donne accès au modèle objet de Project. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Le reste de la classe `ThisAddIn` est défini dans un fichier de code masqué que vous ne devez pas modifier.  
  
-   Les gestionnaires d'événements `ThisAddIn_Startup` et `ThisAddIn_Shutdown` . Ces gestionnaires d’événements sont appelés quand Project charge et décharge votre complément VSTO. Utilisez ces gestionnaires d'événements pour initialiser votre complément VSTO quand il est chargé, ainsi que pour nettoyer les ressources utilisées par votre complément VSTO quand il est déchargé. Pour plus d'informations, consultez [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-task-to-a-new-project"></a>Pour ajouter une tâche à un nouveau projet  
  
1.  Dans le fichier de code ThisAddIn, ajoutez le code suivant à la classe `ThisAddIn` . Ce code définit un gestionnaire d’événements pour l’événement NewProject de la classe Microsoft.Office.Interop.MSProject.application.  
  
     Quand l’utilisateur crée un projet, ce gestionnaire d’événements ajoute une tâche au projet.  
  
     [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
 Pour modifier le projet, cet exemple de code utilise les objets suivants :  
  
-   Le champ `Application` de la classe `ThisAddIn` . Le `Application` champ retourne un objet Microsoft.Office.Interop.MSProject.application, qui représente l’instance actuelle du projet.  
  
-   Le `pj` paramètre du Gestionnaire d’événements pour l’événement NewProject. Le `pj` paramètre est un objet Microsoft.Office.Interop.MSProject.Project, qui représente le projet. Pour plus d'informations, consultez [Project Solutions](../vsto/project-solutions.md).  
  
1.  En C#, ajoutez le code suivant au gestionnaire d'événements `ThisAddIn_Startup` . Ce code connecte le `Application_Newproject` Gestionnaire d’événements à l’événement NewProject.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
-  
  
## <a name="testing-the-project"></a>Test du projet  
 Quand vous générez et exécutez le projet, vérifiez que la nouvelle tâche apparaît dans le nouveau projet obtenu.  
  
#### <a name="to-test-the-project"></a>Pour tester le projet  
  
1.  Appuyez sur **F5** pour générer et exécuter votre projet. Microsoft Project démarre et ouvre automatiquement un nouveau projet vide.  
  
     Quand vous générez le projet, le code est compilé dans un assembly qui est inclus dans le dossier de sortie de la génération du projet. Visual Studio crée aussi un jeu d’entrées de Registre qui permet à Project de détecter et de charger le complément VSTO, puis configure les paramètres de sécurité sur l’ordinateur de développement pour permettre l’exécution du complément VSTO. Pour plus d'informations, consultez [Vue d'ensemble du processus de génération de solutions Office](http://msdn.microsoft.com/en-us/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Vérifiez qu’une nouvelle tâche est bien ajoutée au projet vierge.  
  
3.  Vérifiez que le texte suivant s’affiche dans le champ **Nom de la tâche** de la tâche.  
  
     **Ce texte a été ajouté via le code.**  
  
4.  Fermez Microsoft Project.  
  
## <a name="cleaning-up-the-project"></a>Nettoyage du projet  
 Une fois que vous avez terminé de développer un projet, supprimez l'assembly du complément VSTO, les entrées de Registre et les paramètres de sécurité de votre ordinateur de développement. Sinon, le complément VSTO s’exécute chaque fois que vous ouvrez Microsoft Project sur votre ordinateur.  
  
#### <a name="to-clean-up-your-project"></a>Pour nettoyer votre projet  
  
1.  Dans Visual Studio, dans le menu **Générer** , cliquez sur **Nettoyer la solution**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Maintenant que vous avez créé un complément VSTO de base pour Project, vous pouvez en savoir plus sur le développement des compléments VSTO en consultant les rubriques suivantes :  
  
-   Tâches de programmation générales que vous pouvez effectuer dans les compléments VSTO pour Project : [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Utilisation du modèle objet de Project : [Project Solutions](../vsto/project-solutions.md).  
  
-   Génération et débogage des Compléments VSTO pour Project : [génération de Solutions Office](../vsto/building-office-solutions.md).  
  
-   Déploiement de compléments VSTO pour Project : [déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Solutions Project](../vsto/project-solutions.md)   
 [Génération de Solutions Office](../vsto/building-office-solutions.md)   
 [Déploiement d’une Solution Office](../vsto/deploying-an-office-solution.md)   
 [Vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md)  
  
  