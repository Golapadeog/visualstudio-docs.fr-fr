---
title: "Comment : ajouter un élément de Menu contextuel à un Type d’élément de projet SharePoint personnalisé | Documents Microsoft"
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e30a04d06f74f905daeebc4236962e88c20540bd
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Comment : ajouter un élément de menu contextuel à un type d'élément de projet SharePoint personnalisé
  Lorsque vous définissez un type d’élément de projet SharePoint personnalisé, vous pouvez ajouter un élément de menu contextuel pour l’élément de projet. L’élément de menu s’affiche lorsqu’un utilisateur clique sur l’élément de projet dans **l’Explorateur de solutions**.  
  
 Les étapes suivantes supposent que vous avez déjà défini votre propre type d’élément de projet SharePoint. Pour plus d’informations, consultez [Comment : définir un Type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Pour ajouter un élément de menu contextuel à un type d’élément de projet personnalisés  
  
1.  Dans le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> méthode de votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implémentation, gérez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> l’événement de la *projectItemTypeDefinition* paramètre.  
  
2.  Dans votre gestionnaire d’événements pour le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> événement, ajouter un nouveau <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet à la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> collection du paramètre d’arguments de l’événement.  
  
3.  Dans le <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> pour le nouveau gestionnaire d’événements <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> de l’objet, effectuez les tâches que vous souhaitez exécuter lorsqu’un utilisateur choisit l’élément de menu contextuel.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment ajouter un élément de menu contextuel à un type d’élément de projet personnalisé. Lorsque l’utilisateur ouvre le menu contextuel à partir de l’élément de projet dans **l’Explorateur de solutions** et choisit le **écrire le Message dans la fenêtre sortie** élément de menu, Visual Studio affiche un message dans le **sortie**  fenêtre.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 Cet exemple utilise le service de projet SharePoint pour écrire le message à la **sortie** fenêtre. Pour plus d’informations, consultez [à l’aide du Service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple requiert un projet de bibliothèque de classes avec des références aux assemblys suivants :  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Déploiement de l’élément de projet  
 Pour activer les autres développeurs d’utiliser votre élément de projet, créer un modèle de projet ou un modèle d’élément de projet. Pour plus d’informations, consultez [création de modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Pour déployer l’élément de projet, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour l’assembly, le modèle et tous les autres fichiers que vous voulez distribuer avec l’élément de projet. Pour plus d’informations, consultez [déploiement d’Extensions pour les outils SharePoint dans Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : définir un Type d’élément de projet SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Comment : ajouter une propriété à un Type d’élément de projet SharePoint personnalisé](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Définition de types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  