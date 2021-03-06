---
title: -SafeMode (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 17a8d92075f558e1e00bbba04f2c3ae955056b61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en mode sans échec, en chargeant uniquement l’environnement et les services par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Notes  
 Ce commutateur empêche le chargement de tous les packages VS tiers au démarrage de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], garantissant ainsi la stabilité de l’exécution.  
  
## <a name="description"></a>Description  
 L’exemple suivant démarre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en mode sans échec.  
  
## <a name="code"></a>Code  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)