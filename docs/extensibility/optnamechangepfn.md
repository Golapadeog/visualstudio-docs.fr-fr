---
title: OPTNAMECHANGEPFN | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2d067d5dd150dd026a2bd29a8933e8d9f72222b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Il s’agit d’une fonction de rappel spécifiée dans un appel à la [SccSetOption](../extensibility/sccsetoption-function.md) (à l’aide d’option `SCC_OPT_NAMECHANGEPFN`) et est utilisé pour communiquer des modifications de nom effectuées par le contrôle de source de plug-in à l’IDE.  
  
## <a name="signature"></a>Signature  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 pvCallerData  
 [in] Valeur de l’utilisateur spécifié dans un appel précédent à la [SccSetOption](../extensibility/sccsetoption-function.md) (à l’aide d’option `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] Le nom du fichier d’origine.  
  
 pszNewName  
 [in] Le nom du fichier a été renommé.  
  
## <a name="return-value"></a>Valeur de retour  
 Aucun  
  
## <a name="remarks"></a>Notes  
 Si un fichier est renommé pendant une opération de contrôle de code source, le plug-in de contrôle de code source peut avertir l’IDE sur le changement de nom via ce rappel.  
  
 Si l’IDE ne prend pas en charge ce rappel, elle n’appelle pas la [SccSetOption](../extensibility/sccsetoption-function.md) de le spécifier. Si le plug-in ne prend pas en charge ce rappel, elle retournera `SCC_E_OPNOTSUPPORTED` à partir de le `SccSetOption` lors de l’IDE tente de définir le rappel de fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)