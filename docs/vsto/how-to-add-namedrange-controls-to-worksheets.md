---
title: "Comment : ajouter des contrôles NamedRange aux feuilles de calcul | Documents Microsoft"
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
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ef0ec1846a4ef75200fa6d37f137ca1ab1d70f48
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Comment : ajouter des contrôles NamedRange aux feuilles de calcul
  Vous pouvez ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul Microsoft Office Excel au moment de la conception et au moment de l’exécution dans des projets au niveau du document.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous pouvez aussi ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> au moment de l’exécution dans des projets de complément VSTO.  
  
 Cette rubrique décrit les tâches suivantes :  
  
-   [Ajout de contrôles NamedRange au moment de la conception](#designtime)  
  
-   [Ajout de contrôles NamedRange au moment de l’exécution dans un projet au niveau du document](#runtimedoclevel)  
  
-   [Ajout de contrôles NamedRange au moment de l’exécution dans un projet de complément VSTO](#runtimeaddin)  
  
 Pour plus d’informations sur les contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> , consultez [NamedRange Control](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Adding NamedRange Controls at Design Time  
 Il existe plusieurs façons d’ajouter des contrôles <xref:Microsoft.Office.Tools.Excel.NamedRange> à une feuille de calcul dans un projet au niveau du document au moment de la conception : dans Excel, à partir de la **Boîte à outils**Visual Studio, et à partir de la fenêtre **Sources de données** .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul via la Zone Nom d’Excel  
  
1.  Sélectionnez la ou les cellules que vous souhaitez inclure dans l'étendue nommée.  
  
2.  Dans la **Zone Nom**, tapez un nom pour la plage et appuyez sur Entrée.  
  
     La **Zone Nom** se trouve à côté de la barre de formule, juste au-dessus de la colonne **A** de la feuille de calcul.  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul via la Boîte à outils  
  
1.  Ouvrez la **Boîte à outils** , puis cliquez sur l’onglet **Contrôles Excel** .  
  
2.  Cliquez sur <xref:Microsoft.Office.Tools.Excel.NamedRange> et faites-le glisser vers une feuille de calcul.  
  
     La boîte de dialogue **Ajouter une plage nommée** s’affiche.  
  
3.  Sélectionnez la ou les cellules que vous souhaitez inclure dans l'étendue nommée.  
  
4.  Cliquez sur **OK**.  
  
     Si vous ne voulez pas du nom attribué par défaut au contrôle, vous pouvez le modifier dans la fenêtre **Propriétés** .  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul via la fenêtre Sources de données  
  
1.  Ouvrez la fenêtre **Sources de données** et créez une source de données pour votre projet. Pour plus d’informations, consultez [ajouter de nouvelles connexions](../data-tools/add-new-connections.md).  
  
2.  Faites glisser un seul champ de la fenêtre **Sources de données** vers votre feuille de calcul.  
  
     Un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> lié aux données est ajouté à la feuille de calcul. Pour plus d'informations, consultez [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Adding NamedRange Controls at Run Time in a Document-Level Project  
 Vous pouvez ajouter un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôle par programmation à votre feuille de calcul au moment de l’exécution. Cela vous permet de créer les contrôles hôtes en réponse à des événements. Les plages nommées créées dynamiquement ne sont pas conservées dans la feuille de calcul en tant que contrôles hôtes au moment où la feuille de calcul est fermée. Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul par programmation  
  
1.  Dans le gestionnaire d’événements <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, insérez le code suivant pour ajouter le contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule **A1** et attribuez à sa propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> la valeur `Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Adding NamedRange Controls at Run Time in an VSTO Add-in project  
 Vous pouvez ajouter un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> par programmation à une feuille de calcul ouverte dans un projet de complément VSTO. Les plages nommées créées dynamiquement ne sont pas conservées dans la feuille de calcul en tant que contrôles hôtes au moment où la feuille de calcul est fermée. Pour plus d'informations, consultez [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Pour ajouter un contrôle NamedRange à une feuille de calcul par programmation  
  
1.  Le code suivant génère un élément hôte de feuille de calcul basé sur la feuille de calcul ouverte, puis ajoute un contrôle <xref:Microsoft.Office.Tools.Excel.NamedRange> à la cellule **A1** et attribue à sa propriété <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> la valeur `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des Documents Office](../vsto/controls-on-office-documents.md)   
 [NamedRange (contrôle)](../vsto/namedrange-control.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Comment : redimensionner les contrôles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  