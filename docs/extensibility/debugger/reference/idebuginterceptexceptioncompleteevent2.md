---
title: IDebugInterceptExceptionCompleteEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 70610fac689fb9f0e1490792965f44b8ede7e0b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
Cette interface est envoyée par le moteur de débogage (DE) pour le Gestionnaire de session de débogage (SDM) lorsque le D’a terminé le traitement d’un événement intercepté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface pour signaler que le traitement d’une exception interceptée est terminé. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le crée et envoie cet objet d’événement pour signaler la fin d’une exception interceptée. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le `IDebugInterceptExceptionCompleteEvent2` interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Retourne la valeur unique associée à l’exception gérée.|  
  
## <a name="remarks"></a>Notes  
 Cet événement ne sera envoyé par [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) lorsque cette méthode a terminé avec succès la gestion d’une exception interceptée.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)