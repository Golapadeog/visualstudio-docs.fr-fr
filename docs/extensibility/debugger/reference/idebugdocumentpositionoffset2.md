---
title: IDebugDocumentPositionOffset2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 12b3d9781348beb69bb2f4923dd5d5b311f157c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Représente une position dans un fichier source par un offset de caractère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Implémentée par l’IDE et utilisée par les moteurs de débogage.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de `IDebugDocumentPositionOffset2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Récupère la plage pour la position actuelle du document.|  
  
## <a name="remarks"></a>Notes  
 Cela retourne les mêmes informations que [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) mais dans `char` offsets à partir du début du document. Cela pose le document comme il existe sur un disque, autrement dit, un tableau unidimensionnel de caractères, plutôt que les informations de ligne et de colonne qui est retournée normalement.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)