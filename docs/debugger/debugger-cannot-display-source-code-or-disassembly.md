---
title: "Débogueur ne peut pas afficher le Code Source ou code machine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8795ee33a5fc96c979cb67636d3ce5dd23c1b665
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Le débogueur ne parvient pas à afficher le code source ou le code machine
Cette erreur affiche le message suivant :  
  
 Le débogueur ne peut pas afficher le code source ou code machine de l'emplacement actuel où l'exécution s'est arrêtée.  
  
 Ce message d'erreur peut s'afficher pour plusieurs raisons :  
  
-   Vous avez peut-être atteint un point d'arrêt à un emplacement sans code source pendant le débogage d'un langage ne prenant pas en charge le code machine. Ouvrez le **points d’arrêt** fenêtre, recherchez le point d’arrêt et le supprimer.  
  
-   Si vous déboguez un script, vous avez peut-être atteint un point d'arrêt alors que votre programme n'avait pas de threads. Choisissez **étape** ou **continuer** à partir de la **déboguer** menu pour reprendre le débogage.  
  
-   Le débogueur n'a peut-être pas pu lire les informations de pile, de thread, de Registre et autres informations de contexte à partir du programme que vous déboguez pour des raisons de sécurité. Cela risque surtout de se produire si vous déboguez une application Web et que vous ne disposez pas des autorisations adéquates pour accéder au répertoire virtuel. Vous devez alors définir la sécurité du répertoire virtuel sur Anonyme, puis recommencer.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/index.md) [visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)