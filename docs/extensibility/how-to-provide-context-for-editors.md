---
title: "Comment : fournir un contexte pour les éditeurs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d9b89c4e45f8268df55386d321816325fb50174c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-context-for-editors"></a>Comment : fournir un contexte pour les éditeurs
Pour un éditeur, le contexte est actif uniquement lorsque l’éditeur a le focus ou avait le focus immédiatement avant le focus a été déplacé vers une fenêtre outil. Vous pouvez fournir le contexte pour un éditeur en procédant comme suit :  
  
1.  Créer un conteneur de contexte.  
  
2.  Publier le conteneur de contexte à l’identificateur d’élément de sélection (SEID).  
  
3.  Mettre à jour le contexte dans le conteneur.  
  
 Ces tâches sont couverts par les procédures suivantes. Pour plus d’informations sur la fourniture de contexte, consultez **programmation robuste** plus loin dans cette rubrique.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Pour créer un conteneur de contexte pour un éditeur ou un concepteur  
  
1.  Appelez `QueryService` sur votre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> de l’interface pour le <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> service.  
  
     Un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interface est retournée.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> pour créer un conteneur de contexte ou sous-contexte nouvelle méthode.  
  
     Un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interface est retournée.  
  
3.  Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> méthode pour ajouter des attributs, des mots clés de recherche ou des mots clés F1 pour le conteneur de contexte ou sous-contexte.  
  
4.  Si vous créez un conteneur sous-contexte, appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> méthode pour lier le sac sous-contexte pour le conteneur de contexte parent.  
  
5.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> pour recevoir une notification lorsque le **aide dynamique** fenêtre est sur le point de mise à jour.  
  
     Ayant la **aide dynamique** fenêtre appeler votre éditeur lorsqu’il est prêt à mettre à jour vous permet de retarder la modification du contexte jusqu'à ce que la mise à jour se produit. Cela peut améliorer les performances, car il permet de différer l’exécution des algorithmes qui prennent du temps, jusqu'à ce que la durée d’inactivité système n’est disponible.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Pour publier le conteneur de contexte pour le SEID  
  
1.  Appelez `QueryService` sur la <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> service pour retourner un pointeur vers le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interface.  
  
2.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, en spécifiant un identificateur de l’élément (`elementid` paramètre) la valeur de SEID_UserContext pour indiquer que vous passez un contexte au niveau global.  
  
3.  Lorsque l’éditeur ou du concepteur devient actif, les valeurs dans son <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objet sont propagées à la sélection globale. Vous devez uniquement terminer ce processus une fois par session, puis stocker le pointeur vers le contexte global créé lorsque vous avez appelé <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Pour mettre à jour le conteneur de contexte  
  
1.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> pour vous assurer que le **aide dynamique** fenêtre appelle l’éditeur ou le concepteur avant la mise à jour.  
  
     Pour chaque conteneur de contexte qui a appelé <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> une fois le conteneur de contexte est créé et qu’il a implémenté <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, les appels IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> pour notifier le fournisseur de contexte que le conteneur de contexte sera mise à jour. Vous pouvez utiliser cet appel pour modifier les attributs et les mots clés dans le conteneur de contexte et dans des sachets sous-contexte d’avant la **aide dynamique** mise à jour de la fenêtre.  
  
2.  Appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> sur le conteneur de contexte pour indiquer que l’éditeur ou du concepteur a nouveau contexte.  
  
     Lorsque le **aide dynamique** fenêtre appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> pour indiquer qu’elle est mise à jour, l’éditeur ou le concepteur peut mettre à jour le contexte de manière appropriée pour le conteneur de contexte parent et les conteneurs sous-contexte à ce moment-là.  
  
    > [!NOTE]
    >  Le `SetDirty` est automatiquement défini à `true` chaque fois que le contexte est ajouté ou retiré le sac de contextes. Le **aide dynamique** fenêtre appelle uniquement <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> sur le conteneur de contexte si les `SetDirty` est défini à `true`. Il est réinitialisé à `false` après la mise à jour.  
  
3.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> pour ajouter le contexte à la collection de contexte actif ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> pour supprimer le contexte.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si vous écrivez votre propre éditeur, vous devez effectuer les trois procédures décrites dans cette rubrique pour fournir un contexte pour l’éditeur.  
  
> [!NOTE]
>  Pour activer correctement une fenêtre d’éditeur ou concepteur et vous assurer que le routage de commande est mis à jour correctement, vous devez appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> sur le composant pour rendre la fenêtre de focus.  
  
 Le SEID est une collection de propriétés qui changent en fonction de la sélection. SEID informations sont disponibles via la sélection globale. La sélection globale est câblée dans les événements déclenchés par le <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interface, et a une liste de tous les éléments qui est sélectionné (éditeur actuel, fenêtre Outil active, hiérarchie actuelle et ainsi de suite).  
  
 Pour les éditeurs et concepteurs, dans le contexte peut changer chaque fois que le curseur se déplace dans un mot, il est inutile d’actualiser en permanence le sac de contextes. Pour effectuer la mise à jour plus efficace chaque fois que vous détectez le curseur se déplace dans l’éditeur ou de la fenêtre du concepteur, vous pouvez appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Cela permet de conserver vos changements de contexte jusqu'à ce qu’il est temps d’inactivité et le service de contexte de l’IDE envoie une notification à l’éditeur ou du concepteur qui le **aide dynamique** mise à jour de la fenêtre. Cette approche est utilisée dans la procédure « pour mettre à jour le conteneur de contexte » dans cette rubrique.  
  
 Après avoir entré le contexte des activités au sein de votre éditeur ou du concepteur, vous devez fournir un mot-clé F1 pour permettre aux utilisateurs d’obtenir de l’aide de l’éditeur ou du concepteur lui-même.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>