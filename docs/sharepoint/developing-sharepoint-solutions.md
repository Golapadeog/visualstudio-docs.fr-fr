---
title: "Développement de Solutions SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 848ddab54dd9e7617cce7758fa06d939700f2c3b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="developing-sharepoint-solutions"></a>Développement de solutions SharePoint
  Pour créer des sites et des éléments de sites SharePoint, vous disposez de plusieurs modèles de type de projet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Pour obtenir la liste des types de projet disponibles, consultez [projets et modèles d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md). Les éléments et propriétés d'un projet SharePoint sont décrits ci-après.  
  
 Pour plus d’informations sur SharePoint 2013 et les compléments SharePoint, consultez [SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) et [Compléments SharePoint](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx).  
  
## <a name="elements-of-a-sharepoint-project"></a>Éléments d'un projet SharePoint  
 Les nœuds sous un projet SharePoint sont appelés *éléments SharePoint*. Éléments SharePoint peuvent contenir également un ou plusieurs sous-fichiers, appelés *fichiers d’éléments SharePoint*, tel que [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] les fichiers de configuration, les formulaires .aspx et bien plus encore.  
  
 Au lieu de créer des projets à l'aide de modèles de projet préremplis avec des fichiers d'éléments de projet, vous pouvez utiliser le modèle **Projet vide** pour créer un projet SharePoint vide et ajouter manuellement des éléments de projet. Les projets SharePoint peuvent également contenir un ou plusieurs fichiers de fonctionnalités (pour l'activation dans SharePoint) et un fichier de package permettant de distribuer le projet.  
  
### <a name="special-nodes"></a>Nœuds spéciaux  
 Chaque projet SharePoint contient deux nœuds qui ne peuvent pas être renommés, supprimés, coupés, copiés ou déplacés du projet. Il s'agit des nœuds suivants :  
  
-   Fonctionnalités  
  
-   Package  
  
 Ces deux nœuds apparaissent toujours dans tous les projets SharePoint même si aucune fonctionnalité ou package n'est défini pour le projet.  
  
#### <a name="features-node"></a>Nœud Fonctionnalités  
 Le nœud **Fonctionnalités** contient une ou plusieurs fonctionnalités de projet SharePoint. Une fonctionnalité est un conteneur d'extensions pour SharePoint. Une fois déployée sur un serveur SharePoint, la fonctionnalité peut être ajoutée à des définitions de site ou activée individuellement par les administrateurs SharePoint sur les sites SharePoint. Pour plus d’informations, consultez [Utilisation des fonctionnalités](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
 Quand vous ajoutez un élément, comme un type de contenu ou une instance de liste, à un projet SharePoint, il est ajouté à une fonctionnalité dans le nœud **Fonctionnalités** . La portée de l'élément détermine s'il est ajouté à une fonctionnalité nouvelle ou existante. Si le nouvel élément a la même portée qu'une fonctionnalité existante, il est ajouté à cette fonctionnalité. Sinon, l'élément est ajouté à une nouvelle fonctionnalité.  
  
 Pour ajouter manuellement une fonctionnalité, exécutez la commande **Ajouter une fonctionnalité** dans le menu contextuel du nœud Fonctionnalités. Vous pouvez afficher ou modifier le contenu d'une fonctionnalité à l'aide du Concepteur de fonctionnalités. Pour plus d’informations, consultez [Comment : personnaliser une fonctionnalité SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
 Quand une fonctionnalité est ajoutée à un projet SharePoint, elle apparaît dans l' **Explorateur de solutions** sous la forme d'un nœud ayant pour nom par défaut Feature*x*.feature, où *x* est un nombre unique. Une fois déployée sur le serveur SharePoint, un administrateur SharePoint peut l'activer et la mettre ainsi à la disposition des utilisateurs du site SharePoint.  
  
#### <a name="package-node"></a>Nœud Package  
 Le nœud **Package** contient un fichier unique qui sert de mécanisme de distribution pour le projet SharePoint. Ce fichier, appelé *package**package*, est basé sur le format .CAB et porte l’extension .WSP. Un package de solution est un fichier réutilisable destiné à être déployé. Il contient un ensemble de fonctionnalités, définitions de site et assemblys (activables ou désactivables individuellement) s'appliquant aux sites SharePoint. Le **Package** nœud contient également un fichier nommé package.wspdef, c'est-à-dire un [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] fichier de définition pour le package. Une fois le package déployé sur le serveur qui exécute SharePoint, l'administrateur SharePoint peut l'installer et activer ses fonctionnalités.  
  
 Vous pouvez afficher ou modifier le contenu du package dans le Concepteur de packages en double-cliquant sur le nœud package ou en ouvrant le menu contextuel, puis en choisissant **ouvrir**. Pour plus d’informations, consultez [création de Packages de Solution SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
## <a name="sharepoint-project-and-project-item-properties"></a>Propriétés des projets et des éléments de projet SharePoint  
 Les projets SharePoint, tout comme les autres projets [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], présentent les propriétés dans la fenêtre Propriétés et dans la page Propriétés. Les propriétés affichées dépendent du nœud sélectionné.  
  
 Quand un projet, élément de projet, ou nœud de fichier d'élément de projet SharePoint est sélectionné dans l' **Explorateur de solutions**, les propriétés suivantes s'affichent dans la fenêtre ou la page Propriétés :  
  
### <a name="project-properties"></a>Propriétés du projet  
  
|Nom de propriété|Description|  
|-------------------|-----------------|  
|Configuration de déploiement active|Spécifie la série d'étapes effectuée au cours du déploiement. Pour plus d’informations, consultez [Comment : modifier une Configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|  
|Cible de déploiement d'assembly|Détermine où se trouvent les *assemblys d'application SharePoint* . Les valeurs d'emplacement autorisées sont *GlobalAssemblyCache* (par défaut) ou *WebApplication*.<br /><br /> Si la propriété *Sandboxed Solution* a la valeur **true**, cette propriété est désactivée.|  
|Retrait automatique après le débogage|Spécifie si la solution déployée est automatiquement retirée de SharePoint une fois l'application exécutée en mode débogage dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Quand cette option est activée et que l'IDE repasse en mode Design après le débogage, la solution est retirée. Quand elle est désactivée, la solution n'est pas retirée. Pour plus d’informations, consultez [Retrait d’une solution](http://go.microsoft.com/fwlink/?LinkId=183819).|  
|Modifier les configurations|Spécifie la configuration de déploiement à utiliser pour le projet. Pour plus d’informations, consultez [Comment : modifier une Configuration de déploiement SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) et [déploiement, la publication et la mise à niveau de Packages de Solution SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|  
|Activer le débogage Silverlight (au lieu du débogage de script)|Quand cette option est activée, le débogueur Silverlight s'attache au processus de débogage. Quand cette option est désactivée, le débogueur de script s'attache au processus de débogage. Pour plus d’informations, consultez [Vue d’ensemble du débogage de Silverlight](http://go.microsoft.com/fwlink/?LinkId=179826).|  
|Inclure un assembly dans le package|Spécifie si l'assembly de projet est empaqueté au moment de la génération ou non.|  
|Ligne de commande de post-déploiement|Spécifie les commandes à exécuter après le déploiement de la solution SharePoint. Cette ligne prend en charge toute commande de traitement par lots, ainsi que la résolution des variables MSBuild. Pour plus d’informations, consultez [Comment : définir des commandes de déploiement SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Ligne de commande de prédéploiement|Spécifie les commandes à exécuter avant le déploiement de la solution SharePoint. Cette ligne prend en charge toute commande de traitement par lots, ainsi que la résolution des variables MSBuild. Pour plus d’informations, consultez [Comment : définir des commandes de déploiement SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Fichier projet|Nom du fichier contenant la build, la configuration et d'autres informations sur le projet.|  
|Dossier du projet|Emplacement du fichier projet sur le système. (En lecture seule.)|  
|Sandboxed Solution|Spécifie si le projet doit être déployé en tant que *solution bac à sable (sandbox)*, également appelée *solution créée par l'utilisateur*. Les solutions bac à sable ne sont pas nécessairement dignes de confiance. La valeur **true** signifie que le projet est déployé comme une solution bac à sable, alors que la valeur **false** signifie qu'il est déployé comme une solution de batterie. Pour plus d’informations, consultez [considérations sur les solutions bac à sable](../sharepoint/sandboxed-solution-considerations.md) et [les différences entre bac à sable et les Solutions de batterie de serveurs](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|  
|URL du site|Spécifie l'[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] du site cible pour ce projet.|  
|Élément de démarrage|Spécifie le premier élément à exécuter dans le projet.|  
  
 Quand vous choisissez un fichier d'élément SharePoint (comme un flux de travail ou une fonctionnalité du nœud Fonctionnalités), les propriétés suivantes s'affichent dans la fenêtre Propriétés :  
  
### <a name="project-item-properties"></a>Propriétés des éléments de projet  
  
|Nom de la propriété|Description|  
|-------------------|-----------------|  
|Résolution de conflit de déploiement|Spécifie l'action à entreprendre lors du déploiement d'un élément de projet dont les propriétés sont identiques à celles d'un élément déjà présent sur le serveur. Pour plus d’informations, consultez [résolution des problèmes de conditionnement de SharePoint et de déploiement](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|  
|Propriétés de la fonctionnalité|Spécifie un ensemble de valeurs (stockées sous forme de paires clé/valeur) inclus avec une fonctionnalité au moment de son déploiement sur SharePoint. Une fois la fonctionnalité déployée, vous pouvez accéder aux valeurs de propriété dans votre code. Pour plus d’informations, consultez [fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Récepteur de fonctionnalité|Fournit le code qui s'exécute quand certains événements se produisent pour une fonctionnalité contenant un élément de projet. Pour plus d’informations, consultez [fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Nom du dossier|Nom du dossier contenant les éléments de projet SharePoint.|  
|Références de sortie de projet|Spécifie une dépendance, telle qu'un assembly, que votre élément de projet doit exécuter. Pour plus d’informations, consultez [fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Entrées de contrôle sécurisé|Spécifie les contrôles que les utilisateurs non fiables peuvent modifier en toute sécurité. Pour plus d’informations, consultez [fournissant l’empaquetage et du déploiement dans les éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
  
### <a name="project-item-file-properties"></a>Propriétés des fichiers d'éléments de projet  
  
|Nom de la propriété|Description|  
|-------------------|-----------------|  
|Action de génération|Indique le lien entre le fichier et les processus de génération et de déploiement. Pour plus d’informations, consultez [Propriétés du fichier](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Copier dans le répertoire de sortie|Indique si le ou les fichiers source seront copiés vers le répertoire de sortie. Peut avoir l'une des valeurs suivantes :<br /><br /> -   *Ne pas copier*<br />-   *Toujours copier*<br />-   *Copier si plus récent*<br /><br /> Pour plus d’informations, consultez [Propriétés du fichier](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Outil personnalisé|Spécifie le nom de l'outil utilisé (le cas échéant) pour transformer le fichier au moment du design et placer le résultat de la transformation dans un autre fichier. Par exemple, un fichier dataset (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) est fourni avec un outil personnalisé par défaut. Pour plus d’informations, consultez [Propriétés du fichier](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Espace de noms de l'outil personnalisé|Espace de noms dans lequel est copié le résultat de l'outil personnalisé. Pour plus d’informations, consultez [Propriétés du fichier](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|  
|Emplacement de déploiement|Chemin d'accès complet du fichier sur le serveur SharePoint. Ce chemin d'accès est composé des sous-propriétés Racine du déploiement et Chemin d'accès du déploiement.|  
|Chemin d'accès du déploiement|Le chemin d’accès relatif du fichier sur le serveur de fichiers SharePoint, tel que Workflow1\\. Le chemin d'accès qualifié complet du fichier est obtenu par concaténation de la valeur *Deployment Path* à la fin de la valeur *Deployment Root* .<br /><br /> Sélection d’une valeur de *RootFile* pour le *Type de déploiement* modifications apportées aux propriétés la *racine du déploiement* prend la valeur {SharePointRoot}\\, se traduisant par un chemin complet de {SharePointRoot} \Workflow1\\. Pour plus d’informations, consultez [empaquetage et déploiement de Solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|  
|Deployment Root|Chaîne. Dossier racine dans lequel le fichier est déployé sur le serveur SharePoint. Par exemple, {SharePointRoot} \Template\Features\\{NomFonctionnalité}\\.<br /><br /> La valeur de la propriété *Deployment Root* est déterminée par le paramètre *Deployment Type* .|  
|Deployment Type|Type de déploiement du fichier, lequel détermine sa valeur *Deployment Root* . Peut avoir l'une des valeurs suivantes :<br /><br /> NoDeployment : \<aucune valeur ><br /><br /> ElementManifest : {SharePointRoot} \Template\Features\\{NomFonctionnalité}\\<br /><br /> ElementFile : {SharePointRoot} \Template\Features\\{NomFonctionnalité}\\<br /><br /> TemplateFile : {SharePointRoot} \Template\\<br /><br /> RootFile : {SharePointRoot}\\<br /><br /> GlobalResource : {SharePointRoot} \Resources\\<br /><br /> ClassResources : {ClassResourcePath}\\<br /><br /> Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|  
|Nom du fichier|Nom du fichier ou du dossier pour le fichier d'élément.|  
|Chemin d'accès complet|Emplacement du fichier pour l'élément. (En lecture seule.)|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Modèles de projets et d’éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)|Décrit le projet SharePoint et les modèles d'élément de projet disponibles dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Guide pratique pour ajouter des éléments à un projet SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Explique comment ajouter de nouveaux éléments ou des éléments existants à un projet SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Procédure pas à pas : création d’une colonne de site, d’un type de contenu et d’une liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Montre comment créer, étape par étape, un champ personnalisé, un type de contenu, une définition de liste et une instance de liste.|  
|[Guide pratique pour créer un récepteur d’événements](../sharepoint/how-to-create-an-event-receiver.md)|Décrit comment ajouter un récepteur d’événements pour le projet créé dans [procédure pas à pas : création d’une colonne de Site, le Type de contenu et la liste pour SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|  
|[Création de solutions de flux de travail SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Explique comment créer des projets de flux de travail comportant des formulaires d'association et des formulaires d'initiation de flux de travail.|  
|[Création de pages pour SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Explique comment créer des pages telles que des pages d'application, pages de site, pages maîtres et des mises en page pour SharePoint.|  
|[Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Explique comme ajouter des contrôles pour permettre aux utilisateurs de modifier directement le contenu, l'apparence et le comportement des pages d'un site SharePoint à l'aide d'un navigateur.|  
|[Création de contrôles réutilisables pour les composants WebPart ou les pages d’application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Explique comment créer des contrôles utilisateur pouvant être consommés par les pages d'application et les composants WebPart qui s'exécutent dans SharePoint.|  
|[Intégration de données métiers dans SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Explique comment intégrer les données des services web et des applications serveur principales à une application SharePoint.|  
|[Création de définitions de site pour SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Explique comment créer des définitions de site, c'est-à-dire les modèles utilisés pour concevoir des sites SharePoint.|  
|[Importation d’éléments d’un site SharePoint existant](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Explique comment importer les éléments (tels que des types de contenu et des modules) d'un site SharePoint existant vers un projet SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Utilisation de modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Explique comment utiliser des modules pour déployer les fichiers de votre projet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sur le site SharePoint.|  
|[Parcours des connexions SharePoint à l’aide de l’Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Explique comment parcourir les sites SharePoint locaux à l'aide de l'Explorateur de serveurs.|  
|[Fourniture d’informations de création de packages et de déploiement dans des éléments de projet](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Explique comment utiliser les propriétés d'élément de projet pour fournir des informations d'empaquetage et de déploiement pour les projets, telles que les entrées de contrôle sécurisé, les références de sortie de projet et les propriétés de fonctionnalité.|  
|[Guide pratique pour ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Explique comment ajouter des dossiers mappés à votre projet pour faciliter l'accès aux ressources SharePoint.|  
|[Considérations sur les solutions bac à sable (sandbox)](../sharepoint/sandboxed-solution-considerations.md)|Décrit les problèmes ayant trait aux solutions bac à sable (sandbox).|  
|[Sécurité pour les solutions SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Décrit des considérations au sujet de la sécurité pour le développement de solutions SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Boîte de dialogue Sélecteur URL &#40; Développement SharePoint dans Visual Studio &#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Décrit une boîte de dialogue que vous pouvez utiliser pour ajouter des références de chemin d'accès aux ressources dans votre projet ou sur le serveur SharePoint local.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en route &#40; Développement SharePoint dans Visual Studio &#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [Parcours des connexions SharePoint à l’aide de l’Explorateur de serveurs](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  