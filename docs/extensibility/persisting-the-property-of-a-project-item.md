---
title: Persistance de la propriété d’un élément de projet | Documents Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6f569a8fe57a215a4fcce31de53c8c4a59f51177
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="persisting-the-property-of-a-project-item"></a>Persistance de la propriété d’un élément de projet
Voulez-vous conserver une propriété que vous ajoutez à un élément de projet, telles que l’auteur d’un fichier source. Pour cela, en stockant la propriété dans le fichier projet.

 La première étape pour conserver une propriété dans un fichier de projet consiste à obtenir de la hiérarchie du projet en tant qu’un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface. Vous pouvez obtenir cette interface à l’aide d’Automation ou à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Une fois que vous obtenez l’interface, vous pouvez l’utiliser pour déterminer quel élément de projet est actuellement sélectionné. Une fois que vous avez l’ID d’élément de projet, vous pouvez utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> pour ajouter la propriété.

 Dans les procédures suivantes, vous rendre persistante la propriété VsPkg.cs `Author` avec la valeur `Tom` dans le fichier projet.

### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Pour obtenir la hiérarchie de projet avec l’objet DTE

1.  Ajoutez le code suivant à votre VSPackage :

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Pour conserver la propriété d’élément de projet avec l’objet DTE

1.  Ajoutez le code suivant au code donné dans la méthode dans la procédure précédente :

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Pour obtenir la hiérarchie de projet à l’aide de IVsMonitorSelection

1.  Ajoutez le code suivant à votre VSPackage :

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

2.

### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Pour conserver la propriété d’élément de projet sélectionné, étant donné la hiérarchie de projet

1.  Ajoutez le code suivant au code donné dans la méthode dans la procédure précédente :

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-verify-that-the-property-is-persisted"></a>Pour vérifier que la propriété est persistant.

1.  Démarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et puis ouvrez ou créez une solution.

2.  Sélectionnez le projet d’élément VsPkg.cs dans **l’Explorateur de solutions**.

3.  Utiliser un point d’arrêt ou de déterminer que votre VSPackage est chargé et que SetItemAttribute s’exécute.

    > [!NOTE]
    > Vous pouvez utiliser autoload un VSPackage dans le contexte de l’interface utilisateur <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Pour plus d’informations, consultez [le chargement des VSPackages](../extensibility/loading-vspackages.md).

4.  Fermer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puis ouvrez le fichier projet dans le bloc-notes. Vous devez voir le \<auteur > balise avec la valeur Tom, comme suit :

    ```xml
    <Compile Include="VsPkg.cs">
        <Author>Tom</Author>
    </Compile>
    ```

## <a name="see-also"></a>Voir aussi

- [Outils personnalisés](../extensibility/internals/custom-tools.md)