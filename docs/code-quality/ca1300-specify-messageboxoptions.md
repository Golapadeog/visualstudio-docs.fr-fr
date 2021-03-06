---
title: "CA1300 : Spécifier MessageBoxOptions | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b47c5f2297d9b13e33dc064a203bfd84ce2d196f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300 : Spécifier MessageBoxOptions
|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Category|Microsoft.Globalization|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode appelle une surcharge de la <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> méthode qui n’accepte pas un <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> argument.  
  
## <a name="rule-description"></a>Description de la règle  
 Pour afficher une boîte de message correctement pour les cultures qui utilisent un ordre de lecture de droite à gauche, le <xref:System.Windows.Forms.MessageBoxOptions> et <xref:System.Windows.Forms.MessageBoxOptions> membres de la <xref:System.Windows.Forms.MessageBoxOptions> énumération doit être passée à la <xref:System.Windows.Forms.MessageBox.Show%2A> (méthode). Examinez le <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> propriété du contrôle conteneur pour déterminer s’il faut utiliser un ordre de lecture de droite à gauche.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez une surcharge de la <xref:System.Windows.Forms.MessageBox.Show%2A> méthode qui accepte un <xref:System.Windows.Forms.MessageBoxOptions> argument.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque de code n’est pas localisée pour une culture qui utilise un ordre de lecture de droite à gauche.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode qui affiche une boîte de message qui contient les options qui conviennent pour l’ordre de lecture de la culture. Un fichier de ressources, ce qui n’est pas visible, est requis pour générer l’exemple. Suivez les commentaires de l’exemple pour générer l’exemple sans fichier de ressources et tester la fonctionnalité de droite à gauche.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Ressources dans des applications de bureau](/dotnet/framework/resources/index)