---
title: "Graphique d’activité GPU | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ed2b2d86300106f432e1202c9061676ed3aacc0b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gpu-activity-graph"></a>Graphique d'activité GPU
Le graphique d’activité GPU du visualiseur concurrentiel affiche le niveau d’activité DirectX du système. Cette activité se mesure par le nombre de moteurs DirectX qui sont utilisés dans le temps.  Le graphique n’affiche cependant pas quels moteurs sont utilisés.  Un moteur est considéré comme utilisé lorsqu’il traite un travail GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Couleurs du graphique d’activité GPU  
 Le vert indique la consommation des moteurs DirectX par le processus en cours.  
  
 Le gris clair indique l’utilisation des moteurs DirectX par d’autres processus sur le système. Pour réduire la consommation des moteurs DirectX par d’autres processus, réduisez le nombre des processus qui s’exécutent sur le système.  
  
 Le blanc indique la disponibilité des moteurs DirectX inutilisés sur le système. Ces moteurs sont disponibles pour votre processus si vous leur trouvez d’autres usages. Certains moteurs ne peuvent être utilisés que pour certains types de tâches.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Utilisation](../profiling/utilization-view.md)