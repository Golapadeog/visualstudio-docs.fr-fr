---
title: "Démarrage rapide : Créer un projet Python à l’aide de Cookiecutter dans Visual Studio | Microsoft Docs"
description: "Guide pratique pour commencer rapidement à utiliser Python à l’aide d’un modèle Cookiecutter dans Visual Studio."
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 4b9b7a51436eeeb67634714216f9a583de679a07
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Démarrage rapide : Créer un projet à partir d’un modèle Cookiecutter

Une fois que vous avez [installé la prise en charge de Python dans Visual Studio 2017](installing-python-support-in-visual-studio.md), il est facile de créer un projet à partir d’un modèle Cookiecutter parmi les nombreux qui sont publiés sur GitHub. [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) fournit une interface utilisateur graphique pour découvrir des modèles, des options de modèle d’entrée et créer des projets et des fichiers. Cette extension est incluse avec Visual Studio 2017 et peut être installée séparément dans les versions antérieures de Visual Studio.

1. Pour ce démarrage rapide, installez d’abord la distribution Python Anaconda3, qui inclut les packages Python nécessaires pour le modèle Cookiecutter montré ici. Exécuter le programme d’installation de Visual Studio, sélectionnez **Modifier**, développez les options pour **Développement Python** sur le côté droit et sélectionnez « Anaconda3 » (32 bits ou 64 bits). Notez que si l’installation peut prendre un certain temps, dépendant de la vitesse de votre connexion Internet, il s’agit de la méthode la plus simple pour installer les packages nécessaires.

1. Lancez Visual Studio.

1. Sélectionnez **Fichier > Nouveau > À partir de Cookiecutter...**. Cette commande ouvre une fenêtre dans Visual Studio, où vous pouvez parcourir les modèles. 

    ![Nouveau projet à partir d’un modèle Cookiecutter](media/projects-from-cookiecutter1.png)

1. Sélectionnez le modèle « Microsoft/python-sklearn-classifier-cookiecutter », puis sélectionnez **suivant**. (Le processus peut prendre plusieurs minutes la première fois que vous utilisez Cookiecutter.)

1. Dans l’étape suivante, définissez un emplacement pour le nouveau projet dans le champ **Créer dans**, puis sélectionnez **Créer**.

    ![Deuxième étape de l’utilisation de Cookiecutter : définition des propriétés du projet](media/projects-from-cookiecutter2.png)

1. Quand le processus est terminé, vous voyez le message « Fichiers créés. » Sélectionnez la commande **Ouvrir dans l’Explorateur de solutions** pour ouvrir le projet.

1. Appuyez sur Ctrl+F5 ou sélectionnez **Déboguer > Démarrer sans débogage** pour exécuter le programme. 

    ![Sortie du projet de modèle python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Didacticiel : Utilisation de Python dans Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Voir aussi

- [Utilisation de l’extension Cookiecutter](using-python-cookiecutter-templates.md)
- [Identifier manuellement un interpréteur Python existant](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).
- [Installer la prise en charge de Python dans Visual Studio 2015 et antérieur](installing-python-support-in-visual-studio.md).
- [Emplacements d’installation](installing-python-support-in-visual-studio.md#install-locations).
