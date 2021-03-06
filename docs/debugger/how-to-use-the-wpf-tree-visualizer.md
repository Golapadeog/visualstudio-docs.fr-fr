---
title: "Comment : utiliser le visualiseur de l’arborescence WPF | Documents Microsoft"
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
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78806b2ace7872db06ff403bcae28bb6eff21cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Comment : utiliser le visualiseur de l’arborescence WPF
Vous pouvez utiliser le visualiseur de l’arborescence WPF pour explorer l’arborescence d’éléments visuels d’un objet WPF et visualiser les propriétés de dépendance WPF pour les objets contenus dans cette arborescence. Pour plus d’informations sur l’arborescence d’éléments visuels, consultez [arborescences dans WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Pour plus d’informations sur les propriétés de dépendance, consultez [vue d’ensemble des propriétés de dépendance](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 Lorsque vous ouvrez le visualiseur de l’arborescence WPF, vous verrez deux volets : le **arborescence d’éléments visuels** sur la gauche et la **propriétés de** *nom***:**  *Type* volet de droite. Sélectionnez n’importe quel objet dans le **arborescence d’éléments visuels** volet et le **propriétés de** *nom***:***Type* volet est mise à jour automatiquement pour afficher les propriétés de cet objet.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Pour ouvrir le visualiseur de l’arborescence WPF  
  
1.  Dans un DataTip, **espion** fenêtre, **automatique** fenêtre, ou **variables locales** située en regard d’un nom d’objet WPF, cliquez sur la flèche en regard de l’icône de loupe.  
  
     Une liste de visualiseurs s'affiche.  
  
2.  Cliquez sur **visualiseur de l’arborescence WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Pour effectuer une recherche sur l’arborescence d’éléments visuels  
  
-   Dans le **arborescence d’éléments visuels** volet, tapez la chaîne que vous souhaitez rechercher dans le **recherche** boîte.  
  
     Le visualiseur de l’arborescence WPF recherche immédiatement le premier objet de l’arborescence d’éléments visuels qui correspond à la chaîne que vous avez tapée. Tapez plus de caractères pour rechercher une correspondance plus pertinente.  
  
    -   Pour accéder à la correspondance suivante de l’arborescence d’éléments visuels, cliquez sur **suivant**.  
  
    -   Pour revenir à la correspondance précédente, cliquez sur **Prev**.  
  
    -   Pour effacer les critères de recherche, cliquez sur **désactivez**.  
  
### <a name="to-search-the-properties-list"></a>Pour effectuer une recherche sur la liste des propriétés  
  
-   Dans le **propriétés de** *nom***:***Type* volet, tapez la chaîne à rechercher dans le **filtrer**boîte.  
  
     Le visualiseur de l’arborescence WPF recherche immédiatement les propriétés qui correspondent à la chaîne que vous avez tapée. À présent, la liste n’affiche que les propriétés correspondant à la chaîne que vous avez tapée. Tapez plus de caractères pour rechercher une correspondance plus pertinente.  
  
    -   Pour effacer les critères de recherche, cliquez sur **désactivez**.  
  
### <a name="to-close-the-visualizer"></a>Pour fermer le visualiseur  
  
-   Cliquez sur le **fermer** icône dans le coin supérieur droit de la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Arborescences dans WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Vue d’ensemble des propriétés de dépendance](/dotnet/framework/wpf/advanced/dependency-properties-overview)