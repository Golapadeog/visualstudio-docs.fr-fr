---
title: "Présentation des valeurs des données de conflit de ressources | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7158af10ccb7b34b6bf5836cd6176216fbdb6832
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="understanding-resource-contention-data-values"></a>Fonctionnement des valeurs de données de conflit de ressources

Le profilage de conflit de ressources collecte les informations détaillées de la pile des appels chaque fois que des threads en concurrence dans une application sont forcés d’attendre pour accéder à une ressource partagée.

Les rapports de conflit de ressources affichent le nombre total de conflits et le temps total passé en attente d’une ressource pour les modules, les fonctions, les lignes de code source et les instructions où l’attente s’est produite.

- Les valeurs inclusives affichent le nombre total de conflits qui ont forcé une fonction à attendre en raison des conflits de ressources et le temps d’attente total de la fonction.  Les conflits provoqués par des fonctions enfants qui ont été appelées par la fonction sont inclus dans les valeurs de temps inclusives.

- Les valeurs de temps exclusives montrent seulement le nombre de conflits qui ont forcé une fonction à attendre et qui ont été provoqués par le code du corps de la fonction. Les conflits provoqués par des fonctions enfants ne sont pas inclus. Le temps exclusif pour la fonction inclut seulement les temps d’attente qui ont été provoqués par des instructions du corps de la fonction.

Les vues du rapport de conflit de ressources incluent également des graphiques chronologiques qui montrent les événements de conflit individuels au fil du temps et affichent les piles d’appels qui ont créé l’événement particulier. Pour plus d'informations, consultez l'une des rubriques suivantes :

- [Détails relatifs au thread, vue](../profiling/thread-details-view-contention-data.md)

- [Informations sur les ressources, vue](../profiling/resource-details-view-contention-data.md)

Pour plus d’informations sur le deuxième mode de profilage d’accès concurrentiel, consultez [Visualiseur concurrentiel](../profiling/concurrency-visualizer.md).