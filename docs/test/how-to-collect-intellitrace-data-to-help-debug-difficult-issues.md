---
title: Données IntelliTrace dans Visual Studio | Microsoft Docs
ms.date: 10/13/2016
ms.topic: article
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 04c4c1cd4429228ffa90e06ac9675901602c3cd0
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Comment : collecter des données IntelliTrace pour aider au débogage des problèmes difficiles

Vous pouvez configurer l’adaptateur de données de diagnostic pour IntelliTrace pour collecter des informations de trace de diagnostic spécifiques dans Visual Studio. Avec cet adaptateur, le test peut collecter des événements de diagnostic significatifs pouvant être utilisés ultérieurement par un développeur pour repérer la cause d'un bogue dans le code. L'adaptateur de données de diagnostic pour IntelliTrace peut être utilisé pour des tests manuels ou automatisés.

> [!NOTE]
> IntelliTrace fonctionne uniquement sur une application écrite avec du code managé. Si vous testez une application Web qui utilise un navigateur comme client, vous ne devez pas activer IntelliTrace pour ce client dans vos paramètres de test, car aucun code managé n'est disponible pour effectuer le suivi. Dans ce cas, vous pouvez configurer un environnement pour collecter des données IntelliTrace à distance sur votre serveur web.

Les données IntelliTrace sont stockées dans un fichier ayant une extension .iTrace. Si vous exécutez votre test et qu'une de ses étapes échoue, vous pouvez créer un bogue. Le fichier IntelliTrace qui contient les informations de diagnostic est automatiquement joint à ce bogue.

> [!NOTE]
> L'adaptateur de données de diagnostic pour IntelliTrace ne crée pas de fichier IntelliTrace en cas de réussite du test. Un fichier est enregistré uniquement si un cas de test échoue ou lorsque vous signalez un bogue.

 Les données collectées dans le fichier IntelliTrace accroissent l'efficacité du débogage en réduisant le temps nécessaire à la reproduction et au diagnostic d'une erreur dans le code. En outre, étant donné que vous pouvez partager le fichier IntelliTrace avec une autre personne qui peut répliquer votre session locale sur son ordinateur, la probabilité d'un bogue non reproductible est réduite.

> [!NOTE]
> Si vous activez IntelliTrace dans vos paramètres de test, la collecte des données de couverture du code ne fonctionnera pas.

> [!WARNING]
> L'adaptateur de données de diagnostic pour IntelliTrace fonctionne en instrumentant un processus managé, qui doit être exécuté après le chargement des tests de la série. Si le processus que vous souhaitez contrôler a déjà été lancé, aucun fichier IntelliTrace ne sera collecté car le processus est déjà en cours d'exécution. Pour éviter ce problème, assurez-vous que le processus est arrêté avant le chargement des tests. Ensuite, démarrez le processus après le chargement des tests ou le démarrage du premier test.

 La procédure suivante décrit comment configurer les données IntelliTrace que vous souhaitez collecter. Ces étapes valent aussi bien pour l’éditeur de configuration de Microsoft Test Manager que pour la boîte de dialogue Paramètres de test de Visual Studio.

> [!NOTE]
> Le compte d’utilisateur de l’agent de test qui est utilisé pour collecter les données IntelliTrace doit être membre du groupe Administrateurs. Pour plus d’informations, consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Configurer les données à collecter avec l'adaptateur de données de diagnostic IntelliTrace

Avant d’effectuer les opérations décrites dans cette procédure, vous devez ouvrir vos paramètres de test à partir de Microsoft Test Manager ou de Visual Studio, puis sélectionner la page **Données et diagnostics**.

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Pour configurer les données à collecter avec l'adaptateur de données de diagnostic IntelliTrace

1.  Sélectionnez le rôle à utiliser pour collecter les données IntelliTrace.

2.  Sélectionnez **IntelliTrace**.

3.  Si vous ajoutez IntelliTrace pour un rôle de client web ou pour une application web ASP.NET, vous devez également sélectionner **Proxy client ASP.NET pour IntelliTrace et l’impact de test**.

     Ce proxy vous permet de collecter des informations sur les appels http d’un client à un serveur web pour les adaptateurs de données de diagnostic d’impact de test et IntelliTrace.

    > [!WARNING]
    > Si vous décidez d'utiliser un compte personnalisé pour l'identité utilisée pour le pool d'applications sur Internet Information Server (IIS) où vous envisagez de collecter des données Intellitrace, vous devez créer le profil utilisateur local sur l'ordinateur IIS pour le compte personnalisé utilisé. Vous pouvez créer le profil local pour le compte personnalisé en vous ouvrant localement une session sur l'ordinateur IIS ou en exécutant la ligne de commande suivante à l'aide des informations d'identification du compte personnalisé :
    >
    > **runas /user:domain\name /profile cmd.exe**

