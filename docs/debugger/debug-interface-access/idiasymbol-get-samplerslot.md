---
title: IDiaSymbol::get_samplerSlot | Documents Microsoft
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
ms.assetid: 41c751ba-81be-4bd3-838f-8373fc146157
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5189042ee6bbcf02615530f12e502a15fb5829bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetsamplerslot"></a>IDiaSymbol::get_samplerSlot
Récupère l’emplacement de l’échantillonneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_samplerSlot(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Un pointeur vers un `DWORD` qui contient l’emplacement de l’échantillonneur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)