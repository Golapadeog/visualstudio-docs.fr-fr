---
title: "CA2227 : Les propriétés de la Collection doivent être en lecture seule | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a1835c5e600320ec8b36102e4749d92cf21eae1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227 : Les propriétés de collection doivent être en lecture seule
|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une propriété accessible en écriture extérieurement visible est un type qui implémente <xref:System.Collections.ICollection?displayProperty=fullName>. Tableaux, les indexeurs (propriétés portant le nom 'Item') et les jeux d’autorisations sont ignorés par la règle.  
  
## <a name="rule-description"></a>Description de la règle  
 Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection complètement différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis. Si le remplacement de la collection est un objectif, le modèle de conception par défaut consiste à inclure une méthode pour supprimer tous les éléments de la collection et une méthode pour remplir la collection. Consultez le <xref:System.Collections.ArrayList.Clear%2A> et <xref:System.Collections.ArrayList.AddRange%2A> méthodes de la <xref:System.Collections.ArrayList?displayProperty=fullName> classe pour obtenir un exemple de ce modèle.  
  
 Binaire et la sérialisation XML prend en charge les propriétés en lecture seule qui sont des collections. Le <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> classe a des exigences spécifiques pour les types qui implémentent <xref:System.Collections.ICollection> et <xref:System.Collections.IEnumerable?displayProperty=fullName> afin d’être sérialisables.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez la propriété en lecture seule et, si la conception impose, ajouter des méthodes pour effacer et de remplir à nouveau la collection.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type avec une propriété de collection accessible en écriture et montre comment la collection peut être remplacée directement. En outre, la meilleure manière de remplacer une propriété de collection en lecture seule à l’aide de `Clear` et `AddRange` méthodes s’affiche.  
  
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md)