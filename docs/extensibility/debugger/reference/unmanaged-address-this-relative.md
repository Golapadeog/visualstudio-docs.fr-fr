---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2b8c3088b4bfabb3eec00357d6bc1e9306bd42ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="unmanagedaddressthisrelative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
Cette structure représente une adresse qui est relatif à un `this` pointeur (`Me` en Visual Basic).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _tagUNMANAGED_THIS_RELATIVE {  
   DWORD dwOffset;  
   DWORD dwBitOffset;  
   DWORD dwBitLength;  
} UNMANAGED_ADDRESS_THIS_RELATIVE;  
```  
  
```csharp  
public struct UNMANAGED_THIS_RELATIVE {  
   public uint dwOffset;  
   public uint dwBitOffset;  
   public uint dwBitLength;  
}  
```  
  
## <a name="terms"></a>Termes  
 dwOffset  
 Décalage à partir d’une position de base (par exemple, le début d’une classe de vtable) d’octets.  
  
 dwBitOffset  
 Décalage de bits d’une position de base (toujours 0, sauf si vous faites référence à un champ de bits).  
  
 dwBitLength  
 Nombre de bits qui représente l’adresse (toujours 0, sauf si vous faites référence à un champ de bits).  
  
## <a name="remarks"></a>Notes  
 Cette structure est la partie de l’union dans la [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) lors de la structure la `dwKind` champ le `DEBUG_ADDRESS_UNION` structure est définie sur `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` (une valeur à partir de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) énumération).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)