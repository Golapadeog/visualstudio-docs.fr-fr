---
title: "Propriétés des relations de domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c2fe3f843a6247c93e3fa8f75ea66fe824561d83
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-domain-relationships"></a>Propriétés des relations de domaine
Les propriétés dans le tableau suivant sont associées à une relation de domaine. Pour plus d’informations sur les relations de domaine, consultez [fonctionnement des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Modificateur d'accès|Le niveau d’accès de la relation de domaine (`public` ou `internal`).|`public`|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de la relation de domaine.|\<none>|  
|Génère deux dérivées|Si `True`, une classe de base et une classe partielle (pour la personnalisation par des remplacements) est généré. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|A constructeur personnalisé|Si `True`, indique qu’un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substituer et étendre les Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir de la relation de domaine (`none`, `abstract` ou `sealed`).|\<none>|  
|Autorise les doublons|Si `True`, des liens en double de la relation de domaine peuvent être créées entre les deux mêmes éléments.|`False`|  
|Relations de base|Si la relation de domaine est dérivée, la relation de la base de la relation de domaine.|\<none>|  
|Est de l’incorporation|Si `True`, la relation de domaine est une relation d’incorporation. Si `False`, la relation est une relation de référence.|\<both>|  
|Name|Le nom de la relation de domaine.|Nom actuel|  
|Espace de noms|L’espace de noms n’est affilié à la relation de domaine.|Espace de noms actuel|  
|Notes|Notes informelles qui sont associés à la relation de domaine.|\<none>|  
|Description|La description qui est utilisée pour documenter du code et est utilisée dans l’interface utilisateur du concepteur généré.|\<none>|  
|Nom complet|Le nom qui s’affiche dans le concepteur généré pour la relation de domaine.|\<none>|  
|Help Keyword|Le mot clé facultatif qui sert à l’index d’aide (F1) pour la relation de domaine.|\<none>|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)