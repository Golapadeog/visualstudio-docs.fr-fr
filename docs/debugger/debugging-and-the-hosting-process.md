---
title: "Le processus d’hébergement et de débogage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 01d4ebaada2c8ac65c1f44a5c80525f1b9e66a5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-and-the-hosting-process"></a>Débogage et processus d'hébergement
Le processus d'hébergement Visual Studio améliore la performance de débogueur et active de nouvelles fonctions de débogage, telles que le débogage de confiance partielle et l'évaluation d'une expression au moment du design. Vous pouvez désactiver le processus d’hébergement, le cas échéant. Pour plus d’informations, consultez [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md). Les sections suivantes décrivent certaines des différences entre le débogage avec et sans le processus d’hébergement.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Débogage de confiance partielle et sécurité ClickOnce  
 Le débogage de confiance partielle requiert le processus d'hébergement. Si vous désactivez le processus d’hébergement, le débogage de confiance partielle ne fonctionnera pas, même si la sécurité de confiance partielle est activée dans la page **Sécurité** de **Propriétés du projet**. Pour plus d’informations, consultez [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) et [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Évaluation de l’expression au moment du design  
 L'expression au moment du design utilise toujours le processus d'hébergement. La désactivation du processus d'hébergement dans **Propriétés du projet** désactive l'évaluation d'une expression au moment du design pour les projets Bibliothèque de classes. Pour d'autres types de projet, l'évaluation d'une expression au moment du design n'est pas désactivée. À la place, Visual Studio démarre le fichier exécutable réel et l'utilise pour l'évaluation au moment du design sans le processus d'hébergement. Cette différence peut produire des résultats différents.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Différences AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` retourne des résultats différents selon que le processus d'hébergement est activé ou non. Si vous appelez `AppDomain.CurrentDomain.FriendlyName` avec le processus d’hébergement activé, il retourne *nom_application*`.vhost.exe`. Si vous l’appelez avec le processus d’hébergement désactivé, il retourne *nom_application*`.exe`.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Différences Assembly.GetCallingAssembly().FullName  
 `Assembly.GetCallingAssembly().FullName` retourne des résultats différents selon que le processus d'hébergement est activé ou non. Si vous appelez `Assembly.GetCallingAssembly().FullName` avec le processus d’hébergement activé, il retourne `mscorlib`. Si vous appelez `Assembly.GetCallingAssembly().FullName` avec le processus d’hébergement désactivé, il retourne le nom d’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Processus d’hébergement (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Comment : déboguer une Application de confiance partielle](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Guide pratique pour désactiver le processus d’hébergement](../ide/how-to-disable-the-hosting-process.md)