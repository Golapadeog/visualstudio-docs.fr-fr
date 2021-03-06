---
title: "Tâche XSD | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5d0324b3e72cfffb73e22b3995cfc9458631e7d5
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="xsd-task"></a>Tâche XSD
Encapsule l’outil Définition du schéma XML (xsd.exe), qui génère des fichiers de schéma ou de classe à partir d’une source.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **XSD**.  
  
-   **AdditionalOptions**  
  
     Paramètre **String** facultatif.  
  
     Liste des options comme indiqué sur la ligne de commande. Par exemple, « */option1 /option2 /option#* ». Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **XSD**.  
  
-   **GenerateFromSchema**  
  
     Paramètre **String** facultatif.  
  
     Indique les types qui sont générés à partir du schéma spécifié.  
  
     Spécifiez l’une des valeurs suivantes, chacune d’elles correspondant à une option XSD.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Language**  
  
     Paramètre **String** facultatif.  
  
     Spécifie le langage de programmation à utiliser pour le code généré.  
  
     Vous avez le choix entre **CS** (C#, qui est la valeur par défaut), **VB** (Visual Basic) ou **JS** (JScript). Vous pouvez également spécifier un nom qualifié complet pour une classe qui implémente `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
-   **Namespace**  
  
     Paramètre **String** facultatif.  
  
     Spécifie l'espace de noms du runtime pour les types générés.  
  
-   **Sources**  
  
     Paramètre `ITaskItem[]` requis.  
  
     Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.  
  
-   **SuppressStartupBanner**  
  
     Paramètre **booléen** facultatif.  
  
     Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.  
  
-   **TrackerLogDirectory**  
  
     Paramètre **String** facultatif.  
  
     Spécifie le répertoire du journal de Tracker.  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)