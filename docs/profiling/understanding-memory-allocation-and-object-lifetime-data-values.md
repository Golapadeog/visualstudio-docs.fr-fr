---
title: "Fonctionnement de l’allocation de mémoire et des informations de durée de vie des objets | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7d7594ea2356c737d555423082f3c3010835cc7f
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>Fonctionnement de l’allocation de mémoire et des informations de durée de vie des objets

La méthode de profilage d’*allocation de mémoire .NET* des outils de profilage de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] collecte des informations sur la taille et le nombre d’objets qui ont été créés dans une allocation ou détruits dans un garbage collection, ainsi que des informations supplémentaires sur la *pile des appels* de la fonction quand l’événement s’est produite. Une *pile des appels* est une structure dynamique qui stocke des informations sur les fonctions qui s’exécutent sur le processeur.

Le profileur de mémoire interrompt le processeur de l’ordinateur à chaque allocation d’un objet du .NET Framework dans une application profilée. Quand les données de durée de vie des objets sont également collectées, le profileur interrompt le processeur après chaque garbage collection du .NET Framework. Les données sont agrégées pour chaque fonction profilée et pour chaque type d’objet.

## <a name="allocation-data"></a>Données d’allocation

Quand un événement de mémoire se produit, les totaux des nombres et des tailles des objets de mémoire alloués ou détruits sont incrémentés.

Quand un événement d’allocation de mémoire se produit, le profileur incrémente le nombre d’échantillons pour chaque fonction sur la pile des appels. Quand les données sont collectées, une seule fonction sur la pile des appels exécute le code de son corps de fonction. Les autres fonctions sur la pile sont des parents dans la hiérarchie des appels de fonctions qui sont en attente du retour des fonctions qu’elles ont appelées.

- Pour l’événement d’allocation, le profileur incrémente le nombre d’échantillons *exclusifs* de la fonction qui exécute ses instructions. Comme un échantillon exclusif fait également partie du total des échantillons (*inclusifs*) de la fonction, le nombre d’échantillons inclusifs de la fonction active est également incrémenté.

- Le profileur incrémente le nombre d’échantillons inclusifs de toutes les autres fonctions sur la pile des appels.

## <a name="lifetime-data"></a>Données de durée de vie

Dans le récupérateur de mémoire du .NET Framework gère l’allocation et la libération de mémoire pour votre application. Pour optimiser les performances du garbage collector, le tas managé est divisé en trois générations : 0, 1 et 2. Le récupérateur de mémoire du runtime stocke les nouveaux objets dans la génération 0. Les objets qui survivent aux collectes sont promus et stockés dans les générations 1 et 2.

Le récupérateur de mémoire récupère de la mémoire en désallouant une génération entière d’objets. Pour les objets créés par l’application profilée, la vue Durée de vie des objets montre le nombre et la taille des objets, ainsi que la génération auprès de laquelle ils ont été récupérés.