---
title: "Champs de la fenêtre Propriétés et les Interfaces | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1f238cceb189723e3ec10fbf8db4abbd9675ae21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces et les champs de la fenêtre Propriétés
Le modèle pour la sélection déterminer quelles informations sont affichées dans le **propriétés** fenêtre est basée sur la fenêtre qui a le focus dans l’IDE. Chaque fenêtre et un objet dans la fenêtre sélectionnée, peuvent avoir son objet de contexte de sélection vers le contexte de la sélection globale. L’environnement des mises à jour le contexte global de sélection avec des valeurs à partir d’un frame de fenêtre lorsque cette fenêtre a le focus. Lorsque le focus change, par conséquent, ne le contexte de sélection.  
  
## <a name="tracking-selection-in-the-ide"></a>Suivi de sélection dans l’IDE  
 Le frame de fenêtre ou d’un site, détenu par l’IDE, dispose d’un service appelé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Les étapes suivantes montrent comment une modification dans une sélection, générée par l’utilisateur modifie le focus vers une autre fenêtre ouverte ou en sélectionnant un élément de projet différent dans **l’Explorateur de solutions**, est implémentée pour modifier le contenu affiché dans le  **Propriétés** fenêtre.  
  
1.  L’objet créé par votre VSPackage est placé dans les appels de la fenêtre sélectionnée <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> avoir <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> appeler <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Le conteneur de sélection fourni par la fenêtre sélectionnée, crée sa propre <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objet. Lorsque la sélection change, le VSPackage appelle <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> pour notifier les écouteurs dans l’environnement, y compris le **propriétés** fenêtre, de la modification. Il donne également accès à la hiérarchie et élément relatives à la nouvelle sélection.  
  
3.  Appel de <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> et en lui passant les éléments de la hiérarchie sélectionnée dans le `VSHPROPID_BrowseObject` paramètre remplit la <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objet.  
  
4.  Objet dérivé de la [IDispatch Interface](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) est renvoyée pour <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> pour l’élément demandé, et dans l’environnement encapsule un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (voir l’étape suivante). Si l’appel échoue, l’environnement appelle une deuxième `IVsHierarchy::GetProperty`, en lui passant le conteneur de sélection <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que la hiérarchie ou les éléments fournissent.  
  
     Votre projet ne crée pas de VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , car la fenêtre fournie par l’environnement VSPackage qui implémente (par exemple, **l’Explorateur de solutions**) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> sur son nom.  
  
