---
title: "CA2002 : Ne verrouillent pas sur des objets à identité faible | Documents Microsoft"
ms.custom: 
ms.date: 01/31/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e27af6104b06b1f6a01ae6a98bfe88e8a0e967b1
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002 : Ne définissez pas un verrou sur des objets à identité faible

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un thread tente d’acquérir un verrou sur un objet qui a une identité faible.

## <a name="rule-description"></a>Description de la règle

Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet.

Les types suivants ont une identité faible et sont signalés par la règle :

- <xref:System.String>

- Tableaux de types valeur, y compris [types intégraux](/dotnet/csharp/language-reference/keywords/integral-types-table), [types à virgule flottante](/dotnet/csharp/language-reference/keywords/floating-point-types-table), et <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, utiliser un objet d’un type qui n’est pas dans la liste dans la section Description.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="related-rules"></a>Règles associées

[CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Exemple

L’exemple suivant montre des verrous d’objet qui enfreint la règle.

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>Voir aussi

<xref:System.Threading.Monitor>  
<xref:System.AppDomain>  
[Lock, instruction (c#)](/dotnet/csharp/language-reference/keywords/lock-statement)  
[SyncLock, instruction (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)