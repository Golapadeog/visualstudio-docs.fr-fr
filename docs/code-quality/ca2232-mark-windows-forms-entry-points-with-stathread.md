---
title: "CA2232 : Points d’entrée marque Windows Forms avec STAThread | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fe12ce5947a22414aaf07c59945fd667b106101f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232 : Marquez les points d'entrée Windows Forms avec STAThread
|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un assembly fait référence à la <xref:System.Windows.Forms> espace de noms et son point d’entrée n’est pas marqué avec le <xref:System.STAThreadAttribute?displayProperty=fullName> attribut.  
  
## <a name="rule-description"></a>Description de la règle  
 <xref:System.STAThreadAttribute>Indique que le modèle pour l’application de thread COM est à thread unique cloisonné. Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement. Si l’attribut n’est pas présent, l’application utilise le modèle de cloisonnement multithread, ce qui n’est pas prise en charge pour les Windows Forms.  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]les projets qui utilisent l’infrastructure d’Application n’ont pas marquer le **Main** méthode avec STAThread. Le [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilateur effectue automatiquement.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez le <xref:System.STAThreadAttribute> attribut au point d’entrée. Si le <xref:System.MTAThreadAttribute?displayProperty=fullName> attribut est présent, supprimez-le.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si vous développez pour le .NET Compact Framework, pour laquelle le <xref:System.STAThreadAttribute> attribut est inutiles et non pris en charge.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent l’utilisation correcte de <xref:System.STAThreadAttribute>.  
  
 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]