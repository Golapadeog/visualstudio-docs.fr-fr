---
title: "CA1900 : Les champs de type valeur doivent être portables | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f023749c16a1c4fed36654036813007a83b21a72
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900 : Les champs de type valeur doivent être portables
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Category|Microsoft.Portability|  
|Modification avec rupture|Avec rupture - Si le champ peut être visible à l’extérieur de l’assembly.<br /><br /> Sans rupture - Si le champ n’est pas visible à l’extérieur de l’assembly.|  
  
## <a name="cause"></a>Cause  
 Cette règle vérifie que les structures déclarées avec une disposition explicite seront aligneront correctement lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 64 bits. IA-64 n’autorise pas les accès mémoire non alignés et le processus se bloquera si cette violation n’est pas résolue.  
  
## <a name="rule-description"></a>Description de la règle  
 Structures qui ont une disposition explicite qui contient des champs non alignés provoquent des incidents sur les systèmes d’exploitation 64 bits.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Tous les champs qui sont plus petits que 8 octets doivent avoir les décalages qui sont un multiple de leur taille et les champs qui sont de 8 octets ou plus doivent avoir des offsets qui sont un multiple de 8. Une autre solution consiste à utiliser `LayoutKind.Sequential` au lieu de `LayoutKind.Explicit`, si elle est raisonnable.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Cet avertissement doit être supprimé uniquement si elle se produit par erreur.