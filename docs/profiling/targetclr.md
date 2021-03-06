---
title: TargetCLR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a69edb2730ff89a50dd45252258fc57e7205de3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="targetclr"></a>TargetCLR
L’option **TargetCLR** spécifie la version du common language runtime (CLR) à profiler quand plusieurs versions du CLR sont chargées dans une application.  
  
 Par défaut, les Outils de profilage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ciblent la première version du CLR qui est chargée par l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Paramètres  
 `ClrVersion`  
 Numéro de version du CLR. Utilisez le format de version **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Options obligatoires  
 L’option **TargetCLR** peut être utilisée seulement avec l’option **Launch** ou **Attach**.  
  
 **Launch :** `AppName`  
 Démarre l’application spécifiée et démarre le profilage.  
  
 **Attach:** `PID`  
 Démarre le profilage du processus spécifié.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, l’option TargetCLR est utilisée pour profiler la version 4.0.11003 du CLR.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```