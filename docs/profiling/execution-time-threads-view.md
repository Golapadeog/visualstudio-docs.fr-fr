---
title: "Durée d’exécution (vue Threads) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 91fda110b3bf73b59d7c9d7d8ff6f7226f9ec5fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="execution-time-threads-view"></a>Durée d’exécution (vue Threads)
Ces segments de la chronologie de la vue Threads représentent la durée d’exécution, lorsque le thread effectue un travail sur un cœur logique du système.  
  
 Les changements d’état du thread sont détectés via les événements de changement de contexte du noyau. Le suivi d’événements pour Windows (ETW) capture des échantillons de piles chaque milliseconde. Dans un segment vert très court, il est possible qu’aucun échantillon ne soit capturé. Par conséquent, certains segments d’exécution courts peuvent ne pas afficher de pile d’appels.  
  
 Lorsque vous cliquez sur un segment d’exécution, le visualiseur concurrentiel affiche l’échantillon de pile le plus proche de l’emplacement du clic. L’emplacement de cet échantillon de pile est indiqué par une flèche noire (ou signe insertion) au-dessus de la chronologie. L’échantillon de pile apparaît également sous l’onglet **Actuel**.  
  
 Pour afficher un profil d’échantillonnage classique pour tous les segments d’exécution de la vue actuelle, cliquez sur **Exécution** dans le profil de la chronologie visible.  
  
## <a name="see-also"></a>Voir aussi  
 [Profil d’exécution, rapport](../profiling/execution-profile-report.md)   
 [Vue Threads](../profiling/threads-view-parallel-performance.md)