---
title: "Xml (propriété dynamique XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b03c03ce5980b1c6042d1670d33d43fea6c7edc4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xml-xelement-dynamic-property"></a>Xml (propriété dynamique XElement)
Obtient le contenu XML sans mise en forme de l'élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 <xref:System.String> qui représente le contenu XML sans mise en forme de l'élément.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> de la classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, avec le paramètre `SaveOptions` défini à la valeur <xref:System.Xml.Linq.SaveOptions>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valeur](../designers/value-xelement-dynamic-property.md)