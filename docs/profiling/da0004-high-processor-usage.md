---
title: "DA0004 : Utilisation intensive du processeur | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2612be6fd6980b6134c283ae0f6e6edf4155c955
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="da0004-high-processor-usage"></a>DA0004 : Utilisation intensive du processeur
|||  
|-|-|  
|ID de règle|DA0004|  
|Category|Utilisation des outils de profilage|  
|Méthodes de profilage|Instrumentation<br /><br /> Échantillonnage|  
|Message|L’utilisation de votre processeur est supérieure à 75 %. Utilisez le mode d’échantillonnage pour les applications utilisant le processeur de façon intensive.|  
|Type de règle|Information|  
  
 Lorsque vous effectuez un profilage à l’aide de la méthode d’échantillonnage, de mémoire .NET ou de conflit des ressources, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause  
 L’utilisation du processeur (UC) était très élevée dans les données de profilage qui ont été collectées à l’aide de la méthode d’instrumentation. Utilisez la méthode de profilage par échantillonnage lorsque vous profilez une application utilisant le processeur de manière intensive.  
  
## <a name="rule-description"></a>Description de la règle  
 Pendant cette exécution de profilage, le ou les processeurs étaient constamment très occupés. Une utilisation élevée du processeur peut indiquer qu’une application utilise le processeur de manière intensive. Les profils instrumentés ne sont généralement pas les plus efficaces pour étudier les scénarios d’utilisation du processeur. L’échantillonnage est généralement plus efficace lorsque vous profilez des applications qui consacrent beaucoup de temps à exécuter des instructions dans le processeur.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Profilez votre application à l’aide de la méthode d’échantillonnage au lieu de la méthode d’instrumentation, sauf si vous avez besoin de minutage de fonctions ou si vous êtes plus intéressé par les E/S que par les goulots d’étranglement du processeur.