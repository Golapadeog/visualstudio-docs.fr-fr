---
title: Onglet Actuel | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: eb69f11081015960cd79d54fb90893a9202c9bae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="current-tab"></a>Onglet Actuel
En cliquant sur l’onglet **Actuel**, vous pouvez voir la pile des appels (si disponible) qui est la plus proche du point de sélection actuel dans la chronologie si un segment de thread de processeur est sélectionné.  Dans ce cas, le point de sélection est représenté par une flèche noire, ou point d’insertion, au-dessus de la chronologie. Lorsqu’un segment de blocage est sélectionné, le point d’insertion n’est pas affiché, car il n’y a pas d’exécution. Toutefois, le segment est encore sélectionné et une pile des appels est affichée.  
  
 L’onglet **Actuel** affiche également des informations sur les segments d’activité DirectX, les marqueurs et les accès d’E/S.  Pour les segments d’activité DirectX, des informations sur la façon dont les paquets DMA sont traités par la file d’attente matérielle sont affichées.  Pour les marqueurs, une description et des informations de type sont affichées.  Pour les accès d’E/S, des informations sur le fichier et le nombre d’octets lus ou écrits sont affichées.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)