4.  Choisissez **Configurer** pour **qu’IntelliTrace** modifie les paramètres IntelliTrace par défaut.

     La boîte de dialogue pour configurer les données collectées s'affiche.

    > [!WARNING]
    > Si vous activez la collecte de données IntelliTrace, la collecte des données de couverture du code ne fonctionnera pas.

5.  Choisissez l’onglet **Général**. Sélectionnez **Événements IntelliTrace uniquement** pour enregistrer des événements de diagnostic significatifs qu ont un impact minimal sur les performances lors de vos tests.

     **-**ou-

     Sélectionnez **Événements IntelliTrace et informations d’appels** pour enregistrer des événements de diagnostic et le traçage au niveau de la méthode affichant des informations sur les appels. Ce niveau de traçage peut avoir un impact sur les performances lorsque vous exécutez vos tests.

6.  Pour collecter des données à partir de votre application ASP.NET qui s’exécute sur Internet Information Services, sélectionnez **Collecter des données à partir d’une application ASP.NET exécutée sur Internet Information Services**. Installez et configurez votre agent de test sur le rôle serveur Web. Consultez [Installer et configurer des agents de test](../test/lab-management/install-configure-test-agents.md).

7.  Choisissez l’onglet **Modules**. Sélectionnez **Collecter les données de tous les modules à l’exception des suivants**, et utilisez **Ajouter** pour ajouter un module à la liste et **Supprimer** pour supprimer un module. Cette option vous permet d'inclure tous les modules en cours d'exécution sur le système, à l'exception des modules que vous spécifiez.

     - ou -

     Sélectionnez **Collecter les données des modules suivants uniquement**, et utilisez **Ajouter** pour ajouter un module à la liste et **Supprimer** pour supprimer un module. Cette option vous permet de spécifier quels modules doivent être utilisés.

    > [!NOTE]
    > Si possible, sélectionnez les processus spécifiques que vous souhaitez surveiller. Cela est recommandé pour une performance optimale.

8.  Choisissez l’onglet **Processus**. Sélectionnez **Collecter les données de tous les processus à l’exception des suivants**, et utilisez **Ajouter** pour ajouter un processus à la liste et **Supprimer** pour supprimer un processus. Cette option vous permet d'inclure tous les processus qui s'exécutent sur le système, à l'exception des processus que vous spécifiez.

     - ou -

     Sélectionnez **Collecter les données des processus spécifiés uniquement**, et utilisez **Ajouter** pour ajouter un processus à la liste et **Supprimer** pour supprimer un processus. Cette option vous permet de spécifier quels processus doivent être utilisés.

9. (Facultatif) Choisissez l’onglet **Événements IntelliTrace**. Activez ou désactivez chaque catégorie d’événement IntelliTrace à inclure ou exclure lorsque vous collectez des événements de diagnostic.

10. (Facultatif) Développez chaque catégorie d’événement IntelliTrace et activez ou désactivez chaque événement spécifique à inclure ou exclure dans les événements IntelliTrace.

11. (Facultatif) Choisissez l’onglet **Avancé**. Ensuite, cliquez sur la flèche à côté de **Quantité maximale d’espace disque pour chaque enregistrement** et sélectionnez l’espace maximal que le fichier IntelliTrace doit utiliser.

    > [!NOTE]
    > Si vous augmentez la taille de l'enregistrement, un problème de délai d'expiration peut se produire lorsque vous enregistrez cet enregistrement avec vos résultats de test. Pour plus d’informations sur l’augmentation des valeurs du délai d’expiration pour les adaptateurs de données de diagnostic, consultez [Guide pratique pour éviter les dépassements des délais d’expiration des adaptateurs de données de diagnostic](../test/how-to-prevent-time-outs-for-diagnostic-data-adapters.md).

12. Si vous utilisez Microsoft Test Manager, choisissez **Enregistrer**. Si vous utilisez Visual Studio, choisissez **OK**. Les paramètres IntelliTrace sont maintenant configurés et enregistrés pour vos paramètres de test.

    > [!NOTE]
    > Pour réinitialiser la configuration de cet adaptateur de données de diagnostic, choisissez **Rétablir la configuration par défaut** pour Visual Studio ou **Rétablir les valeurs par défaut** pour Microsoft Test Manager.

## <a name="see-also"></a>Voir aussi

- [Collecter les données de diagnostic pendant les tests (VSTS)](/vsts/manual-test/collect-diagnostic-data)
- [Collecter des données de diagnostic dans des tests manuels (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)
- [Collecter des informations de diagnostic avec des paramètres de test](../test/collect-diagnostic-information-using-test-settings.md)
- [Collecter les données IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)