---
title: "DA0505 : Octets privés alloués en moyenne au processus en cours de profilage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5d37ebd2ec296153eefdb08d52930cfc08614e96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505 : Octets privés alloués en moyenne au processus en cours de profilage
|||  
|-|-|  
|ID de règle|DA0505|  
|Category|Gestion des ressources|  
|Méthode de profilage|Tous|  
|Message|Uniquement à titre d’informations. Le compteur Octets privés de processus mesure la mémoire virtuelle allouée par le processus que vous profilez. La valeur signalée correspond à la moyenne pour tous les intervalles de mesure.|  
|Type de règle|Information|  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="rule-description"></a>Description de la règle  
 Ce message signale la quantité moyenne de mémoire virtuelle actuellement allouée par le processus, en octets (octets privés). Les octets privés représentent les emplacements de mémoire virtuelle alloués par le processus et qui ne sont accessibles qu’aux threads actuellement exécutés dans le processus.  
  
 Pour un processus 32 bits s’exécutant sur un ordinateur 32 bits, la taille maximale de la partie privée de l’espace d’adressage de processus est de 2 Go. Avec le commutateur Boot.ini [/3GB](http://go.microsoft.com/fwlink/?LinkId=177831), les processus 32 bits peuvent acquérir jusqu’à 3 Go de mémoire virtuelle. Un processus 32 bits exécuté sur un ordinateur 64 bits peut acquérir jusqu’à 4 Go de mémoire virtuelle privée.  
  
 Un processus 64 bits exécuté sur un ordinateur 64 bits peut acquérir jusqu’à 8 To de mémoire virtuelle privée.  
  
 La valeur signalée correspond à la moyenne de tous les intervalles de mesure pendant lesquels le processus profilé était actif.  
  
 Pour plus d’informations sur les espaces d’adressage de processus, consultez [Espace d’adressage virtuel](http://go.microsoft.com/fwlink/?LinkId=177832) dans la documentation relative à la gestion de la mémoire dans Windows.  
  
## <a name="how-to-use-rule-data"></a>Comment utiliser des données de règle  
 Utilisez la valeur signalée pour comparer les performances des différentes versions du programme ou pour comprendre les performances de l’application dans différents scénarios de profilage.