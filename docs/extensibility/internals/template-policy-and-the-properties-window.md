---
title: "Stratégie de modèle et de la fenêtre Propriétés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 51735bf0f46e5a1ead6f989a8e75745ebc8e6e35
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="template-policy-and-the-properties-window"></a>Stratégie de modèle et de la fenêtre Propriétés
Lorsqu’un projet est contenu dans un projet de modèle d’entreprise, ce projet de modèle d’entreprise peut appliquer la stratégie. Stratégie de modèle devient un contrainte système qui peut être utilisé pour définir les valeurs par défaut pour les propriétés, masquer les propriétés, ajouter des propriétés et ainsi de suite.  
  
 À l’aide de la stratégie de modèle pour contrôler l’affichage des informations dans le **propriétés** fenêtre est différente de la mise en œuvre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>gère les propriétés de l’objet au niveau du composant, alors que la stratégie de modèle peut être utilisée pour limiter les propriétés de l’objet au niveau de la solution ou le projet. En d’autres termes  
  
-   Implémenter les méthodes sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> pour déterminer ce qui est affiché dans le **propriétés** fenêtre pour des objets spécifiques  
  
-   Utiliser la stratégie du modèle au niveau du projet et de solution pour déterminer ce qui est affiché dans le **propriétés** fenêtre pour les objets précédemment spécifiées  
  
 À l’aide de la stratégie de modèle pour limiter de façon sélective des propriétés spécifiques dans le **propriétés** fenêtre lorsqu’un élément de projet d’un type spécifié est sélectionné dans **l’Explorateur de solutions** peut être utile de tous les membres de l’équipe de développement travaille sur un projet. Par exemple, à l’aide de la stratégie de modèle, vous pouvez configurer toutes les informations de chaîne de connexion dans une base de données pour les développeurs et définir la chaîne de connexion en lecture seule. De cette façon, vous pouvez fournir un moyen simple pour vous assurer que chaque développeur utilise le chemin d’accès approprié pour accéder aux données.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)