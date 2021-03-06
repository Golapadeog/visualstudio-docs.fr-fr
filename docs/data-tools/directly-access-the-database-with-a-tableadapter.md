---
title: "Accéder directement à la base de données avec un TableAdapter | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 5fc7167e75aea963d43a482416b7592dcda55ee8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Accéder directement à la base de données avec un TableAdapter
Outre la `InsertCommand`, `UpdateCommand`, et `DeleteCommand`, les TableAdapters sont créés avec des méthodes qui peuvent être exécutées directement sur la base de données. Ces méthodes (`TableAdapter.Insert`, `TableAdapter.Update`, et `TableAdapter.Delete`) peut être appelé pour manipuler des données directement dans la base de données.  
  
 Si vous ne souhaitez pas créer ces méthodes directes, affectez à la `GenerateDbDirectMethods` propriété `false` dans les **propriétés** fenêtre. Si toutes les requêtes sont ajoutés à un TableAdapter en plus de la requête du TableAdapter principal, ils sont des requêtes autonomes qui ne génèrent pas ces méthodes DbDirect.  
  
## <a name="send-commands-directly-to-a-database"></a>Envoyer des commandes directement à une base de données  
 Appelez la méthode DbDirect du TableAdapter qui exécute la tâche que vous essayez d’accomplir.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Pour insérer de nouveaux enregistrements directement dans une base de données  
  
-   Appelez la `Insert` méthode, en passant les valeurs pour chaque colonne en tant que paramètres. La procédure suivante utilise le `Region` table dans la base de données exemple Northwind.  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Pour mettre à jour des enregistrements directement dans une base de données  
  
-   Appelez la `Update` méthode, en passant les valeurs nouvelles et d’origine pour chaque colonne en tant que paramètres.  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Pour supprimer des enregistrements directement à partir d’une base de données  
  
-   Appelez la `Delete` méthode, en passant les valeurs pour chaque colonne en tant que paramètres de la `Delete` (méthode). La procédure suivante utilise le `Region` table dans la base de données exemple Northwind.  
  
    > [!NOTE]
    >  Si vous n’avez pas d’instance disponible, instanciez le TableAdapter que vous souhaitez utiliser.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Remplir des datasets à l’aide de TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)