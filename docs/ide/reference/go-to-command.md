---
title: Atteindre, commande | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 53c45ccf528375bc31b4d61fd6af0193aa295e6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="go-to-command"></a>Atteindre, commande
Déplace le curseur à la ligne spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Arguments  
 `linenumber`  
 Facultatif. Nombre entier représentant le numéro de la ligne à atteindre.  
  
## <a name="remarks"></a>Notes  
 La numérotation des lignes débute à 1. Si la valeur de `linenumber` est inférieure à 1, la première ligne est affichée. Si la valeur de `linenumber` est supérieure au numéro de la dernière ligne, la dernière ligne est affichée.  
  
 Si aucune valeur n’est spécifiée pour `linenumber`, la boîte de dialogue **Atteindre la ligne** s’affiche.  
  
 L’alias de cette commande est GoToLn.  
  
## <a name="example"></a>Exemple  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)