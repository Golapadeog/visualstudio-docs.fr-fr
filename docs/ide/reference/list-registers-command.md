---
title: Afficher les registres, commande | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 016de257d1ce4e6d2aa95284adbe762a5c54eacf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="list-registers-command"></a>Afficher les registres, commande
Affiche la valeur des registres sélectionnés et vous permet de modifier la liste de registres à afficher.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>Commutateurs  
 /Display [{`register`&#124;`registerGroup`}...]  
 Affiche les valeurs du `register` ou `registerGroup` spécifié. Si aucun `register` ni `registerGroup` n’est spécifié, la liste par défaut de registres est affichée. Si aucun commutateur n’est spécifié, le comportement est le même. Exemple :  
  
 `Debug.ListRegisters /Display eax`  
  
 est équivalent à  
  
 `Debug.ListRegisters eax`  
  
 /List  
 Affiche tous les groupes de registres dans la liste.  
  
 /Watch [{`register`&#124;`registerGroup`}...]  
 Ajoute une ou plusieurs valeurs de `register` ou `registerGroup` dans la liste.  
  
 /Unwatch [{`register`&#124;`registerGroup`}...]  
 Supprime une ou plusieurs valeurs de `register` ou `registerGroup` de la liste.  
  
## <a name="remarks"></a>Notes  
 L’alias `r` peut être utilisé à la place de `Debug.ListRegisters`.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l’alias `Debug.ListRegisters` `r` pour afficher les valeurs du groupe de registres `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Concepts de base du débogage : fenêtre Registres](../../debugger/debugging-basics-registers-window.md)   
 [Guide pratique pour utiliser la fenêtre Registres](../../debugger/how-to-use-the-registers-window.md)