---
title: Configurer les retards de début de scénario pour un test de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 2802172d3ba959b489e5449351d40395abe712a6
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Configurer les retards de début de scénario dans les tests de charge

Spécifiez un délai avant le démarrage d'un scénario de test de charge dans l'éditeur de test de charge et la fenêtre Propriétés.

Par exemple, vous pouvez utiliser la propriété **Retarder l’heure de début**, si vous avez besoin qu’un scénario commence à produire des éléments consommés par un autre scénario. Vous pouvez retarder le scénario d'utilisation pour permettre au scénario de production de remplir certaines données.

Comme autre exemple, vous pouvez être amené à exécuter un scénario uniquement à une certaine heure de la journée. Par conséquent, vous voulez retarder le début du scénario pour simuler cette situation.

## <a name="specifying-the-delay-start-time-of-a-scenario"></a>Spécification du délai de démarrage d'un scénario

Vous pouvez spécifier un délai avant le début d’un scénario dans un test de charge en utilisant l’éditeur de test de charge pour changer la propriété **Retarder l’heure de début** dans la fenêtre Propriétés.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

 Par exemple, vous pouvez utiliser la propriété **Retarder l’heure de début** quand vous avez besoin qu’un scénario commence à produire des éléments consommés par un autre scénario. Vous pouvez retarder le scénario d'utilisation pour permettre au scénario de production de remplir certaines données.

 Comme autre exemple, vous pouvez être amené à exécuter un scénario uniquement à une certaine heure de la journée. Par conséquent, vous voulez retarder le début du scénario pour simuler cette situation.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des paramètres d’exécution et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Pour spécifier le retard de l'heure de début d'un scénario

1. Ouvrez un test de charge.

     L'Éditeur de test de charge s'affiche. L’arborescence du test de charge s’affiche.

2. Dans le dossier **Scénarios** des arborescences du test de charge, choisissez le nœud de scénario pour lequel vous souhaitez retarder l’heure de début.

3. Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario s'affichent dans la fenêtre Propriétés.

4. Dans la zone de texte de la propriété **Retarder l’heure de début**, tapez une valeur de temps qui indique la durée d’attente après le démarrage du test de charge et avant le début du scénario, quand le test de charge est exécuté.

    > [!NOTE]
    > Si la valeur de la propriété **Désactiver pendant le préchauffage** du scénario est **True**, la valeur de temps affectée à la propriété **Retarder l’heure de début** est appliquée après la période de préchauffage. Vous pouvez contrôler les scénarios inclus dans le préchauffage à l’aide de la propriété de scénario **Désactiver pendant le préchauffage**.

5. Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Retarder l’heure de début**.

## <a name="enabling-and-disabling-whether-a-scenario-runs-during-the-warm-up-period"></a>Activation et désactivation de l'exécution d'un scénario pendant la période de préchauffage

La propriété **Désactiver pendant le préchauffage** est définie dans la fenêtre Propriétés. La modification des propriétés du scénario de test de charge est définie à l'aide de l'Éditeur de test de charge.

 La propriété **Désactiver pendant le préchauffage** est utilisée pour indiquer si le scénario doit être exécuté ou non pendant la période de préparation spécifiée dans la propriété **Retarder l’heure de début**. Pour plus d’informations, consultez la procédure précédente [Spécification du délai de démarrage d’un scénario](../test/configure-scenario-start-delays.md#ConfiguringScenarioStartDelayHowTo).

> [!NOTE]
> Pour obtenir la liste complète des propriétés des paramètres d’exécution et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Pour activer ou désactiver la période de préparation d'un scénario

1. Ouvrez un test de charge.

     L’**éditeur de test de charge** s’affiche. L’arborescence du test de charge s’affiche.

2. Dans le dossier **Scénarios** des arborescences du test de charge, choisissez le nœud de scénario dont vous souhaitez spécifier les agents à utiliser.

3. Dans le menu **Affichage**, sélectionnez **Fenêtre Propriétés**.

     Les catégories et les propriétés du scénario sont affichées dans la fenêtre Propriétés.

     Dans la propriété **Désactiver pendant le préchauffage**, sélectionnez **True** ou **False**.

4. Après avoir changé la propriété, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge à l’aide de la nouvelle valeur associée à **Désactiver pendant le préchauffage**.

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Configurer les agents de test et les contrôleurs de test pour les tests de charge](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md)