---
title: IDebugDocumentText (Interface) | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9522d1075cd796fb69f6abbc42adc2706a817fed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText, interface
Fournit l’accès à une version texte du document de débogage. Cette interface utilise les conventions suivantes :  
  
-   Les positions de caractère et les numéros de ligne sont de base zéro.  
  
-   Positions de caractère représentent des offsets de caractères ; elles ne représentent des octets ou les décalages de word. Pour Win32, une position de caractère est un offset de Unicode.  
  
 Outre les méthodes héritées de `IDebugDocument`, le `IDebugDocumentText` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Retourne les attributs du document.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Retourne le nombre de lignes et le nombre de caractères dans le document.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Retourne la position de caractère correspondant au premier caractère d’une ligne.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Retourne le numéro de ligne et, éventuellement, l’offset de caractère dans la ligne qui correspond à la position de caractère spécifiée.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Récupère les caractères et/ou les attributs de caractères associés à une plage de la position de caractère.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Retourne la plage de la position de caractère correspondant à un contexte de document.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Crée un objet de contexte de document correspondant à la plage de position de caractère fourni.|