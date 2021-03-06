---
title: Modèles de charge pour les tests de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, load patterns
- load tests, scenarios
- load tests, virtual users
ms.assetid: 0ba0363b-7f50-4bde-a919-0e3bce7bc115
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 986b2e263a5beedf7f40ed36526365735b3ba17f
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="edit-load-patterns-to-model-virtual-user-activities"></a>Modifier les modèles de charge en modèle d’activités des utilisateurs virtuels

Les propriétés du modèle de charge spécifient le mode d’ajustement de la charge utilisateur simulée pendant un test de charge. Visual Studio propose trois modèles de charge intégrés : constant, dans l’étape et en fonction des objectifs. Vous choisissez le modèle de charge et ajustez les propriétés aux niveaux appropriés à vos objectifs de test de charge.

Le modèle de charge est un composant d’un scénario. Les scénarios et leurs modèles de charge définis comportent un test de charge.

> [!NOTE]
> Dans tous les modèles de charge, la charge générée par Visual Studio est une charge simulée d’utilisateurs virtuels.

## <a name="load-patterns"></a>Modèles de charge

### <a name="constant"></a>Constante

 Le modèle de charge constant est utilisé pour spécifier une charge utilisateur qui ne change pas pendant le test de charge. Par exemple, lorsque vous effectuez un test de détection de fumée (smoke test) sur une application Web, vous souhaiterez peut-être définir une charge légère et constante de 10 utilisateurs.

#### <a name="constant-load-pattern-considerations"></a>Considérations sur un modèle de charge constant

 Un modèle de charge constant est utilisé pour exécuter la même charge utilisateur pendant l’exécution d’un test de charge. Soyez très prudent lorsque vous utilisez un modèle de charge constant dont le nombre d'utilisateurs est élevé ; vous risquez de solliciter de manière déraisonnable et irréaliste votre serveur ou vos serveurs de test de charge. Par exemple, si votre test de charge contient un test Web qui démarre avec une requête vers une page d'accueil et que vous configurez le test de charge avec une charge constante de 1 000 utilisateurs, le test de charge soumet les 1 000 premières requêtes à la page d'accueil aussi rapidement que possible. La simulation d'accès réel à votre site Web peut paraître peu réaliste. Pour minimiser ce problème, pensez à utiliser un modèle de charge par étape qui passe progressivement à 1 000 utilisateurs ou spécifiez une période de préparation dans les paramètres d’exécution des tests de charge. Si une période de préparation est spécifiée, le test de charge augmentera automatiquement la charge de manière progressive pendant la période de préparation. Pour plus d’informations, consultez [Configuration des délais de démarrage des scénarios](../test/configure-scenario-start-delays.md).

### <a name="step"></a>Étape

 Le modèle de charge par étape est utilisé pour spécifier une charge utilisateur qui augmente avec le temps jusqu’à une charge utilisateur maximale définie. Pour les charges par étape, vous spécifiez le **Nombre initial d’utilisateurs**, le **Nombre maximal d’utilisateurs**, la **Durée de l’étape (secondes)** et le **Nombre d’utilisateurs dans l’étape**.

 Par exemple, une charge par étape avec un compte **Nombre initial d’utilisateurs** de 1, un **Nombre maximal d’utilisateurs** de 100, une **Durée de l’étape (secondes)** de 10 et un **Nombre d’utilisateurs dans l’étape** de 1 crée un modèle de charge utilisateur qui commence à 1, augmente de 1 toutes les 10 secondes jusqu’à atteindre 100 utilisateurs.

> [!NOTE]
>  Si la durée de test totale est plus courte que la durée nécessaire pour atteindre la charge utilisateur maximale, le test s'arrête après la durée écoulée et n'atteint pas la cible Nombre maximal d'utilisateurs.

 Vous pouvez utiliser l'objectif d'étape pour augmenter la charge jusqu'à ce que le serveur atteigne un point auquel les performances diminuent considérablement. À mesure que la charge augmente, le serveur finit par manquer de ressources. La charge d'étape est une bonne méthode pour déterminer le nombre d'utilisateurs auquel cela se produit. Avec la charge par étape, vous devez également surveiller attentivement les ressources des agents, afin de vous assurer que ces derniers sont capables de générer la charge souhaitée.

 En règle générale, vous devez exécuter plusieurs séries de tests qui présentent des durées d'étape et un nombre d'utilisateurs dans l'étape différents afin de pouvoir obtenir de bonnes mesures pour une charge donnée. Souvent, les charges montrent un pic initial pour chaque étape à mesure que des utilisateurs sont ajoutés. La maintenance de la charge à ce taux vous permet de mesurer les performances du système après que le système a récupéré du pic initial.

#### <a name="step-load-pattern-considerations"></a>Considérations sur le modèle de charge par étape

 Un modèle de charge dans l'étape peut être utilisé pour augmenter la charge sur le ou les serveurs au cours de l'exécution du test de charge. Il permet d'apprécier l'évolution des performances au fur et à mesure que la charge utilisateur augmente. Par exemple, pour voir les performances de votre serveur ou de vos serveurs lorsque la charge utilisateur passe à 2 000 utilisateurs, vous pouvez exécuter un test de charge de 10 heures à l'aide d'un modèle de charge par étape dont les propriétés sont les suivantes :

