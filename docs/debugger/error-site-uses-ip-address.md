---
title: "Erreur : Le Site utilise les adresses IP | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e6073fd88221e307b46a90173526876f2e2186d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="error-site-uses-ip-address"></a>Erreur : le site utilise l'adresse IP
Cette erreur se produit lorsque le débogueur essaie de s'auto-attacher à une application Web qui utilise une adresse IP. Cela se produit si vous modifiez **identification de site Web** à **utiliser une adresse IP spécifique** dans IIS.  
  
 Pour que l'auto-attachement fonctionne, vous devez créer le projet avec l'adresse IP spécifique plutôt qu'avec seulement le nom de l'ordinateur. Sinon, le débogueur transformera le nom de l'ordinateur en localhost, ce qui empêchera d'envoyer le verbe de débogage à IIS.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  À la place de l’attachement manuel de l’utilisation (dans le menu Déboguer, choisissez **attacher au processus**).  
  
     - ou -  
  
2.  Modifier la **identification du site Web IIS** paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)