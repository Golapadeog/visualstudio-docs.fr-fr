---
title: "endsWith, méthode (String) (JavaScript) | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c7d836e3-bc43-4d1b-be60-0a93beb8b7a2
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6d57d501f0f100f069522e4b51666918168fa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="endswith-method-string-javascript"></a>endsWith, méthode (String) (JavaScript)
Retourne une valeur qui indique si une chaîne ou sous-chaîne se termine par une autre chaîne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
  
stringObj.endsWith(str, [, position]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stringObj`  
 Obligatoire. Objet String pour la recherche.  
  
 `str`  
 Obligatoire. Chaîne recherchée.  
  
 `position`  
 Facultatif. Position du premier caractère pour la recherche dans l'objet String, en commençant à 0.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la chaîne commençant à `position` se termine par la chaîne recherchée, la méthode `endsWith` retourne `true` ; sinon, elle retourne `false`.  
  
## <a name="exceptions"></a>Exceptions  
 Si `str` est un `RegExp`, une `TypeError` est générée.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="requirements"></a>Spécifications  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]