-   Nombre initial d'utilisateurs : 100

-   Nombre maximal d'utilisateurs : 2 000

-   Durée de l'étape (secondes) : 1 800

-   Durée de démarrage de l'étape (secondes) : 20

-   Nombre d'utilisateurs dans l'étape : 100

 Ces paramètres exécutent le test de charge pendant 30 minutes (1 800 secondes) avec des charges utilisateur de 100, 200, 300 et jusqu'à 2 000 utilisateurs. La propriété **Durée de démarrage de l’étape** vaut mention spéciale, parce que c’est l’une des seules propriétés qui n’est pas disponible pour la sélection dans l’Assistant Nouveau test de charge. Cette propriété autorise le passage progressif à l'étape suivante (par exemple de 100 à 200 utilisateurs), et non immédiat. Dans l'exemple, la charge utilisateur passerait de 100 à 200 utilisateurs sur une période de 20 secondes (soit une augmentation de cinq utilisateurs par seconde). Pour plus d’informations, consultez [Guide pratique pour spécifier la propriété de la durée de démarrage de l’étape d’un modèle de charge par étape](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md).

### <a name="goal-based"></a>En fonction des objectifs

 Un modèle de charge basé sur des objectifs est semblable au modèle par étape, mais il ajuste la charge utilisateur en fonction des seuils de compteurs de performance par rapport aux ajustements de charge utilisateur périodiques. Les charges basées sur des objectifs sont utiles dans différents cas :

-   Optimiser la sortie des agents : mesurez la mesure de limite clé sur l'agent pour optimiser la sortie des agents. En général, il s'agit de l'UC ; toutefois, il peut également s'agir de la mémoire.

-   Atteindre un certain niveau de ressources cible (en général UC) sur le serveur cible, puis mesurer le débit à ce niveau. Vous pouvez ainsi effectuer des comparaisons série à série du débit en fonction d'un niveau constant d'utilisation de ressources sur le serveur.

-   Atteindre un niveau de débit cible sur le serveur.

 Le tableau suivant présente un exemple de modèle basé sur les objectifs avec les paramètres de propriété suivants :

|Groupe de propriétés|Propriété|Value|
|--------------------|--------------|-----------|
|Compteur de performance|Category|Processeur|
|Compteur de performance|Ordinateur|ContosoServer1|
|Compteur de performance|Counter|% temps processeur|
|Compteur de performance|Instance|_Total|
|Plage cible pour le compteur de performance|Extrémité supérieure|90|
|Plage cible pour le compteur de performance|Extrémité inférieure|70|
|Limites du nombre d'utilisateurs|Nombre initial d'utilisateurs|1|
|Limites du nombre d'utilisateurs|Nombre maximal d'utilisateurs|100|
|Limites du nombre d'utilisateurs|Décrément maximal du nombre d'utilisateurs|5|
|Limites du nombre d'utilisateurs|Incrément maximal du nombre d'utilisateurs|5|
|Limites du nombre d'utilisateurs|Nombre minimal d'utilisateurs|1|

 Ces paramètres font en sorte que **l’analyseur de test de charge** ajuste la charge utilisateur entre 1 et 100 pendant une série de tests, de sorte que le **Compteur** pour `% Processor Time` du WebServer01 varie entre `70%` et `90%.`

 La taille de chaque ajustement de charge utilisateur est déterminée par les paramètres **Incrément maximal du nombre d’utilisateurs** et **Décrément maximal du nombre d’utilisateurs**. Les limites de nombre d’utilisateurs sont définies par les propriétés **Nombre maximal d’utilisateurs** et **Nombre minimal d’utilisateurs**.

