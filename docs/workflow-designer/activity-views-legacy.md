---
title: "Vues d’activité (héritées) | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 10661aa3f12b83a383defaa204b5bba0b93e236a
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="activity-views-legacy"></a>Vues d'activité (héritées)
Un grand nombre des activités fournies par [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], dans les workflows sont composés, a plusieurs vues de conception disponibles dans le Concepteur de flux de travail Windows hérité. Lorsque vous faites glisser un concepteur d’activités à partir de la **boîte à outils** sur l’aire de conception et par la suite chaque fois que vous sélectionnez l’activité, vous pouvez basculer entre les différents modes design à l’aide du **Workflow**menu ou en cliquant sur l’activité sélectionnée. De la même façon, lorsque vous déplacez le pointeur sur le nom d’une activité sélectionnée, un jeu déroulant d’onglets apparaît, que vous pouvez utiliser pour alterner entre les différentes vues.

 Chaque activité possède au moins une vue ; Il s’agit d’affichage par défaut lorsque vous faites glisser un concepteur d’activités à partir de la **boîte à outils** sur l’aire de conception. Cette vue par défaut d’activité est disponible en tant que le **afficher [type d’activité]** option sous l’onglet, par exemple et les menus **vue parallèle**. La plupart des activités possède des vues supplémentaires et des activités différentes peuvent posséder des vues différentes. Par exemple, le [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) activité possède la vue de compensation et la [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) activité comporte des événements d’une vue. La plupart des activités qui sont fournis avec Windows Workflow Foundation ont **afficher le Gestionnaire d’annulation** et **vue erreurs** concevoir des vues pour afficher le [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) et un [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) qui s’y rapportent.

 Le tableau suivant contient le nom et la description de chaque vue.

|Option de menu/d'onglet|Description|
|----------------------|-----------------|
|**Vue [type d’activité]**|Sélectionnez cette option de menu ou d'onglet pour afficher la représentation graphique par défaut de l'activité sélectionnée.|
|**Afficher le Gestionnaire d’annulation**|Sélectionnez cette option de menu ou d’onglet pour consulter les [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associé à l’activité sélectionnée.|
|**Afficher le Gestionnaire d’erreur**|Sélectionnez cette option de menu ou d’onglet pour consulter les [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associé à l’activité sélectionnée.|
|**Afficher le Gestionnaire de Compensation**|Sélectionnez cette option de menu ou d’onglet pour consulter les [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) associée [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|
|**Afficher le Gestionnaire d’événements**|Sélectionnez cette option de menu ou d’onglet pour consulter les [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) associée le [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|

 Pour plus d’informations sur des vues similaires, consultez [vues de Workflow séquentiel (héritées)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Voir aussi

- [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)
- [Vues Flux de travail séquentiels (hérité)](../workflow-designer/sequential-workflow-views-legacy.md)