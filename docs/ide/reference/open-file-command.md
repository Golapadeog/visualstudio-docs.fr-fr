---
title: Ouvrir un fichier, commande | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 59b0c421fa5a62394a32a2b9ad9926df58a40cb9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="open-file-command"></a>Ouvrir un fichier, commande
Ouvre un fichier existant et vous permet de spécifier un éditeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Obligatoire. Chemin complet ou partiel et nom du fichier à ouvrir. Les chemins comportant des espaces doivent être placés entre guillemets.  
  
## <a name="switches"></a>Commutateurs  
 /e:`editorname`  
 Facultatif. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.  
  
 La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la boîte de dialogue Ouvrir avec, entre guillemets.  
  
 Par exemple, pour ouvrir un fichier dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Notes  
 La fonctionnalité de saisie semi-automatique tente de trouver le chemin et le nom de fichier correspondant aux caractères que vous tapez.  
  
## <a name="example"></a>Exemple  
 Cet exemple ouvre la feuille de style « Test1.css » dans l’éditeur de code source.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Fenêtre Exécution](../../ide/reference/immediate-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)