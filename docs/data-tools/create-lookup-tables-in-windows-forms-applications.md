---
title: "Créer des tables de recherche dans les applications Windows Forms | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: f27fdbe216b6ba2a738f6d9f45d746344d542b38
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Créer des tables de recherche dans les applications Windows Forms
Le terme *table de recherche* décrit les contrôles qui sont liés aux tables de données connexes deux. Ces contrôles de recherche affichent les données à partir de la première table selon une valeur sélectionnée dans la seconde table.  
  
 Vous pouvez créer des tables de choix en faisant glisser le nœud principal d’une table parente (à partir de la [fenêtre Sources de données](add-new-data-sources.md)) vers un contrôle sur votre formulaire déjà lié à la colonne dans la table enfant connexe.  
  
 Par exemple, prenons une table `Orders` dans une base de données de ventes. Chaque enregistrement dans le `Orders` table inclut une `CustomerID`, indiquant le client qui a passé la commande. Le `CustomerID` est une clé étrangère pointant vers un enregistrement de client dans le `Customers` table. Dans ce scénario, vous développez le `Orders` de table dans le **des Sources de données** fenêtre et la valeur du nœud principal **détails**. Puis définissez la `CustomerID` colonne à utiliser un <xref:System.Windows.Forms.ComboBox> (ou tout autre contrôle qui prend en charge la liaison de correspondance), puis faites glisser le `Orders` nœud vers votre formulaire. Enfin, faites glisser le `Customers` nœud sur le contrôle qui est lié à la colonne associée, dans ce cas, le <xref:System.Windows.Forms.ComboBox> lié à la `CustomerID` colonne.  
  
## <a name="to-databind-a-lookup-control"></a>Pour un contrôle de recherche de databind  
  
1.  Ouvrez le **des Sources de données** fenêtre.  
  
    > [!NOTE]
    >  Tables de correspondance nécessitent que deux tables ou objets connexes sont disponibles dans le **des Sources de données** fenêtre. Pour plus d’informations, consultez [des relations dans les jeux de données](relationships-in-datasets.md).  
  
2.  Développez les nœuds dans le **des Sources de données** fenêtre jusqu'à ce que vous pouvez voir la table parente et toutes ses colonnes et la table enfant associée et toutes ses colonnes.  
  
    > [!NOTE]
    >  Le nœud de la table enfant est le nœud qui apparaît sous la forme d’un nœud enfant peut être développé dans la table parente.  
  
3.  Modifier le type de déplacement de la table enfant à **détails** en sélectionnant **détails** à partir de la liste de contrôle sur le nœud de la table enfant. Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
4.  Localisez le nœud qui relie les deux tables (le `CustomerID` nœud dans l’exemple précédent). Modifier son type de déplacement pour une <xref:System.Windows.Forms.ComboBox> en sélectionnant **ComboBox** à partir de la liste de contrôle.  
  
5.  Faites glisser le nœud de la table enfant principal à partir de la **des Sources de données** fenêtre vers votre formulaire.  
  
     Suppriment les contrôles liés aux données (avec des étiquettes descriptives) et un outil (<xref:System.Windows.Forms.BindingNavigator>) apparaissent dans le formulaire. A [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, et <xref:System.Windows.Forms.BindingNavigator> s’affichent dans la barre d’état du composant.  
  
6.  Maintenant, faites glisser le nœud de la table parent principal à partir de la **des Sources de données** fenêtre directement sur le contrôle de liste de choix (la <xref:System.Windows.Forms.ComboBox>).  
  
     Les liaisons de recherche sont désormais établis. Reportez-vous au tableau ci-dessous pour les propriétés spécifiques qui ont été définies sur le contrôle.  
  
    |Propriété|Explication du paramètre|  
    |--------------|----------------------------|  
    |**Source de données**|Visual Studio définit cette propriété sur le <xref:System.Windows.Forms.BindingSource> créé pour la table que vous avez fait glisser vers le contrôle (et non sur le <xref:System.Windows.Forms.BindingSource> créé en même temps que le contrôle).<br /><br /> Si vous avez besoin de faire des réglages, définissez la <xref:System.Windows.Forms.BindingSource> de la table contenant la colonne que vous souhaitez afficher.|  
    |**DisplayMember**|Visual Studio définit cette propriété sur la première colonne après la clé principale contenant un type de données de chaîne pour la table que vous avez fait glisser vers le contrôle.<br /><br /> Si vous avez besoin de faire des réglages, puis affectez la valeur le nom de colonne que vous souhaitez afficher.|  
    |**ValueMember**|Visual Studio définit cette propriété sur la première colonne participant à la clé principale, ou la première colonne de la table si aucune clé n'est définie.<br /><br /> Si vous avez besoin de faire des réglages, définissez à la clé primaire dans la table avec la colonne que vous souhaitez afficher.|  
    |**SelectedValue**|Visual Studio définit cette propriété sur la colonne d’origine déplacée à partir de la **des Sources de données** fenêtre.<br /><br /> Si vous avez besoin de faire des réglages, définissez à la colonne de clé étrangère dans la table associée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Lier des contrôles Windows Forms à des données dans Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)