#### <a name="goal-based-load-pattern-considerations"></a>Considérations sur le modèle de charge en fonction des objectifs

 Un modèle de charge en fonction des objectifs est utile pour déterminer le nombre d’utilisateurs que votre système peut prendre en charge avant d’atteindre un certain niveau d’utilisation des ressources. Cette option fonctionne mieux lorsque vous avez déjà identifié la ressource limitative (autrement dit, le goulot d'étranglement) dans votre système.

 Par exemple, supposez que vous sachiez que la ressource limitative dans votre système est l'UC de votre serveur de base de données, et donc vous souhaitez connaître le nombre d'utilisateurs qui peut être pris en charge lorsque l'UC du serveur de base de données est saturée à 75 % environ. Vous pourriez utiliser un modèle de charge en fonction des objectifs dont l'objectif est de conserver la valeur du compteur de performance « % temps processeur » entre 70 % et 80 %.

 À surveiller également la présence d'une autre ressource limitant le débit du système. Ces ressources peuvent nuire à réalisation de l’objectif spécifié par le modèle de charge en fonction des objectifs. En outre, la charge utilisateur continue d’augmenter jusqu’à ce que la valeur définie pour **Nombre maximal d’utilisateurs** soit atteinte. Il ne s’agit pas généralement de la charge désirée ; soyez donc prudent lorsque vous choisissez le compteur de performance dans le modèle de charge en fonction des objectifs.

## <a name="tasks"></a>Tâches

|Tâches|Rubriques associées|
|-----------|-----------------------|
|**Spécifier le modèle de charge initiale pour votre test de charge :** Quand vous créez un test de charge à l’aide de l’Assistant Nouveau test de charge, vous sélectionnez un modèle de charge.|-   [Changement du modèle de charge](../test/edit-load-patterns-to-model-virtual-user-activities.md#EditingLoadPatternsChanging)|
|**Modification du modèle de charge de votre test de charge :** Après avoir créé votre test de charge, vous pouvez modifier le modèle de charge dans l’éditeur de test de charge.|-   [Guide pratique pour spécifier la propriété de la durée de démarrage de l’étape d’un modèle de charge par étape](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|
|**Spécification si les utilisateurs virtuels dans votre scénario de test de charge doivent inclure les données en cache du site web :** Vous pouvez changer la propriété **Pourcentage de nouveaux utilisateurs** pour définir le mode de simulation par le test de charge de la mise en cache web qui serait exécutée par un navigateur web pour les utilisateurs virtuels.|-   [Guide pratique pour spécifier le pourcentage des utilisateurs virtuels qui utilisent les données du cache web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)|
|**Spécification du temps de démarrage de l’étape pour un modèle de charge par étape :** La propriété **Durée de démarrage de l’étape** autorise le passage progressif, et non immédiat, d’une étape à l’autre (par exemple de 100 à 200 utilisateurs).|-   [Guide pratique pour spécifier la propriété de la durée de démarrage de l’étape d’un modèle de charge par étape](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)|

## <a name="changing-the-load-pattern"></a>Modification du modèle de charge

 Après avoir créé votre test de charge avec **l’Assistant Nouveau test de charge**, vous pouvez utiliser **l’éditeur de test de charge** pour changer les propriétés du modèle de charge associé à un scénario en fonction des niveaux qui répondent à vos objectifs de test.

> [!NOTE]
>  Pour obtenir une liste complète des propriétés de scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

 Un modèle de charge spécifie le nombre d’utilisateurs virtuels actifs pendant un test de charge et le taux auquel de nouveaux utilisateurs sont ajoutés. Vous pouvez choisir parmi les trois modèles disponibles : étape, constante et en fonction des objectifs. Pour plus d’informations, consultez [Spécification du nombre d’utilisateurs virtuels avec des modèles de charge dans un scénario de test de charge](../test/edit-load-patterns-to-model-virtual-user-activities.md).

> [!NOTE]
>  Vous pouvez également modifier par programmation vos propriétés de charge à l'aide d'un plug-in de test de charge. Pour plus d’informations, consultez [Guide pratique pour créer un plug-in de test de charge](../test/how-to-create-a-load-test-plug-in.md).

### <a name="to-change-the-load-pattern"></a>Pour modifier le modèle de charge

1.  Ouvrez un test de charge.

2.  Dans **l’éditeur de test de charge**, dans le dossier Scénarios, développez le scénario pour lequel vous souhaitez modifier le modèle de charge, puis choisissez le modèle de charge.

    > [!NOTE]
    > Le libellé du nœud du modèle de charge, tel qu’il s’affiche dans l’arborescence de scénarios de votre test de charge, reflète le profil de charge que vous avez choisi lors de la création du test de charge. Il peut s’agir d’un **profil de charge constante** ou d’un **profil de charge dans l’étape**.

3.  Appuyez sur **F4** pour afficher la fenêtre Propriétés.

     Les catégories **Modèle de charge** et **Paramètres** sont affichées dans la fenêtre Propriétés.

4.  (Facultatif) Changez la propriété **Modèle** dans la catégorie **Modèle de charge**.

     Les choix disponibles pour la propriété **Modèle** sont **Étape**, **Constante** et **En fonction des objectifs**. Pour plus d’informations sur les types de modèles de charge, consultez [Spécification du nombre d’utilisateurs virtuels avec des modèles de charge dans un scénario de test de charge](../test/edit-load-patterns-to-model-virtual-user-activities.md).

5.  (Facultatif) Dans la catégorie **Paramètres**, changez les valeurs.

    > [!NOTE]
    > Les valeurs que vous pouvez définir pour **Paramètres** varient en fonction de la valeur qui a été sélectionnée pour la propriété **Modèle**.

6.  Quand vous avez fini de changer les propriétés, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez exécuter ensuite votre test de charge avec le nouveau modèle de charge.

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)
- [Guide pratique pour spécifier le pourcentage des utilisateurs virtuels qui utilisent les données du cache web](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md)
- [Guide pratique pour spécifier la propriété de la durée de démarrage de l’étape d’un modèle de charge par étape](../test/how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern.md)