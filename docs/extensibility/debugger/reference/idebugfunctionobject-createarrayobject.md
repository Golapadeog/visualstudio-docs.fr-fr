---
title: IDebugFunctionObject::CreateArrayObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5dfe24252ce2ce51ff86fa680d94964b86d09365
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Crée un objet tableau. Ce tableau peut contenir des soit primitive ou valeurs de l’instance d’objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ot`  
 [in] Spécifie une valeur à partir de la [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) énumération indiquant le type du nouvel objet tableau.  
  
 `pClassField`  
 [in] Un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objet représentant la classe d’un objet, si vous créez un tableau d’objet des valeurs d’instance. Si vous créez un tableau d’objets de type primitif, ce paramètre est une valeur null.  
  
 `dwRank`  
 [in] Le rang ou le nombre de dimensions du tableau.  
  
 `dwDims`  
 [in] Les tailles de chaque dimension du tableau.  
  
 `dwLowBounds`  
 [in] L’origine de chaque dimension (généralement 0 ou 1).  
  
 `ppObject`  
 [out] Retourne un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet représentant le tableau qui vient d’être créé. Il s’agit en fait un [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer un objet qui représente un paramètre de tableau à la fonction qui est représentée par le [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)