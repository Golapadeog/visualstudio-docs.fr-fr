---
title: IDebugComPlusSymbolProvider::GetEntryPoint | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetEntryPoint
- GetEntryPoint
ms.assetid: 9640e121-1da1-41f9-8e66-76efca36baf2
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c695c8685be3db9004ec2ae8b68afd6b7844e7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcomplussymbolprovidergetentrypoint"></a>IDebugComPlusSymbolProvider::GetEntryPoint
Récupère le point d’entrée de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetEntryPoint(  
   ULONG32         ulAppDomainID,  
   GUID            guidModule,  
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetEntryPoint(  
   uint              ulAppDomainID,  
   Guid              guidModule,  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ulAppDomainID`  
 [in] Identificateur du domaine d’application.  
  
 `guidModule`  
 [in] Identificateur unique pour le module.  
  
 `ppAddress`  
 [out] Retourne le point d’entrée représenté par une [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose la [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetEntryPoint(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IDebugAddress **ppAddress  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidWritePtr(ppAddress, IDebugAddress *));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetEntryPoint );  
  
    IfFalseGo( ppAddress, E_INVALIDARG );  
  
    *ppAddress = NULL;  
  
    IfFailGo( GetModule( idModule, &pModule) );  
  
    IfFailGo( pModule->GetEntryPoint( ppAddress ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetEntryPoint, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)