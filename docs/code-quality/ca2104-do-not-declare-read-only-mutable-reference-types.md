---
title: "CA2104 : Ne déclarez pas les types référence mutables uniquement en lecture | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bbd12d09c95f1ec93c7232901270cfbece311693
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104 : Ne déclarez pas les types référence mutables en lecture seule
|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Category|Microsoft.Security|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type visible de l’extérieur contient un champ en lecture seule visible de l’extérieur qui constitue un type référence mutable.  
  
## <a name="rule-description"></a>Description de la règle  
 Un type mutable est un type dont les données d’instance peuvent être modifiées. La <xref:System.Text.StringBuilder?displayProperty=fullName> classe est un exemple d’un type référence mutable. Il contient des membres qui peuvent modifier la valeur d’une instance de la classe. Est un exemple d’un type référence immuable la <xref:System.String?displayProperty=fullName> classe. Une fois qu’il a été instancié, sa valeur ne peut jamais changer.  
  
 Le modificateur en lecture seule ([readonly](/dotnet/csharp/language-reference/keywords/readonly) en c#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], et [const](/cpp/cpp/const-cpp) en C++) sur un type référence de champ (pointeur en C++) empêche le champ remplacé par une autre instance du type référence. Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le type de référence.  
  
 Les champs de tableau en lecture seule sont exemptés de cette règle, mais au lieu de cela provoque une violation de la [CA2105 : les champs de tableau ne doivent pas être lu uniquement](../code-quality/ca2105-array-fields-should-not-be-read-only.md) règle.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le modificateur en lecture seule, ou si une modification avec rupture est acceptable, remplacez le champ par un type immuable.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si le type de champ est immuable.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une déclaration de champ qui provoque une violation de cette règle.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]