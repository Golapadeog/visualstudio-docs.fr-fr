---
title: "CA2139 : Les méthodes transparentes ne peuvent pas utiliser l’attribut HandleProcessCorruptingExceptions | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3852955704bb218ac252d4c4c5edbbf1a0f5927c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139 : Les méthodes transparentes ne peuvent pas utiliser l'attribut HandleProcessCorruptingExceptions
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|  
|CheckId|CA2139|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode transparente est marquée avec le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attribut.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle déclenche toute méthode transparente qui essaie de gérer un exception qui endommage à l’aide de processus le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attribut. Un exception qui endommage de processus est une classification d’exception CLR version 4.0 des exceptions tel <xref:System.AccessViolationException>. L'attribut HandleProcessCorruptedStateExceptionsAttribute peut uniquement être utilisé par des méthodes critiques de sécurité et sera ignoré s'il s'applique à une méthode transparente. Pour gérer les exceptions qui endommagent un processus, cette méthode doit être critique de sécurité ou critique sécurisé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> d’attribut, ou marquez la méthode avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, une méthode transparente est marquée avec le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> d’attribut et échouera la règle. La méthode doit également être marquée avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.  
  
 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]