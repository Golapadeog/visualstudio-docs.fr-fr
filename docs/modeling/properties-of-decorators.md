---
title: "Propriétés des éléments décoratifs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, decorators
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 95338b26019a2faf2afc2eb6be019ac33d6ece3c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-decorators"></a>Propriétés des décorateurs
Éléments décoratifs sont des icônes, texte ou développer/réduire les chevrons qui peuvent s’afficher sur les formes ou des connecteurs du diagramme. Les tableaux suivants présentent les propriétés pour les trois types de decorator. Certaines propriétés s’affichent uniquement sur les éléments décoratifs de forme ou seulement sur des éléments décoratifs du connecteur.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Développer/réduire le Decorator  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|DisplayName|Le nom de l’élément décoratif qui s’affichera dans le concepteur généré.|Développez Collapse Decorator|  
|Name|Le nom de l’élément décoratif.|ExpandCollapseDecorator|  
|Notes|Notes informelles qui sont associés à cet élément décoratif.|\<none>|  
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|VerticalOffset|Le décalage vertical, par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|OffsetFromShape|Le décalage de l’élément décoratif de la forme, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|Position|La position par défaut de l’élément décoratif.|SourceTop|  
  
## <a name="icon-decorator"></a>Icône Decorator  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|DefaultIcon|Le chemin d’accès du fichier icône ou image à afficher.|\<none>|  
|DisplayName|Le nom de l’élément décoratif à afficher dans le concepteur généré.|Icône Decorator|  
|Name|Le nom de l’élément décoratif.|IconDecorator|  
|Notes|Notes informelles qui sont associés à l’élément décoratif.|\<none>|  
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|VerticalOffset|Le décalage vertical, par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|OffsetFromShape|Le décalage de l’élément décoratif de la forme, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|Position|La position par défaut de l’élément décoratif.|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|DefaultText|Le texte par défaut à afficher.|Ajouter des contrôles|  
|DisplayName|Le nom de l’élément décoratif à afficher dans le concepteur généré.|Ajouter des contrôles|  
|FontSize|La taille de police pour le texte qui s’affiche dans le decorator.|8|  
|FontStyle|Le style de police du texte qui s’affiche dans le decorator.|Normale|  
|Name|Le nom de l’élément décoratif.|Ajouter des contrôles|  
|Notes|Notes informelles qui sont associés à l’élément décoratif.|\<none>|  
|HorizontalOffset|Le décalage horizontal par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|VerticalOffset|Le décalage vertical, par rapport à la position par défaut de l’élément décoratif, exprimée en pouces. (Sur les formes uniquement.)|0|  
|OffsetFromLine|Le décalage de l’élément décoratif à partir de la ligne, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|OffsetFromShape|Le décalage de l’élément décoratif de la forme, par rapport à sa position par défaut, exprimée en pouces. (Sur les connecteurs uniquement.)|0|  
|Position|La position par défaut de l’élément décoratif.|TargetBottom|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)