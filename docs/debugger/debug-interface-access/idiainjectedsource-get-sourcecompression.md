---
title: IDiaInjectedSource::get_sourceCompression | Documents Microsoft
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
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 68b0d80d57e8e29aa326946b6cf94fe119ca30fd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Récupère l’indicateur de la compression de la source utilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne l’indicateur de la compression de la source utilisée. La valeur zéro indique qu’aucune compression de la source a été utilisée.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par cette méthode est spécifique au compilateur utilisé. Par exemple, un compilateur peut utiliser la compression RLE encodage ou Huffman-style.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)