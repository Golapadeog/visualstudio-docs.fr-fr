---
title: "CA1716 : Les identificateurs ne doivent pas correspondre aux mots clés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4feb6293675437307e9ebd95b13457ef7439d5e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés
|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un nom d’un espace de noms, un type ou un membre d’interface ou virtuel correspond à un mot clé réservé dans un langage de programmation.  
  
## <a name="rule-description"></a>Description de la règle  
 Identificateurs des espaces de noms, types et virtuels et les membres d’interface ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le common language runtime. Selon le langage utilisé et le mot clé, ambiguïtés et les erreurs du compilateur peuvent rendre la bibliothèque difficile à utiliser.  
  
 Cette règle vérifie par rapport aux mots clés dans les langues suivantes :  
  
-   Visual Basic  
  
-   C#  
  
-   C++/CLI  
  
 Comparaison respectant la casse est utilisé pour [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] les mots clés et une comparaison respectant la casse est utilisé pour les autres langues.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Sélectionnez un nom qui n’apparaît pas dans la liste de mots clés.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Vous pouvez supprimer un avertissement de cette règle si vous êtes sûr que l’identificateur sera confondez pas les utilisateurs de l’API, et que la bibliothèque est utilisable dans toutes les langues disponibles dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].