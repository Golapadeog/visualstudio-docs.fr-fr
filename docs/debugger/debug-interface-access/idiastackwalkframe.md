---
title: IDiaStackWalkFrame | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: eb683afe63880af9d1a666436739140519f7339b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Gère le contexte d’empilement entre les appels de la [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDiaStackWalkFrame`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Récupère la valeur d’un Registre.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Définit la valeur d’un Registre.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Lit la mémoire à partir de l’image.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Recherche dans le frame de pile spécifié pour l’adresse de retour de fonction le plus proche.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Recherche dans le frame de pile spécifié pour une adresse d’expéditeur à ou près de l’adresse spécifiée.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est utilisée pendant l’exécution du programme pour lire et écrire des registres ainsi accéder à la mémoire et trouver les adresses d’expéditeur.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 L’application cliente implémente cette interface et passe une instance de l’interface pour le [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) (méthode). La même instance de cette interface est utilisée et pour maintenir l’état des registres au cours de chaque appel du `execute` (méthode). Le `execute` méthode utilise également cette interface afin de déterminer l’adresse de retour.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Dia2.h  
  
 Bibliothèque : diaguids.lib  
  
 DLL : msdia80.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)