---
title: Outils R pour Visual Studio et conteneurs Docker | Microsoft Docs
description: "Guide pratique pour configurer des conteneurs Docker pour R et s’y connecter avec Visual Studio."
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author:
- kraigb
- karthiknadig
ms.author:
- kraigb
- karthiknadig
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 85db40a5e5b4fa05260bd62ff9857cc9b1ffebcd
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="using-docker-containers-with-r-tools-for-visual-studio"></a>Utilisation de conteneurs Docker avec Outils R pour Visual Studio

Outils R pour Visual Studio (RTVS) version 1.3+, parallèlement à une installation de [Docker pour Windows](https://www.docker.com/docker-windows), prend en charge l’utilisation des conteneurs Docker.

## <a name="creating-a-container"></a>Création d'un conteneur

1. Sélectionnez le bouton **Conteneurs...** situé dans l’angle droit de la fenêtre **Espaces de travail** (**Outils R > Windows > Espaces de travail**). La fenêtre vous informe si vous n’avez pas installé Docker pour Windows et fournit un lien pour son téléchargement. L’installation de Docker peut nécessiter un redémarrage de l’ordinateur.

    ![Fenêtre Espaces de travail dans Outils R pour Visual Studio (VS2017) avec la commande Conteneurs](media/container-workspaces-window.png)

1. Dans la fenêtre **Conteneurs**, sélectionnez **Créer** :

    ![Commande Créer dans la fenêtre Conteneurs](media/containers-window-create.png)

1. Complétez les informations requises dans la boîte de dialogue et sélectionnez **Créer**. Les informations d’identification que vous entrez sont également utilisées pour créer un compte sur Linux, avec lequel vous vous connecterez ultérieurement.

    ![Entrée d’un nom de conteneur et d’informations d’identification lors de la création d’un conteneur](media/containers-window-create-fill.png)

1. La génération de l’image par RTVS peut prendre un certain temps. La fenêtre **Sortie** dans Visual Studio indique la progression, mais peut sembler figée lors des longs téléchargements d’images ; armez-vous de patience. Une fois l’image créée, RTVS démarre le conteneur, et celui-ci apparaît dans la fenêtre **Conteneur**. Les contrôles situés à droite permettent d’arrêter, de supprimer ou de redémarrer le conteneur.

    ![Fenêtre Conteneurs montrant un conteneur terminé](media/containers-window-created.png)

## <a name="connecting-to-a-container"></a>Connexion à un conteneur

1. La section **Conteneurs en cours d’exécution locaux** de la fenêtre **Espaces de travail** présente les conteneurs qui exécutent le démon RTVS sur le port 5444. (Consultez [R Server distant pour Linux](setting-up-remote-r-service-on-linux.md) pour plus d’informations sur la façon dont le démon est configuré.)

    ![Fenêtre Espaces de travail montrant les conteneurs disponibles](media/workspaces-window-running-containers.png)

1. Pour vous connecter à un conteneur, double-cliquez sur son nom ou sélectionnez la flèche située à sa droite. Une fois connecté, une fenêtre **interactive R** apparaît (consultez [Utilisation de la fenêtre interactive R](interactive-repl-for-r-in-visual-studio.md)) :

    ![Fenêtre Espaces de travail et fenêtre REPL ouvertes pour un conteneur](media/workspaces-window-container-connected.png)

## <a name="using-custom-built-images"></a>Utilisation d’images personnalisées

RTVS détecte et autorise la gestion des conteneurs créés à l’aide d’images personnalisées, comme l’image microsoft/rtvs décrite dans le fichier Docker ci-dessous. L’image de base utilisée ici a rtvs-daemon, R 3.4.2 et les packages R courants préinstallés. **Remarque** : modifiez le nom d’utilisateur et le mot de passe indiqués ici, si nécessaire.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Utilisez la commande suivante pour générer l’image, en changeant le nom du conteneur (argument `--name`) à votre gré :

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

L’argument `-p 6056:5444` mappe le port 6056 sur le port interne 5444, que RTVS utilise pour détecter rtvs-daemon. Tout conteneur qui expose le port du conteneur 5444 est répertorié dans la fenêtre **Espaces de travail**. Vous pouvez alors utiliser la fenêtre **Espaces de travail** pour vous connecter à un conteneur en utilisant `<<unix>>\ruser1` comme nom d’utilisateur et « foobar » comme mot de passe, sauf si vous avez spécifié des informations d’identification différentes dans le fichier Docker.
