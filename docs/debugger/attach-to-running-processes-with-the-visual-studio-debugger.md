---
title: "Attacher au processus en cours d’exécution avec le débogueur dans Visual Studio | Documents Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 28126f9c832f55d63bd1b477599cf83ac8a57d59
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Attacher aux processus en cours d'exécution avec le débogueur Visual Studio
Vous pouvez attacher le débogueur Visual Studio à un processus en cours d’exécution sur un ordinateur local ou distant. Une fois le processus est en cours d’exécution, cliquez sur **Déboguer > Attacher au processus** (ou appuyez sur **CTRL + ALT + P**) pour ouvrir la **attacher au processus** boîte de dialogue.

Vous pouvez utiliser cette fonctionnalité pour déboguer des applications qui sont exécutent sur un ordinateur local ou distant, déboguer plusieurs processus simultanément ou déboguer une application qui n’a pas été créée dans Visual Studio. Il est souvent utile lorsque vous souhaitez déboguer une application, mais (pour une raison quelconque) vous n’avez pas démarré l’application à partir de Visual Studio avec le débogueur attaché. Par exemple, si vous exécutez l’application sans le débogueur et une exception d’accès, vous pourrez ensuite attacher au processus qui exécute l’application pour commencer le débogage.

> [!TIP]
> Ne savez pas si vous devez utiliser **attacher au processus** pour votre scénario de débogage ? Consultez [commune de scénarios de débogage](#BKMK_Scenarios). Si vous souhaitez déboguer les applications ASP.NET qui ont été déployés sur IIS, consultez [ASP.NET de débogage à distance sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a>Attacher à un processus en cours d’exécution sur l’ordinateur local  
 Pour pouvoir attacher à un processus, vous devez connaître le nom du processus (consultez [commune de scénarios de débogage](#BKMK_Scenarios) pour certains noms de processus courants).
  
1.  Dans Visual Studio, sélectionnez **Déboguer > Attacher au processus** (ou appuyez sur **CTRL + ALT + P**).

    Si vous souhaitez rapidement rattacher à un processus, consultez [rattachez au processus](#BKMK_reattach).
  
2.  Dans la boîte de dialogue **Attacher au processus** , recherchez le programme que vous voulez attacher dans la liste **Processus disponibles** .  

     Pour sélectionner rapidement le processus que vous souhaitez, tapez la première lettre du nom du processus. Si vous ne connaissez pas le nom de processus, consultez [commune de scénarios de débogage](#BKMK_Scenarios).
     
     ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
     Si le processus s’exécute sous un compte d’utilisateur différent, cochez la case **Afficher les processus de tous les utilisateurs** .
  
3.  Dans la zone **Attacher à** , vérifiez que le type de code à déboguer est répertorié. Le paramètre par défaut **Automatique** tente de déterminer le type de code que vous souhaitez déboguer. Pour définir le type de code manuellement, procédez comme suit :  
  
    1.  Dans la zone **Attacher à** , cliquez sur **Sélectionner**.  
  
    2.  Dans la boîte de dialogue **Sélectionner le type de code** , cliquez sur **Déboguer ces types de codes** et sélectionnez les types à déboguer.  
  
    3.  Cliquez sur **OK**.  
  
4.  Cliquez sur **Attacher**.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Attacher à un processus sur un ordinateur distant  
 Pour pouvoir attacher à un processus, vous devez connaître le nom du processus (consultez [commune de scénarios de débogage](#BKMK_Scenarios) pour certains noms de processus courants). Pour obtenir une aide plus complète pour les applications ASP.NET qui ont été déployés sur IIS, consultez [ASP.NET de débogage à distance sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Pour les autres applications, vous pourrez peut-être trouver le nom du processus dans le Gestionnaire des tâches.
  
 Quand vous utilisez la boîte de dialogue **Attacher au processus** , vous pouvez sélectionner un autre ordinateur configuré pour le débogage distant. Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md). Après avoir sélectionné un ordinateur distant, vous pouvez consulter une liste des processus disponibles exécutés sur cet ordinateur et attacher le débogueur à un ou plusieurs d’entre eux pour déboguer.
  
 **Pour sélectionner un ordinateur distant :**  

1. Dans Visual Studio, sélectionnez **Déboguer > Attacher au processus** (ou appuyez sur **CTRL + ALT + P**).

    Si vous souhaitez rapidement rattacher à un processus, consultez [rattachez au processus](#BKMK_reattach).

2.  Dans la boîte de dialogue **Attacher au processus** , sélectionnez le type de connexion approprié dans la liste **Transport** . Généralement, ce paramètre a la valeur**Défaut** .

    Le paramètre **Transport** persiste entre des sessions de débogage. 
  
3.  La zone de liste **Qualificateur** vous permet de sélectionner le nom de l’ordinateur distant à l’aide de l’une des méthodes suivantes :  
  
    1.  Tapez le nom dans la zone de liste **Qualificateur** .
    
        >**Remarque** si, dans les étapes ultérieures, vous ne peut pas se connecter en utilisant le nom de l’ordinateur distant, utilisez l’adresse IP. (Le numéro de port peut être automatiquement après avoir sélectionné le processus. Vous pouvez également l’entrer manuellement. Dans l’illustration ci-dessous, 4020 est le port par défaut pour le débogueur distant.)  

        Si vous souhaitez utiliser le **trouver** bouton, vous devrez peut-être [ouvrir le port UDP 3702](../debugger/remote-debugger-port-assignments.md) sur le serveur.
  
    2.  Cliquez sur la flèche de déroulement associée à la zone de liste **Qualificateur** , puis sélectionnez le nom de l’ordinateur dans la liste déroulante.  
  
    3.  Cliquez sur le bouton **Rechercher** en regard de la liste**Qualificateur** pour ouvrir la boîte de dialogue **Sélectionner une connexion du débogueur distant** . La boîte de dialogue **Sélectionner une connexion du débogueur distant** répertorie tous les appareils qui se trouvent sur votre sous-réseau local, et les éventuels appareils directement connectés à votre ordinateur via un câble Ethernet. Cliquez sur l’ordinateur ou l’appareil souhaité, puis sur **Sélectionner**. 
  
     Le paramètre **Qualificateur** persiste entre des sessions de débogage uniquement si une connexion de débogage réussie est établie avec ce qualificateur.
     
4.  Cliquez sur **Actualiser**.

      La liste **Processus disponibles** s’affiche automatiquement quand vous ouvrez la boîte de dialogue **Processus** . Les processus peuvent démarrer et s’interrompre en arrière-plan pendant que la boîte de dialogue est ouverte. Toutefois, le contenu n’est pas toujours actualisé. Vous pouvez actualiser la liste à tout moment pour visualiser la liste des processus en cours d’exécution en cliquant sur **Actualiser**. 
     
4.  Dans la boîte de dialogue **Attacher au processus** , recherchez le programme que vous voulez attacher dans la liste **Processus disponibles** .

     Pour sélectionner rapidement le processus que vous souhaitez, tapez la première lettre du nom du processus. Si vous ne connaissez pas le nom de processus, consultez [commune de scénarios de débogage](#BKMK_Scenarios).
  
     Si le processus s’exécute sous un compte d’utilisateur différent, cochez la case **Afficher les processus de tous les utilisateurs** .
     
5.  Cliquez sur **Attacher**.

## <a name="BKMK_reattach"></a>Rattachez au processus

Vous pouvez rattacher rapidement à des processus qui vous ont été précédemment attaché en choisissant **Déboguer > rattacher à un processus en cours...** (**Maj + Alt + P**). Lorsque vous choisissez cette commande, le débogueur immédiatement tente de se joindre à la dernière des processus attachés à l’aide du **attacher au processus** boîte de dialogue.

Le débogueur sera rattacher en tentant d’abord de faire correspondre l’ID de processus précédent, puis, si cette tentative échoue, en faisant correspondre le nom de processus précédent. Si aucune correspondance n’est trouvée, ou s’il existe plusieurs processus portent le même nom, puis le **attacher au processus** boîte de dialogue s’affiche afin que vous puissiez sélectionner le processus correct.

> [!NOTE]
> Le **rattachez au processus** commande est une nouveauté de Visual Studio 2017.

## <a name="additional-info"></a>Informations supplémentaires

Vous pouvez attacher un débogueur à plusieurs programmes à la fois, mais un seul d’entre eux est actif dans le débogueur à un moment donné. Vous pouvez définir le programme actif dans la barre d’outils **Emplacement de débogage** ou la fenêtre **Processus** .  
  
Si vous essayez d’établir un attachement à un processus appartenant à un compte d’utilisateur non fiable, une boîte de dialogue d’avertissement de sécurité s’affiche avec un message de confirmation. Pour plus d’informations, consultez [avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations ci-dessous semblent suspectes ou si vous n’êtes pas sûr, n’attachez pas ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
Dans certains cas, lors du débogage dans une session Bureau à distance (services Terminal Server), la liste **Processus disponibles** n’affiche pas tous les processus disponibles. Si vous exécutez Visual Studio avec un compte d’utilisateur limité, la liste **Processus disponibles** n’affiche pas les processus qui s’exécutent dans la session 0, qui est utilisée pour les services et les autres processus serveur, notamment w3wp.exe. Vous pouvez résoudre le problème en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sous un compte administrateur ou en exécutant [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à partir de la console du serveur au lieu d’une session Terminal Server. Si aucune de ces solutions de contournement n’est possible, la troisième option consiste à attacher le débogueur au processus en exécutant `vsjitdebugger.exe -p` *ProcessId* à partir de la ligne de commande Windows. Vous pouvez déterminer l’ID de processus à l’aide de tlist.exe. Pour obtenir tlist.exe, téléchargez et installez les outils de débogage pour Windows, qui sont disponibles dans  [Téléchargements relatifs au WDK et à WinDbg](http://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a>Scénarios de débogage courants

Pour vous aider à déterminer si vous devez utiliser **attacher au processus** et identifier les processus à attacher, quelques scénarios de débogage courants sont indiquées ici (la liste n’est pas exhaustive). Lorsque des instructions plus détaillées sont disponibles, nous fournissons des liens.

Pour certains types d’application (par exemple, les applications UWP), ne pas attacher directement à un nom de processus, mais utilisez le **déboguer le Package d’application installé** plutôt l’option de menu (voir tableau).

> [!NOTE]
> Pour plus d’informations sur la base de débogage dans Visual Studio, consultez [mise en route avec le débogueur](../debugger/getting-started-with-the-debugger.md).

|Scénario|Déboguer (méthode)|Nom du processus|Notes et des liens|
|-|-|-|-|
|Déboguer une application managée ou native sur l’ordinateur local|Utilisez attacher au processus ou [de débogage standard](../debugger/getting-started-with-the-debugger.md)|*appname*.exe|Pour accéder rapidement à la boîte de dialogue, utilisez **CTRL + ALT + P** puis tapez la première lettre du nom du processus.|
|Déboguer des applications ASP.NET sur l’ordinateur local après avoir démarré l’application sans le débogueur|Utilisez attacher au processus|iiexpress.exe|Cela peut être utile pour que votre application charge plus rapidement, telles que (par exemple) lors du profilage. |
|Débogage distant ASP.NET 4 ou 4.5 sur un serveur IIS|Utiliser les outils distants et attacher au processus|w3wp.exe|Consultez [ASP.NET de débogage à distance sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Débogage distant ASP.NET Core sur un serveur IIS|Utiliser les outils distants et attacher au processus|dotnet.exe|Déploiement d’applications, consultez [publier sur IIS](https://docs.asp.net/en/latest/publishing/iis.html). Pour le débogage, consultez [distant débogage ASP.NET Core sur un ordinateur IIS distant](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Déboguer d’autres types d’application pris en charge sur un processus serveur|Utilisez les outils à distance (si le serveur est à distance) et l’attacher au processus|Iexplore.exe ou autres processus|Si nécessaire, utilisez le Gestionnaire des tâches pour aider à identifier le processus. Consultez [débogage distant](../debugger/remote-debugging.md) et des sections plus loin dans cette rubrique|
|Débogage à distance une application de bureau Windows|Outils à distance et F5|N/A| Consultez [débogage distant](../debugger/remote-debugging.md)|
|Une application universelle (UWP), OneCore, HoloLens et IoT de débogage à distance|Déboguer le package d’application installé|N/A|Consultez [déboguer un Package d’application installé](debug-installed-app-package.md) au lieu d’utiliser **attacher au processus**|
|Déboguer une application Windows universelle (UWP), OneCore, HoloLens, IoT application ou que vous n’avez pas démarrer à partir de Visual Studio|Déboguer le package d’application installé|N/A|Consultez [déboguer un Package d’application installé](debug-installed-app-package.md) au lieu d’utiliser **attacher au processus**|  
  
> [!NOTE]
>  Pour que le débogueur s’attache au code écrit en C++, le code doit émettre `DebuggableAttribute`. Vous pouvez ajouter cela automatiquement à votre code grâce à la liaison, à l'aide de l'option [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

## <a name="what-debugger-features-can-i-use"></a>Les fonctionnalités du débogueur puis-je utiliser ?

Pour utiliser toutes les fonctionnalités du débogueur Visual Studio (par exemple, en appuyant sur les points d’arrêt) lors de l’attachement à un processus, l’exécutable doit correspondre exactement à votre source locale et des symboles (autrement dit, le débogueur doit être en mesure de charger la bonne [(.pbd) fichiers de symboles ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Par défaut, cela requiert une version debug.

Pour les scénarios de débogage à distance, vous devez disposer du code source (ou une copie du code source) déjà ouvert dans Visual Studio. Les fichiers binaires d’application compilé sur l’ordinateur distant doivent provenir de la même build que sur l’ordinateur local.

Dans certains scénarios de débogage locales, vous pouvez déboguer dans Visual Studio sans accès à la source si les fichiers de symboles corrects sont présents à l’application (par défaut, cela requiert une version debug). Pour plus d’informations, consultez [spécifier les symboles et les fichiers de code Source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a>Résoudre les erreurs d’attachement  
 Quand le débogueur est attaché à un processus en cours d’exécution, le processus peut contenir un ou plusieurs types de code. Les types de code auxquels le débogueur peut s’attacher sont affichés et sélectionnés dans la boîte de dialogue **Sélectionner le type de code** .  
  
 Parfois, le débogueur peut réussir à s’attacher à un type de code, mais pas aux autres. Cela peut se produire si vous tentez d’attacher le débogueur à un processus exécuté sur un ordinateur distant. Il est possible que des composants de débogage distant soient installés pour certains types de code, mais pas pour d’autres, sur l’ordinateur distant. Cela peut également se produire si vous tentez d’attacher le débogueur à plusieurs processus pour déboguer directement la base de données. Le débogage SQL prend en charge l’attachement à un seul processus uniquement.  
  
 Si le débogueur peut être attaché à certains des types de code, mais pas à tous, un message identifie les types auxquels il n’a pas pu être attaché.  
  
 Si le débogueur parvient à s’attacher à au moins un type de code, vous pouvez procéder au débogage du processus. Vous pouvez uniquement déboguer les types de code attachés avec succès. L’exemple de message précédent indique que le type de code de script n’a pas réussi à s’attacher. Il vous sera donc impossible de déboguer le code de script se trouvant dans le processus. Le code de script continuera de s’exécuter dans le processus, mais vous ne pourrez pas définir des points d’arrêt, afficher des données ni réaliser d’autres opérations de débogage dans le script.  
  
 Si vous souhaitez des informations plus spécifiques sur l’incapacité du débogueur à s’attacher à un type de code, vous pouvez tenter d’attacher à nouveau le débogueur uniquement à ce type de code.  
  
 **Pour obtenir des informations spécifiques sur la raison de l’échec de l’attachement d’un type de code**  
  
1.  Procédez au détachement du processus. Dans le menu **Déboguer** , cliquez sur **Détacher tout**.  
  
2.  Rattachez le processus en sélectionnant un seul type de code.  
  
    1.  Dans la boîte de dialogue **Attacher au processus** , sélectionnez le processus dans la liste **Processus disponibles** .  
  
    2.  Cliquez sur **Sélectionner**.  
  
    3.  Dans la boîte de dialogue **Sélectionner le type de code** , sélectionnez **Déboguer ces types de codes** et le type de code qui a échoué lors de l’attachement. Effacez tout autre code.  
  
    4.  Cliquez sur **OK**. La boîte de dialogue **Sélectionner le type de code** se ferme.  
  
    5.  Dans la boîte de dialogue **Attacher au processus** , cliquez sur **Attacher**.  
  
     Cette fois-ci, l’attachement échoue entièrement et un message d’erreur spécifique s’affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer plusieurs processus](../debugger/debug-multiple-processes.md)   
 [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Débogage à distance](../debugger/remote-debugging.md)