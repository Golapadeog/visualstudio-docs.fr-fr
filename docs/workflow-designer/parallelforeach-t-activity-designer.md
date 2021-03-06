---
title: "ParallelForEach&lt;T&gt; Concepteur d’activités | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4d8a46b2535c976bbfe490f85fc5cc5fd6082bc7
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt; Concepteur d’activités
L'activité <xref:System.Activities.Statements.ParallelForEach%601> énumère les éléments d'une collection et, pour chacun d'eux, exécute en parallèle une instruction incorporée, qui se trouve de façon asynchrone sur le même thread. Utilisez cette activité de contrôle de flux au lieu de l'activité <xref:System.Activities.Statements.Sequence> si ses activités enfants sont censées devenir inactives.

 L'activité <xref:System.Activities.Statements.ParallelForEach%601> a une propriété <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> qui contient une expression [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] spécifiée par l'utilisateur. L'activité <xref:System.Activities.Statements.ParallelForEach%601> évalue cette propriété après l'exécution de chaque branche. Si elle a la valeur **true**, puis le <xref:System.Activities.Statements.ParallelForEach%601> activité se termine sans exécuter d’autres branches. Si le <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> ne correspond pas à **true**, puis le <xref:System.Activities.Statements.ParallelForEach%601> activité se termine lorsque toutes ses activités enfants sont terminées.

## <a name="the-parallelforeacht-activity"></a>Le ParallelForEach < T\> activité
 L'activité <xref:System.Activities.Statements.ParallelForEach%601> énumère ses valeurs et planifie la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> pour chaque valeur énumérée. Elle planifie seulement la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. La manière dont le corps s'exécute dépend de l'inactivation de la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>.

 Si la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> ne devient pas inactive, son exécution s'effectue dans l'ordre inverse, car les activités planifiées sont gérées comme une pile, la dernière activité planifiée s'exécutant en premier. Par exemple, si vous avez une collection {1,2,3,4} dans <xref:System.Activities.Statements.ParallelForEach%601> et utiliser un **WriteLine** comme corps pour écrire la valeur. L'impression suit l'ordre 4, 3, 2, 1 dans la console. C’est parce que **WriteLine** ne devient pas inactif, après 4 **WriteLine** activités planifiées, elles exécutées à l’aide d’un comportement de la pile (première dernier sorti).

 Par contre, si des activités dans la propriété <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> peuvent devenir inactives, par exemple une activité <xref:System.ServiceModel.Activities.Receive> ou <xref:System.Activities.Statements.Delay>, Il n'est pas nécessaire d'attendre qu'elles soient terminées. <xref:System.Activities.Statements.ParallelForEach%601> accède à l'activité de corps planifiée suivante et l'exécute. Si cette activité devient inactive à son tour, <xref:System.Activities.Statements.ParallelForEach%601> passe de nouveau à l'activité de corps suivante.

### <a name="using-the-parallelforeacht-activity-designer"></a>À l’aide de la ParallelForEach\<T > Concepteur d’activités
 Le **ParallelForEach\<T >** Concepteur d’activités peut être trouvé dans le **flux de contrôle** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le  **Boîte à outils** onglet sur le côté gauche de la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (ou bien, sélectionnez **barre d’outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le **ParallelForEach\<T >** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface partout où les concepteurs d’activités sont généralement placés, pour exemple, à l’intérieur d’un **séquence** Concepteur d’activités. Une fois déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], il crée un <xref:System.Activities.Statements.ParallelForEach%601> activité, laquelle contient par défaut un <xref:System.Activities.Activity.DisplayName%2A> de **ParallelForEach < Int32\>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\> propriétés dans le Concepteur de flux de travail
 Le tableau suivant répertorie les propriétés les plus utiles de l'activité <xref:System.Activities.Statements.ParallelForEach%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom d'affichage convivial du concepteur d'activités dans l'en-tête. La valeur par défaut est **ParallelForEach\<Int32 >**. La valeur peut être modifiée si vous le souhaitez dans le **propriétés** grille ou directement dans l’en-tête du Concepteur d’activité.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Activité à exécuter pour chaque élément dans la collection. Pour ajouter le <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> activité, déposez une activité à partir de la boîte à outils dans le **corps** zone sur le **ParallelForEach\<T >** Concepteur d’activités avec le texte d’indication « Déposer l’activité ici ».|
|**TypeArgument**|True|Le type des éléments dans le <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> collection spécifiée par le paramètre générique *T*. Par défaut, **TypeArgument** a la valeur **Int32**. Pour modifier le type T dans le **ParallelForEach < T\>**  Concepteur d’activités, modifiez la valeur de la **TypeArgument** zone de liste déroulante dans la grille des propriétés.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|Collection d’éléments à itérer. Pour définir le <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, tapez un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] expression dans le **valeurs** zone sur le **ForEach < T\>**  Concepteur d’activités dans la zone avec le texte d’indication « Entrer une expression VB » ou dans **Valeurs** zone sur le **propriétés** fenêtre.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Propriété évaluée à l'issue de chaque itération. Si sa valeur est True, les itérations en attente planifiées sont annulées. Si cette propriété n'est pas définie, toutes les instructions planifiées s'exécutent jusqu'à ce qu'elles soient terminées.|

 Par défaut, l'itérateur de boucle est nommé « item ». Vous pouvez modifier le nom de la variable d’itérateur dans la **ForEach** zone **ParallelForEach\<T >** Concepteur d’activités. L'itérateur de boucle peut être utilisé dans des expressions dans les enfants de l'activité <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>Voir aussi

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)