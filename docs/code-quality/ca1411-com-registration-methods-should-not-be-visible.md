---
title: "CA1411 : Les méthodes d’inscription COM ne doivent pas être visibles | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43b1f340b62726edc33b3e7e05d52634c2a2595b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411 : Les méthodes d'inscription COM ne doivent pas être visibles
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Category|Microsoft.Interoperability|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode qui est marquée avec la <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribut est visible de l’extérieur.  
  
## <a name="rule-description"></a>Description de la règle  
 Lorsqu’un assembly est enregistré avec COM Component Object Model (), les entrées sont ajoutées au Registre pour chaque type visible par COM dans l’assembly. Les méthodes marquées avec le <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> et <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> attributs sont appelés pendant les processus d’inscription et d’annulation d’inscription, respectivement, pour exécuter le code utilisateur qui est spécifique à l’inscription/de la désinscription de ces types. Ce code ne doit pas être appelé en dehors de ces processus.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez l’accessibilité de la méthode à `private` ou `internal` (`Friend` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux méthodes qui enfreint la règle.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1410 : Les méthodes d’inscription COM doivent être mises en correspondance](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Inscription d’assemblys dans COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (outil d’inscription d’assemblys)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)