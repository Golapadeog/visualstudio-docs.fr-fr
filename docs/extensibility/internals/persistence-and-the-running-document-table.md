---
title: "Persistance et l’exécution de Table Document | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7f48a1acdad3856e7334ce6a86b48e67c880f9c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-and-the-running-document-table"></a>Persistance et la Table de Document en cours d’exécution
Dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, les projets sont entièrement responsables de la gestion de la persistance de leurs éléments de projet, ils accomplir à l’aide du service, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Les documents sont l’unité de base de persistance dans l’environnement Visual Studio. Projets de coordonnent l’ouverture, l’enregistrement et la modification du nom des documents avec la table document en cours d’exécution (r & DT), une ressource qui effectue le suivi de l’état de tous les documents ouverts.  
  
## <a name="managing-persistence"></a>La gestion de persistance  
 Projets de contrôle de service de persistance de l’environnement en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interface. Alors que l’environnement de demande jamais directement à un document persistant, il demande le projet propriétaire (ou hiérarchie) pour enregistrer le document. Cela rend possible pour le projet enregistrer ses données d’élément de projet dans les fichiers locaux, les fichiers à distance, une base de données, un référentiel ou autre support.  
  
 L’environnement global conserve la r & DT. L’environnement conserve les entrées pour toutes les fenêtres et documents dans la r & DT, ce qui rend possible pour pouvoir recevoir des notifications spéciale, tels que lors de la fermeture d’une solution. En outre, la r & DT permet à l’environnement effectuer le suivi de leurs nœuds correspondants dans **l’Explorateur de solutions**. La r & DT conserve un enregistrement par objet ouvert, persistant, y compris les fichiers projet et les documents de l’élément de projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Table de Document en cours d’exécution](../../extensibility/internals/running-document-table.md)   
 [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)