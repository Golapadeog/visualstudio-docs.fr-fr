---
title: "Comment : ajouter un fichier de ressources | Documents Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 47cae5fac3ddbcbc34535176701d0293ae4f66ba
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-resource-file"></a>Comment : ajouter un fichier de ressources
  Les commandes permettant d’ajouter des fichiers de ressources est dans le menu contextuel du nœud de la solution et des nœuds de fonctionnalité dans l’Explorateur de solutions. Pour plus d’informations, consultez [localiser des Solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Pour ajouter un fichier de ressources globales à une solution SharePoint  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez une solution SharePoint.  
  
2.  Dans **l’Explorateur de solutions**, choisissez un nœud de projet SharePoint, puis, dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
3.  Dans le **ajouter un nouvel élément** boîte de dialogue, choisissez le **fichier de ressources Global** modèle, puis choisissez le **ajouter** bouton.  
  
    > [!NOTE]  
    >  Le modèle d’élément de projet fichier de ressources Global apparaît uniquement lorsqu’un élément de projet SharePoint est sélectionné.  
  
4.  Dans le **ajouter une ressource** boîte de dialogue, choisissez une culture pour le fichier de ressources, tel que l’anglais (États-Unis).  
  
     Cette étape ajoute un fichier de ressources globales à votre solution dans le format, Resource*x***.** *culture***.** resx, par exemple, Resource1-US.resx.  
  
5.  Lorsque le **éditeur de ressources** s’ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ajouter des ressources au fichier de ressources.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Pour ajouter un fichier de ressources de fonctionnalité à une fonctionnalité SharePoint  
  
1.  Si la solution SharePoint n’est pas déjà ouverte dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez la solution.  
  
2.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nom d’une fonctionnalité sous le **fonctionnalités** nœud, puis choisissez **ajouter une ressource de fonctionnalité**.  
  
     Cette étape ajoute un fichier de ressources à la fonctionnalité dans le format, *ResourceFileName***.** *culture***.** resx, tel que Feature1.en-us.resx.  
  
3.  Lorsque le **éditeur de ressources** s’ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ajouter des ressources au fichier de ressources.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  