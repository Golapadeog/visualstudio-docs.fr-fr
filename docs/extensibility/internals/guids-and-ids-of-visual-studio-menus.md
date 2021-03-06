---
title: GUID et ID de Menus Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69ad8f62931b628582c73a3e370a86611795caa6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID et ID de Menus Visual Studio
Cette rubrique énumère les valeurs GUID et l’ID des menus et des groupes dans la barre de menus de Visual Studio. Ces valeurs sont définies dans les fichiers .vsct qui sont installés dans le cadre du SDK Visual Studio. Pour plus d’informations, consultez [IDE-Defined commandes, Menus et des groupes](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Pour plus d’informations sur l’utilisation des objets d’environnement (IDE) de développement intégré qui sont définis dans les fichiers .vsct, consultez [étendant les Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Les menus et les groupes dans la barre de menus de Visual Studio utilisent le GUID `guidSHLMainMenu`. Le menu de la barre proprement dite a un ID `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Groupes sur la barre de menus de Visual Studio  
 Pour ajouter un menu à la barre de menus, définissez un de ces groupes comme son parent.  
  
|Regrouper|Id|  
|-----------|--------|  
|Affichage/Modifier/fichier|IDG_VS_MM_FILEEDITVIEW|  
|Refactorisation|IDG_VS_MM_REFACTORING :|  
|Projet|IDG_VS_MM_PROJECT|  
|Générer|IDG_VS_MM_BUILDDEBUGRUN|  
|Format/Tools|IDG_VS_MM_TOOLSADDINS|  
|Fenêtre/aide/Community|IDG_VS_MM_WINDOWHELP|  
|Compléments|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Menus dans la barre de menus de Visual Studio  
 Pour ajouter un groupe à un menu existant de Visual Studio, définissez un des menus suivants en tant que son parent. Sous-menus ne sont pas inclus dans cette liste.  
  
|Menu|Id|  
|----------|--------|  
|Fichier|IDM_VS_MENU_FILE|  
|Modifier|IDM_VS_MENU_EDIT|  
|Vue|IDM_VS_MENU_VIEW|  
|Réorganiser|IDM_VS_MENU_REFACTORING|  
|Projet|IDM_VS_MENU_PROJECT|  
|Générer|IDM_VS_MENU_BUILD|  
|Format|IDM_VS_MENU_FORMAT|  
|Outils|IDM_VS_MENU_TOOLS|  
|Fenêtre|IDM_VS_MENU_WINDOW|  
|Compléments|IDM_VS_MENU_ADDINS|  
|Communauté|IDM_VS_MENU_COMMUNITY|  
|Help|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Groupes de Menus Visual Studio  
 Les listes suivantes présentent les groupes qui descendent directement à partir des menus dans la barre de menus de Visual Studio. Le moyen le plus rapide pour ajouter une commande à un menu de Visual Studio est à un de ces groupes défini comme parent. Les groupes qui descendent des sous-menus n’apparaissent pas dans cette section.  
  
### <a name="file-menu-groups"></a>Menu groupes de fichiers  
  
|Regrouper|Id|  
|-----------|--------|  
|Nouveau/ouvrir|IDG_VS_FILE_FILE|  
|Ajouter|IDG_VS_FILE_ADD|  
|Solution|IDG_VS_FILE_SOLUTION|  
|Divers|IDG_VS_FILE_MISC|  
|Enregistrer|IDG_VS_FILE_SAVE|  
|Renommer|IDG_VS_FILE_RENAME|  
|Visiteur|IDG_VS_FILE_BROWSER|  
|Imprimer|IDG_VS_FILE_PRINT|  
|Utilisés le plus récemment|IDG_VS_FILE_MRU|  
|Déplacement|IDG_VS_FILE_MOVE|  
|Exit|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Modifier les groupes de menus  
  
|Regrouper|Id|  
|-----------|--------|  
|Annuler/Rétablir|IDG_VS_EDIT_UNDOREDO|  
|Couper/copier/coller.|IDG_VS_EDIT_CUTCOPY|  
|Sélectionner|IDG_VS_EDIT_SELECT|  
|GoTo|IDG_VS_EDIT_GOTO|  
|Find|IDG_VS_EDIT_FIND|  
|Objets|IDG_VS_EDIT_OBJECTS|  
|Verbes OLE|IDG_VS_EDIT_OLEVERBS|  
|Commande bien|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>Refactoriser les groupes de menus  
  
|Regrouper|Id|  
|-----------|--------|  
|Communes|IDG_REFACTORING_COMMON|  
|Avancé|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Afficher les groupes de Menu  
  
|Regrouper|Id|  
|-----------|--------|  
|Code du formulaire|IDG_VS_VIEW_FORMCODE|  
|Visiteur|IDG_VS_VIEW_BROWSER|  
|Définir des vues|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|L’architecture de Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|Organisation Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|Explorateur de code|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Développement Windows|IDG_VS_VIEW_DEV_WINDOWS|  
|Barres d'outils|IDG_VS_VIEW_TOOLBARS|  
|Symboles|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Accédez|IDG_VS_VIEW_NAVIGATE|  
|Accédez réduit|IDG_VS_VIEW_SMALLNAVIGATE|  
|Explorateur d'objets|IDG_VS_VIEW_OBJBRWSR|  
|Commande bien|IDG_VS_VIEW_COMMANDWELL|  
|Pages de propriétés|IDG_VS_VIEW_PROPPAGES|  
|Actualisation|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Groupes de menus de projet  
  
|Regrouper|Id|  
|-----------|--------|  
|Divers ajouter|IDG_VS_PROJ_MISCADD|  
|Ajouter|IDG_VS_PROJ_ADD|  
|Dossier|IDG_VS_PROJ_FOLDER|  
|Déchargement/rechargement|IDG_VS_PROJ_UNLOADRELOAD|  
|Référence|IDG_VS_PROJ_REFERENCE|  
|Options|IDG_VS_PROJ_OPTIONS|  
|Paramètres|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Créer des groupes de menus  
  
|Regrouper|Id|  
|-----------|--------|  
|Solution|IDG_VS_BUILD_SOLUTION|  
|Sélection|IDG_VS_BUILD_SELECTION|  
|Optimisation guidée par profil|IDG_VS_PGO_SELECTION|  
|Divers|IDG_VS_BUILD_MISC|  
|Annuler|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Groupes du Menu Outils  
  
|Regrouper|Id|  
|-----------|--------|  
|Ligne de commande|IDG_VS_TOOLS_CMDLINE|  
|Extraits de code|IDG_VS_TOOLS_SNIPPETS|  
|Sous-ensemble de l’objet|IDG_VS_TOOLS_OBJSUBSET|  
|Options|IDG_VS_TOOLS_OPTIONS|  
|Autres 2|IDG_VS_TOOLS_OTHER2|  
|Outils externes|IDG_VS_TOOLS_EXT_TOOLS|  
|Personnalisations externes|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Groupes du Menu fenêtre  
  
|Regrouper|Id|  
|-----------|--------|  
|Nouveau|IDG_VS_WINDOW_NEW|  
|Ancrer/de fermeture|IDG_VS_DOCKCLOSE|  
|Ancrer/masquage|IDG_VS_DOCKHIDE|  
|Organiser les|IDG_VS_WINDOW_ARRANGE|  
|Navigation|IDG_VS_WINDOW_NAVIGATION|  
|Liste|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Groupes de menus aide  
  
|Regrouper|Id|  
|-----------|--------|  
|Exemples|IDG_VS_HELP_SAMPLES|  
|Assistance|IDG_VS_HELP_SUPPORT|  
|À propos de|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Sous-menus des Menus de Visual Studio  
 La hiérarchie suivante montre les sous-menus qui sont associés les menus dans la barre de menus de Visual Studio. Car un groupe peut avoir un menu en tant que son parent, chaque sous-menu doit descendre d’un groupe dans un menu, au lieu de directement à partir du menu. Pour plus d’informations sur la relation entre les menus, des groupes et des sous-menus, consultez [Ajout d’un sous-menu à un Menu](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Les noms des menus dans la barre de menus de Visual Studio ne sont pas indiquées séparément dans cette hiérarchie car ils peuvent être déduits à partir de la convention d’affectation de noms pour les groupes dans l’IDE, comme suit : IDG_VS_*nom de Menu*_*nomdugroupe*.  
  
|Groupe parent|Sous-menu|Groupes enfants|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1... 6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>Voir aussi  
 [GUID et ID de barres d’outils de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUID et ID de commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)