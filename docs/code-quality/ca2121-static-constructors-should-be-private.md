---
title: "CA2121 : Les constructeurs statiques doivent être privés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 33770496c5d7585979d0be4198155982068957cf
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121 : Les constructeurs statiques doivent être privés
|||  
|-|-|  
|TypeName|StaticConstructorsShouldBePrivate|  
|CheckId|CA2121|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type a un constructeur statique n’est pas privé.  
  
## <a name="rule-description"></a>Description de la règle  
 Un constructeur statique, également appelé constructeur de classe, est utilisé pour initialiser un type. Le système appelle le constructeur statique avant la création de la première instance du type ou le référencement de tout membre statique. L’utilisateur n’a aucun contrôle sur lorsque le constructeur statique est appelé. Si un constructeur statique n’est pas privé, il peut être appelé par un code autre que le système. Selon les opérations effectuées dans le constructeur, cette possibilité peut provoquer un comportement inattendu.  
  
 Cette règle est appliquée par les compilateurs c# et Visual Basic.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Les violations sont généralement provoquées par une des actions suivantes :  
  
-   Vous défini un constructeur statique pour votre type et s’est pas rendu privé.  
  
-   Le compilateur de langage de programmation ajouté un constructeur statique par défaut à votre type et s’est pas rendu privé.  
  
 Pour résoudre le premier type de violation, rendez votre constructeur statique privé. Pour résoudre le second type, ajoutez un constructeur statique privé à votre type.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez pas ces violations. Si votre conception de logiciels requiert un appel explicite à un constructeur statique, il est probable que la conception présente des défauts graves et doit être examinée.