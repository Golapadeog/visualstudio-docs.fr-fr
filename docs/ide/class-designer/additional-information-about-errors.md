---
title: "Informations supplémentaires sur les erreurs du Concepteur de classes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53b61b1fa49ffcbc047d47dd26586b45ae883c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="additional-information-about-class-designer-errors"></a>Informations supplémentaires sur les erreurs du Concepteur de classes
Le Concepteur de classes n'effectue pas le suivi de l'emplacement de vos fichiers sources ; par conséquent, si vous modifiez votre structure de projet ou si vous déplacez des fichiers sources dans votre projet, le Concepteur de classes peut perdre la trace du type (surtout le type de source d'un typedef, de classes de base ou de types d'associations). Vous pouvez recevoir une erreur telle que **Le Concepteur de classes n’est pas en mesure d’afficher ce type**. Dans ce cas, refaites glisser le code source modifié ou déplacé vers le diagramme de classes pour le réafficher.  
  
Vous pouvez obtenir de l'aide sur d'autres erreurs et avertissements dans les ressources suivantes :  
  
[Utilisation du code Visual C++](working-with-visual-cpp-code.md)  
Inclut des informations de dépannage sur l'affichage de C++ dans un diagramme de classes.  
  
[Forum du Concepteur de classes Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754)  
Propose un forum de questions relatives au Concepteur de classes.  
  
## <a name="see-also"></a>Voir aussi
[Conception et affichage des classes et des types](designing-and-viewing-classes-and-types.md)