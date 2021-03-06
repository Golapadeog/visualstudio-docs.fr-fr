---
title: "Procédure pas à pas : Ajout de fonctionnalités à un éditeur personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f3c207b80686a66d9a06b8c50321b4dce2257ada
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Procédure pas à pas : Ajout de fonctionnalités à un éditeur personnalisé
Après avoir créé un éditeur personnalisé, vous pouvez ajouter davantage de fonctionnalités à ce dernier.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Pour créer un éditeur pour un VSPackage  
  
1.  Créer un éditeur personnalisé en utilisant le modèle de projet de Package Visual Studio.  
  
     Pour plus d’informations, consultez [procédure pas à pas : création d’un éditeur personnalisé](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Décidez si vous souhaitez que votre éditeur pour prendre en charge un seul ou plusieurs vues.  
  
     Un éditeur qui prend en charge la **nouvelle fenêtre** de commande, ou a mode formulaire et en mode code, requiert des objets de données de document distinct et les objets de vue de document. Dans un éditeur qui prend en charge qu’une seule vue, l’objet de données de document et l’objet de vue de document peuvent être implémentées sur le même objet.  
  
     Pour obtenir un exemple de plusieurs vues, consultez [prenant en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implémenter une fabrique d’éditeur en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
     Pour plus d’informations, consultez [fabriques d’éditeur](../extensibility/editor-factories.md).  
  
4.  Décider si votre éditeur afin d’utiliser l’activation sur place ou simplifié incorporation pour gérer la fenêtre d’objet de vue de document.  
  
     Une fenêtre d’éditeur incorporation simplifié héberge un mode d’affichage standard, pendant une fenêtre d’éditeur de l’activation sur place héberge un contrôle ActiveX ou un autre objet active en tant que sa vue de document. Pour plus d’informations, consultez [simplifié incorporation](../extensibility/simplified-embedding.md) et [Activation en Place](../extensibility/in-place-activation.md).  
  
5.  Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface pour gérer les commandes.  
  
6.  Fournir la persistance de document et de réponse aux modifications de fichier externe en procédant comme suit :  
  
    1.  Pour conserver le fichier, vous devez implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> et <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> sur l’objet de données de document de votre éditeur.  
  
    2.  Pour répondre aux modifications de fichier externe, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> sur l’objet de données de document de votre éditeur.  
  
        > [!NOTE]
        >  Appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> pour obtenir un pointeur vers `IVsFileChangeEx`.  
  
7.  Coordonner les événements de modification de document avec contrôle de code source. Pour ce faire :  
  
    1.  Obtenir un pointeur vers `IVsQueryEditQuerySave2` en appelant `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Lorsque le premier événement de modification se produit, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (méthode).  
  
         Cette invite l’utilisateur pour extraire le fichier si elle n’a pas déjà été extrait. Veillez à gérer une condition « fichier ne pas extrait » à éviter des erreurs  
  
    3.  De même, avant d’enregistrer le fichier, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> (méthode).  
  
         Cette méthode invite l’utilisateur à enregistrer le fichier s’il n’a pas été enregistré ou s’il a été modifié depuis le dernier enregistrement.  
  
8.  Activer la **propriétés** fenêtre pour afficher les propriétés pour le texte sélectionné dans l’éditeur. Pour ce faire :  
  
    1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> chaque sélection de texte heure change, passage dans votre implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service pour obtenir un pointeur vers <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Permettre aux utilisateurs de faire glisser des éléments entre l’éditeur et le **boîte à outils**, ou entre des éditeurs externes (par exemple, Microsoft Word) et le **boîte à outils**. Pour ce faire :  
  
    1.  Implémentez `IDropTarget` sur votre éditeur pour alerter l’IDE que votre éditeur est une cible de dépôt.  
  
    2.  Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interface sur l’affichage pour votre éditeur peut activer et désactiver des éléments dans le **boîte à outils**.  
  
    3.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> et appelez `QueryService` sur <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service pour obtenir un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfaces.  
  
         Cela permet à votre VSPackage pour ajouter de nouveaux éléments à la **boîte à outils**.  
  
10. Décidez si vous souhaitez que les autres fonctionnalités facultatives pour votre éditeur.  
  
    -   Si vous souhaitez que votre éditeur pour prendre en charge les rechercher et remplacer des commandes, implémentez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Si vous souhaitez utiliser une fenêtre d’outil de structure du document dans votre éditeur, implémenter `IVsDocOutlineProvider`.  
  
    -   Si vous souhaitez utiliser une barre d’état dans votre éditeur, implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> et appelez `QueryService` pour <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> pour obtenir un pointeur vers `IVsStatusBar`.  
  
         Par exemple, un éditeur peut afficher la ligne / informations sur les colonnes, le mode de sélection (flux / zone) et le mode d’insertion (insert / Surfrappe).  
  
    -   Si vous souhaitez que votre éditeur pour prendre en charge le `Undo` de commande, la méthode recommandée consiste à utiliser le modèle de gestionnaire d’annulation OLE. En guise d’alternative, vous pouvez avoir le handle de l’Éditeur du `Undo` commande directement.  
  
11. Créez plus d’informations, y compris les GUID pour le package Visual Studio, les menus, l’éditeur et autres fonctionnalités de Registre.  
  
     Voici un exemple de code que vous devez placer dans votre script de fichier .rgs pour montrer comment enregistrer correctement un éditeur générique.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Implémenter la prise en charge d’aide contextuelle.  
  
     Cela vous permet de vous permet de fournir l’aide (F1) et la fenêtre Aide dynamique prennent en charge pour les éléments dans votre éditeur. Pour plus d’informations, consultez [Comment : fournir un contexte pour les éditeurs de](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Exposer un modèle d’objet Automation à partir de votre éditeur en implémentant le `IDispatch` interface.  
  
     Pour plus d’informations, consultez [qui contribuent au modèle Automation](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Programmation fiable  
  
-   L’instance d’éditeur est créé lors de l’IDE appelle le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (méthode). Si l’éditeur prend en charge plusieurs vues, `CreateEditorInstance` crée les données du document et les objets de vue de document. Si l’objet de données de document est déjà ouvrir, une valeur non null `punkDocDataExisting` la valeur est passée à `IVsEditorFactory::CreateEditorInstance`. Votre implémentation de fabrique d’éditeur doit déterminer si un objet de données de document est compatible en interrogeant les interfaces appropriées sur celui-ci. Pour plus d’informations, consultez [prenant en charge plusieurs vues de Document](../extensibility/supporting-multiple-document-views.md).  
  
-   Si vous utilisez l’approche simplifiée de l’incorporation, implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface.  
  
-   Si vous décidez d’utiliser l’activation sur place, implémenter les interfaces suivantes :  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  Le `IOleInPlaceComponent` interface est utilisée pour éviter la fusion de menus OLE 2.  
  
     Votre `IOleCommandTarget` implémentation gère les commandes telles que **couper**, **copie**, et **coller**. Lors de l’implémentation `IOleCommandTarget`, décider si votre éditeur requiert son propre fichier .vsct pour définir sa propre structure de menu de commande ou si elle peut implémenter des commandes standard définis par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En règle générale, les éditeurs utilisent et d’étendent les menus de l’IDE et définissent leurs propres barres d’outils. Toutefois, il est souvent nécessaire pour un éditeur définir ses propres commandes spécifiques en plus d’utiliser le jeu de commandes standard de l’IDE. Pour ce faire, votre éditeur doit déclarer les commandes standard, il utilise et puis définissez les nouvelles commandes, les menus contextuels, les menus de niveau supérieur et les barres d’outils dans un fichier .vsct. Si vous créez une activation sur place de l’éditeur, puis implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> et définir les menus et les barres d’outils de l’éditeur dans un fichier .vsct au lieu d’utiliser la fusion de menus OLE 2.  
  
-   Pour empêcher la commande de menu charger dans l’interface utilisateur, vous devez utiliser les commandes existantes dans l’IDE avant inventer de nouvelles commandes. Commandes partagées sont définies dans SharedCmdDef.vsct et ShellCmdDef.vsct. Ces fichiers sont installés par défaut dans le sous-répertoire VisualStudioIntegration\Common\Inc de votre [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installation.  
  
-   `ISelectionContainer`peuvent exprimer des sélections uniques et multiples. Chaque objet sélectionné est implémenté comme un `IDispatch` objet.  
  
-   L’IDE implémente `IOleUndoManager` en tant que service accessible à partir d’un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> ou sous la forme d’un objet qui peut être instancié via <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Votre éditeur implémente la `IOleUndoUnit` interface pour chaque `Undo` action.  
  
-   Il existe deux emplacements un éditeur personnalisé peut exposer des objets automation :  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Voir aussi  
 [Qui contribuent au modèle Automation](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Comment : fournir un contexte pour les éditeurs](../extensibility/how-to-provide-context-for-editors.md)