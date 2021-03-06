---
title: "Concepteur d’activités flowchart | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3bd8875fe9215f3ee8f0f187b84c0d38833764e3
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="flowchart-activity-designer"></a>Concepteur d'activités d'organigramme
L'activité <xref:System.Activities.Statements.Flowchart> permet de créer des flux de travail qui définissent et gèrent des contrôles de flux complexes. <xref:System.Activities.Statements.Flowchart> peut être créé dans le code ou à l'aide de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Cette rubrique explique comment utiliser [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. Le Concepteur d’activités de flux de travail Windows Workflow Designer permet aux développeurs de créer des workflows de façon naturelle.

## <a name="the-flowchart-activity"></a>Activité Flowchart
 <xref:System.Activities.Statements.Flowchart> spécifie une propriété <xref:System.Activities.Statements.Flowchart.StartNode%2A> unique exécutée lorsque le flux de travail démarre et utilise un réseau de propriétés <xref:System.Activities.Statements.Flowchart.Nodes%2A> liées pour créer des boucles arbitraires ou détourner le flux d'exécution ailleurs dans le flux de travail à un moment donné.

### <a name="using-the-flowchart-activity-designer"></a>Utilisation du concepteur d'activités Flowchart
 Le **organigramme** Concepteur d’activités peut être trouvé dans le **organigramme** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**onglet sur le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **organigramme** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface, là où les concepteurs d’activités sont généralement placés, en tant qu’une activité racine ou l’enfant d’une autre activité de flux de contrôle. Si le **organigramme** Concepteur d’activités est déposé sur une valeur vide [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] aire de conception, il crée un <xref:System.Activities.Statements.Flowchart> activité, qui s’affiche dans une vue développée dans laquelle le nœud de démarrage qui initialise l’exécution est par défaut représenté par une boule verte. Si le **organigramme** Concepteur d’activités est déposé dans une autre activité de flux de contrôle, il s’affiche dans une vue réduite qui peut être développée en double-cliquant sur le **organigramme** Concepteur d’activités. Toutes les activités dans le **boîte à outils** peuvent être déplacées directement sur le **organigramme** Concepteur d’activités, notamment d’autres activités de flux de contrôle.

 Après avoir fait glisser différents concepteurs d'activités sur la zone de dessin de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], les objets <xref:System.Activities.Activity> qu'ils représentent peuvent être liés pour spécifier l'ordre d'exécution. Pour créer un lien entre une activité source et une activité de destination, pointez la souris sur le concepteur de l'activité source pour faire apparaître des poignées carrées sur chacun de ses côtés. Cliquez sur l'une des poignées carrées et faites-la glisser, en maintenant le bouton de la souris enfoncé, vers l'une des poignées qui s'affiche de manière similaire autour de l'activité de destination lorsque vous pointez dessus avec la souris. Relâchez le bouton de la souris, un lien est créé entre ces deux activités, représenté par une flèche du concepteur source au concepteur de destination.

### <a name="flowchart-activity-properties"></a>Propriétés de l'activité Flowchart
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Flowchart> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire du concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom d'affichage du concepteur d'activités dans l'en-tête. La valeur par défaut est Flowchart. La valeur peut être modifiée dans le **propriétés** fenêtre ou directement dans l’en-tête du Concepteur d’activité.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Collection de variables dont l'étendue est limitée par cet objet <xref:System.Activities.Statements.Flowchart> pour partager l'état entre ses activités enfants.|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|Objet <xref:System.Activities.Statements.FlowNode> exécuté lorsque <xref:System.Activities.Statements.Flowchart> démarre.|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Contient la collection d'objets <xref:System.Activities.Statements.FlowNode> dans <xref:System.Activities.Statements.Flowchart>.|

## <a name="see-also"></a>Voir aussi

- [Organigramme](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)