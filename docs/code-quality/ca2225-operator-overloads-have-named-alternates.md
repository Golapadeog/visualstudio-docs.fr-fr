---
title: "CA2225 : Les surcharges d’opérateur ont nommées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f8c7b71fc964f898aefc5e243c787be71a8a063a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées
|||  
|-|-|  
|TypeName|OperatorOverloadsHaveNamedAlternates|  
|CheckId|CA2225|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée.  
  
## <a name="rule-description"></a>Description de la règle  
 Surcharge d’opérateur autorise l’utilisation de symboles pour représenter des calculs pour un type. Par exemple, un type qui surcharge le signe plus (+) pour l’addition aurait en général un membre de substitution nommé 'Add'. Le membre de substitution nommé donne accès à la même fonctionnalité que l’opérateur et est fourni pour les développeurs qui programment dans les langages qui ne prennent pas en charge les opérateurs surchargés.  
  
 Cette règle examine les opérateurs répertoriés dans le tableau suivant.  
  
|C#|Visual Basic|C++|Nom de remplacement|  
|---------|------------------|-----------|--------------------|  
|+ (binaire)|+|+ (binaire)|Ajouter|  
|+=|+=|+=|Ajouter|  
|&|Et|&|BitwiseAnd|  
|&=|Et =|&=|BitwiseAnd|  
|&#124;|Ou|&#124;|BitwiseOr|  
|&#124;=|Ou =|&#124;=|BitwiseOr|  
|--|N/A|--|Décrémentation|  
|/|/|/|Diviser|  
|/=|/=|/=|Diviser|  
|==|=|==|Equals|  
|^|Xor|^|Xor|  
|^=|XOR =|^=|Xor|  
|>|>|>|Comparer|  
|>=|>=|>=|Comparer|  
|++|N/A|++|Incrémentation|  
|<>|!=|Equals|  
|<<|<<|<<|LeftShift|  
|<<=|<<=|<<=|LeftShift|  
|<|<|<|Comparer|  
|<=|<=|\<=|Comparer|  
|&&|N/A|&&|LogicalAnd|  
|&#124;&#124;|N/A|&#124;&#124;|LogicalOr|  
|!|N/A|!|LogicalNot|  
|%|Mod|%|Mod ou reste|  
|%=|N/A|%=|Mod|  
|* (binaire)|*|*|Multiplier|  
|*=|N/A|*=|Multiplier|  
|~|pas|~|OnesComplement|  
|>>|>>|>>|MAJ|  
=|N/A|>>=|MAJ|  
|-(binaire)|-(binaire)|-(binaire)|Soustraire|  
|-=|N/A|-=|Soustraire|  
|true|IsTrue|N/A|IsTrue (propriété)|  
|-(unaire)|N/A|-|Inverser le signe|  
|+ (unaire)|N/A|+|signe plus|  
|False|IsFalse|False|IsTrue (propriété)|  
  
 N/a == ne peut pas être surchargé dans la langue sélectionnée.  
  
 La règle vérifie également les opérateurs de cast implicites et explicites dans un type (`SomeType`) en recherchant les méthodes nommées `ToSomeType` et `FromSomeType`.  
  
 En c#, lorsqu’un opérateur binaire est surchargé, l’opérateur d’assignation correspondant, le cas échéant, est également implicitement surchargé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez la méthode de remplacement pour l’opérateur. nom à l’aide de l’autre nom recommandée.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle si vous implémentez une bibliothèque partagée. Les applications peuvent ignorer un avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit une structure qui enfreint cette règle. Pour corriger l’exemple, ajoutez un public `Add(int x, int y)` méthode à la structure.  
  
 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1046 : Ne pas surcharger l’opérateur égal sur les types de référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224 : Remplacez Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218 : Remplacez GetHashCode lors du remplacement de Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)