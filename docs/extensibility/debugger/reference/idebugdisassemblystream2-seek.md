---
title: IDebugDisassemblyStream2::Seek | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2725eb876cf66665c27027dd4d9b250ed7e866e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Déplace le pointeur de la lecture dans le flux de code machine un nombre donné d’instructions par rapport à une position spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSeekStart`  
 [in] Une valeur à partir de la [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) énumération qui spécifie la position relative pour commencer le processus de recherche.  
  
 `pCodeContext`  
 [in] Le [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objet représentant le contexte de code que l’opération de recherche est relatif au. Ce paramètre est utilisé uniquement si `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; sinon, ce paramètre est ignoré et peut être une valeur null.  
  
 `uCodeLocationId`  
 [in] L’identificateur d’emplacement de code auquel l’opération de recherche est associée. Ce paramètre est utilisé si `dwSeekStart`  =  `SEEK_START_CODELOCID`; sinon, ce paramètre est ignoré et peut être défini à 0. Consultez la section Notes pour le [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) méthode pour obtenir une description d’un identificateur d’emplacement de code.  
  
 `iInstructions`  
 [in] Le nombre d’instructions pour déplacer par rapport à la position spécifiée dans `dwSeekStart`. Cette valeur peut être négative revenir en arrière.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la position de recherche a été au-delà de la liste des instructions disponibles. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 Si la recherche a été vers une position avant le début de la liste, la position de lecture est définie à la première instruction dans la liste. Si le consultez consistait à une position après la fin de la liste, la position de lecture est définie sur la dernière instruction dans la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)