---
title: "Guide pratique pour modifier le répertoire de sortie de la génération | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 14aad8b82a3757fecb1d449a671fc07c2582bb5f
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-change-the-build-output-directory"></a>Guide pratique pour modifier le répertoire de sortie de la génération
Vous pouvez spécifier l’emplacement de sortie en fonction de la configuration (débogage, version ou les deux) généré par votre projet.  
  
> [!NOTE]
>  Si vous possédez un **projet d’installation** , lisez la remarque à la fin de cet article.  
  
## <a name="changing-the-build-output-directory"></a>Modification du répertoire de sortie de génération  
  
#### <a name="to-change-the-build-output-directory"></a>Pour modifier le répertoire de sortie de génération  
  
1.  Dans la barre de menus, choisissez **Projet**, *Propriétés* **nom_application**. Vous pouvez également cliquer avec le bouton droit sur le nœud du projet dans l' **Explorateur de solutions** , puis sélectionner **Propriétés**.  
  
2.  Si vous avez un projet Visual Basic, sélectionnez l'onglet **Compiler** . Si vous avez un projet C#, sélectionnez l'onglet **Générer**. Si vous avez un projet C++ ou un projet JavaScript, sélectionnez l'onglet **Général** .  
  
3.  Dans la liste déroulante de configuration située dans la partie supérieure, choisissez la configuration pour laquelle vous voulez modifier l’emplacement du fichier de sortie (débogage, version ou tout).  
  
     Recherchez l'entrée de chemin de sortie (**Chemin de sortie de la génération** en Visual Basic, **Répertoire de sortie** en Visual C++, **Chemin de sortie** en JavaScript et C#). Spécifiez un nouveau répertoire de sortie de génération relatif au répertoire du projet.  
  
> [!NOTE]
>  Dans un projet d’installation, la zone **Nom du fichier de sortie** permet uniquement de modifier l’emplacement du fichier Setup.exe, et non l’emplacement des fichiers du projet. Pour plus d'informations, consultez **Build, propriétés de configuration, boîte de dialogue Propriétés du projet de déploiement**.  
  
## <a name="see-also"></a>Voir aussi  
 [Générer, page du Concepteur de projets (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [Général, page de propriétés (Projet)](/cpp/ide/general-property-page-project)   
 [Compilation et génération](../ide/compiling-and-building-in-visual-studio.md)