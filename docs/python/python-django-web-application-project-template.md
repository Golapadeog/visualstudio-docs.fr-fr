---
title: "Modèle de projet web Django pour Python dans Visual Studio | Microsoft Docs"
description: "Vue d’ensemble des modèles Visual Studio pour les applications web écrites dans Python à l’aide de l’infrastructure Django."
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 25a2d92d5d61850f0f4928de437d9040d8953dd2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="django-web-project-template"></a>Modèle de projet web Django

[Django](https://www.djangoproject.com/) est un framework Python général conçu pour un développement web rapide, sécurisé et scalable. La prise en charge de Python dans Visual Studio fournit un modèle de projet permettant de configurer la structure d’une application web Django. Pour utiliser ce modèle dans Visual Studio, sélectionnez **Fichier > Nouveau > Projet**, recherchez « Django », puis sélectionnez le modèle **Django Web Project** (Projet web Django). Le projet résultant inclut du code réutilisable, ainsi qu’une base de données SQLite par défaut. Le modèle **Blank Django Web Project** (Projet Web Django vide) est similaire, mais n’inclut pas la base de données.

Visual Studio offre une fonctionnalité IntelliSense complète pour les projets Django :

- Variables de contexte transmises dans le modèle :

    ![IntelliSense pour les variables de contexte](media/template-django-intellisense.png)

- Balisage et filtrage pour les éléments intégrés et définis par l’utilisateur :

    ![IntelliSense pour les balises et les filtres](media/template-django-intellisense-filter.png)

- Coloration syntaxique pour les éléments CSS et JavaScript incorporés :

    ![IntelliSense pour CSS](media/template-django-intellisense-css.png)

    ![IntelliSense JavaScript](media/template-django-intellisense-js.png)

Visual Studio offre également une [prise en charge complète du débogage](debugging-python-in-visual-studio.md) pour les projets Django : 

![Points d’arrêt](media/template-django-debugging.png)

Il est courant pour les projets Django d’être gérés via leur fichier `manage.py`, qui est une hypothèse suivie par Visual Studio. Si vous n’utilisez plus ce fichier comme point d’entrée, vous arrêtez essentiellement le fichier projet. Dans ce cas, vous devez [recréer le projet à partir de fichiers existants](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) sans le marquer comme projet Django.

## <a name="django-management-console"></a>Console de gestion Django

La console de gestion Django est accessible par le biais de plusieurs commandes du menu **Projet** ou par un clic droit sur le projet dans l’Explorateur de solutions.

- **Ouvrir l’interpréteur de commandes Django**  : ouvre un interpréteur de commandes dans le contexte de l’application qui vous permet de manipuler vos modèles.

    ![Console](media/template-django-console-shell.png)

- **Django Sync DB (Base de données de synchronisation Django)** : exécute `manage.py syncdb` dans une fenêtre interactive :

    ![Console](media/template-django-console-sync-db.png)

- **Collect Static (Collecter les fichiers statiques)** : exécute `manage.py collectstatic --noinput` pour copier tous les fichiers statiques dans le chemin d’accès spécifié par `STATIC_ROOT` dans votre fichier `settings.py`. Notez que lors de la [publication sur Microsoft Azure](python-web-application-project-templates.md#publishing-to-azure-app-service), les fichiers statiques sont automatiquement collectés dans le cadre de l’opération de publication.

    ![Console](media/template-django-console-collect-static.png)

- **Valider** : exécute `manage.py validate`, qui signale toutes les erreurs de validation dans les modèles installés spécifiés par `INSTALLED_APPS` dans votre fichier `settings.py` :

    ![Console](media/template-django-console-validate.png)