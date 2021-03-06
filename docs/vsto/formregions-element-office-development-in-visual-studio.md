---
title: "&lt;formRegions&gt; élément (développement Office dans Visual Studio) | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: eb7008f86dd552eac2b8a6ba9b227884270c8694
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; élément (développement Office dans Visual Studio)
  L’élément `formRegions` de l’espace de noms `vstov4` contient les zones de formulaire Microsoft Office Outlook associées à un complément VSTO.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 L’élément `formRegions` de l’espace de noms `vstov4` contient tous les éléments `formRegion` pour un complément VSTO Outlook. Il est uniquement obligatoire pour les compléments VSTO Outlook qui incluent des zones de formulaire.  
  
 Un seul élément `formRegions` peut être défini dans un manifeste de l’application.  
  
 L’élément `formRegions` ne possède pas d’attributs.  
  
 L’élément `formRegions` possède l’élément suivant.  
  
### <a name="formregion"></a>formRegion  
 Obligatoire pour les compléments VSTO Outlook qui comprennent des zones de formulaire. Le `formRegion` élément est défini dans [&#60; formRegion &#62; Élément &#40; développement Office dans Visual Studio &#41; ](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
### <a name="description"></a>Description  
 L’exemple de code suivant illustre un élément `formRegions` dans un manifeste de l’application pour une solution Office au niveau de l’application déployée à l’aide de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Cet exemple de code fait partie d’un exemple plus complet fourni dans [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifeste d’application ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  