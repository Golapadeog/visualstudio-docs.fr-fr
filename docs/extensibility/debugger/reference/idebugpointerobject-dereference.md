---
title: IDebugPointerObject::Dereference | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3e743f5a312e437ca48a5e36fb202783f41b934d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtient l’objet désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwIndex`  
 [in] Offset d’octet simple à partir du début de l’objet indiqué.  
  
 `ppObject`  
 [out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de l’objet qui représente l’objet vers lequel pointe, ainsi que le décalage, le cas échéant.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur. Retourne E_FAIL si cet objet ne pointe pas vers un autre objet.  
  
## <a name="remarks"></a>Notes  
 L’objet vers lequel pointé peut être un type primitif ou un type plus complexe comme une classe ou structure.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)