5.  L’environnement appelle les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pour obtenir les objets selon la `IDispatch` interface pour renseigner le **propriétés** fenêtre.  
  
 Lorsqu’une valeur dans la **propriétés** fenêtre est modifiée, implémenter des VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx` et `IVsTrackSelectionEx::OnSelectionChangeEx` pour signaler la modification à la valeur de l’élément. L’environnement appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ou <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> pour conserver les informations affichées dans le **propriétés** fenêtre synchronisés avec les valeurs de propriété. Pour plus d’informations, consultez [mise à jour des valeurs de propriété dans la fenêtre Propriétés](#updating-property-values-in-the-properties-window).  
  
 En plus de sélectionner un autre élément de projet dans **l’Explorateur de solutions** pour afficher les propriétés relatives à cet élément, vous pouvez également choisir un autre objet à partir de dans une fenêtre de document ou formulaire à l’aide de la liste déroulante disponible sur le **Propriétés** fenêtre. Pour plus d’informations, consultez [objet liste de la fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md).  
  
 Vous pouvez modifier l’affichage des informations dans le **propriétés** grille de la fenêtre d’alphabétique aux catégories, et, s’il est disponible, vous pouvez également ouvrir une page de propriétés d’un objet sélectionné en cliquant sur les boutons appropriés sur le  **Propriétés** fenêtre. Pour plus d’informations, consultez [boutons de la fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md) et [Pages de propriétés](../../extensibility/internals/property-pages.md).  
  
 Enfin, la partie inférieure de la **propriétés** fenêtre contient également une description du champ sélectionné dans le **propriétés** grille de la fenêtre. Pour plus d’informations, consultez [mise en route des Descriptions de champs à partir de la fenêtre Propriétés](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a>Mise à jour des valeurs de propriété dans la fenêtre Propriétés
Il existe deux façons de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour. La première consiste à appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface, ce qui donne accès aux fonctionnalités de base de fenêtrage, y compris l’accès à et création de fenêtres Outil et document fournies par l’environnement. Les étapes qui suivent décrivent ce processus de synchronisation.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Pour mettre à jour les valeurs de propriété à l’aide de l’interface IVsUIShell  
  
1.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (via <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service) quand un VSPackage, projets, ou éditeurs doivent créer ou énumérer les fenêtres Outil ou le document.  
  
2.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> pour conserver le **propriétés** fenêtre synchronisé avec les modifications apportées aux propriétés d’un projet (ou tout autre objet sélectionné affiché dans le **propriétés** fenêtre) sans implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> et d’activation <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> événements.  
  
3.  Implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> pour activer ou désactiver, respectivement, notification du client pour implémenter des événements sans nécessiter de la hiérarchie <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IConnection  
 La deuxième façon de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour consiste à implémenter `IConnection` sur l’objet connectable pour indiquer l’existence des interfaces sortantes. Si vous souhaitez localiser le nom de propriété, dérivez votre objet de <xref:System.ComponentModel.ICustomTypeDescriptor>. Le <xref:System.ComponentModel.ICustomTypeDescriptor> implémentation peut modifier les descripteurs de propriété, elle retourne et modifiez le nom d’une propriété. Pour localiser la description, créer un attribut qui dérive de <xref:System.ComponentModel.DescriptionAttribute> et remplacez la propriété Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considérations relatives à l’implémentation de l’interface IConnection  
  
1.  `IConnection`fournit l’accès à un sous-objet énumérateur avec le <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. Il permet également d’accéder à tous les connexions point sous-chemin objets, chacun d’eux implémentant le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface.  
  
2.  Chaque objet est chargée d’implémenter un <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> événement. La fenêtre **Propriétés** affiche des conseils sur l’événement défini via `IConnection`.  
  
3.  Un point de connexion détermine le nombre de connexions (un ou plusieurs) autorise dans son implémentation de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un point de connexion qui ne permet qu’une seule interface peut retourner <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> à partir de la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> (méthode).  
  
4.  Un client peut appeler le `IConnection` interface pour obtenir l’accès à un sous-objet énumérateur avec le <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. Le <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface peut ensuite être appelée pour énumérer les points de connexion pour chaque interface sortante ID (IID).  
  
5.  `IConnection`peut également être appelée pour obtenir l’accès à la connexion sous-objets point avec les <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface pour chaque IID sortant. Via le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface, un client démarre ou arrête une boucle de Conseil avec l’objet connectable et la synchronisation du client. Le client peut également appeler le <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface pour obtenir un objet énumérateur avec le <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interface pour énumérer les connexions qu’il connaît.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a>Lors de l’obtention des Descriptions de champs à partir de la fenêtre Propriétés
En bas de la fenêtre **Propriétés** , une zone de description affiche des informations relatives au champ de propriété sélectionné. Cette fonctionnalité est activée par défaut. Si vous voulez masquer le champ de description, cliquez avec le bouton droit sur la fenêtre **Propriétés** et cliquez sur **Description**. Cette action supprime également la coche à côté du titre **Description** dans la fenêtre de menu. Vous pouvez afficher le champ à nouveau en suivant la même procédure pour réactiver **Description** .  
  
 Les informations dans le champ de description proviennent de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Chaque méthode, interface, coclasse, etc. peut avoir un attribut `helpstring` non localisé dans la bibliothèque de types. Le **propriétés** fenêtre récupère la chaîne à partir de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Pour spécifier des chaînes d’aide localisées  
  
1.  Ajoutez l’attribut `helpstringdll` à l’instruction library dans la bibliothèque de types (`typelib`).  
  
    > [!NOTE]
    >  Cette étape est facultative si la bibliothèque de types se trouve dans un fichier de bibliothèque d’objets (.olb).  
  
2.  Spécifiez des attributs `helpstringcontext` pour les chaînes. Vous pouvez également spécifier des attributs `helpstring` .  
  
     Ces attributs sont distincts des attributs `helpfile` et `helpcontext` qui sont contenus dans les vraies rubriques d’aide du fichier .chm.  
  
 Pour récupérer les informations de description à afficher pour le nom de la propriété mise en surbrillance, le **propriétés** fenêtre appels <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> pour la propriété est sélectionnée, en spécifiant l’élément `lcid` d’attribut pour le chaîne de sortie. En interne, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> recherche le fichier .dll spécifié dans le `helpstringdll` attribut et les appels `DLLGetDocumentation` sur ce fichier .dll avec le contexte spécifié et `lcid` attribut.  
  
 La signature et l’implémentation de `DLLGetDocumentation` sont les suivantes :  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 La fonction `DLLGetDocumentation` doit être une exportation définie dans le fichier .def pour la DLL.  
  
 En interne, un fichier .olb est créé, qui est effectivement une DLL. Cette DLL contient une ressource, le fichier de bibliothèque de types (.tlb) et une fonction exportée, `DLLGetDocumentation`.  
  
 Dans le cas des fichiers .olb, l’attribut `helpstringdll` est facultatif, car il s’agit du même fichier qui contient le fichier .tlb lui-même.  
  
 Par conséquent, pour que des chaînes s’affichent dans le volet **Descriptions** , vous devez au moins spécifier l’attribut `helpstring` dans la bibliothèque de types. Si vous voulez que ces chaînes soient localisées, vous devez spécifier l’attribut `helpstringdll` (facultatif) et l’attribut `helpstringcontext` (obligatoire), et implémenter `DLLGetDocumentation`.  
  
 Aucune autre interface ne doit être implémentée lors de la localisation d’informations par le biais de l’attribut `helpstringcontext` d’idl et `DLLGetDocumentation`.  
  
 Une autre façon d’obtenir le nom localisé et la description d’une propriété est en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Pour plus d’informations sur l’implémentation de cette méthode, consultez [champs de la fenêtre Propriétés et les Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés](../../extensibility/internals/extending-properties.md)