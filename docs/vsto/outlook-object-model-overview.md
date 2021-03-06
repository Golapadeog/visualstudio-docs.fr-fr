---
title: "Vue d’ensemble du modèle d’objet Outlook | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 481a18d40f17aa5488afabf1dd04f3cf6ed345b9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="outlook-object-model-overview"></a>Vue d'ensemble du modèle d'objet Outlook
  Pour développer des compléments VSTO pour Microsoft Office Outlook, vous pouvez interagir avec les objets fournis par le modèle objet Outlook. Le modèle objet Outlook fournit des classes et des interfaces qui représentent des éléments dans l'interface utilisateur. Par exemple, l'objet <xref:Microsoft.Office.Interop.Outlook.Application> représente l'application entière, l'objet <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> représente un dossier qui contient des messages électroniques ou d'autres éléments, et l'objet <xref:Microsoft.Office.Interop.Outlook.MailItem> représente un message électronique.  
  
 Cette rubrique fournit une brève présentation de certains objets principaux du modèle objet Outlook. Pour obtenir la liste des ressources fournissant des informations complémentaires sur le modèle objet Outlook complet, consultez [Utilisation de la documentation du modèle objet Outlook](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire : utiliser Outlook pour créer un rapport des tâches personnalisé ?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="accessing-objects-in-an-outlook-project"></a>Accès aux objets dans un projet Outlook  
 Outlook fournit de nombreux objets avec lesquels vous pouvez interagir. Pour utiliser le modèle objet efficacement, vous devez être familiarisé avec les objets de niveau supérieur suivants :  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Objet Application  
 L'objet <xref:Microsoft.Office.Interop.Outlook.Application> représente l'application Outlook. Il s'agit de l'objet de niveau supérieur le plus élevé dans le modèle objet Outlook. Voici quelques-uns des membres les plus importants de cet objet :  
  
-   la méthode [CreateItem](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) , qui vous permet de créer un élément tel qu'un message électronique, une tâche ou un rendez-vous ;  
  
-   la propriété <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> , qui vous permet d'accéder aux fenêtres affichant le contenu d'un dossier dans l'interface utilisateur d'Outlook ;  
  
-   la propriété <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> , qui vous permet d'accéder aux fenêtres affichant le contenu d'un élément unique, par exemple un message électronique ou une demande de réunion.  
  
 Pour obtenir une instance de la <xref:Microsoft.Office.Interop.Outlook.Application> d’objet, utilisez le champ d’Application de la `ThisAddIn` classe dans votre projet. Pour plus d'informations, consultez [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Pour éviter les avertissements de sécurité lorsque vous utilisez des propriétés et méthodes qui sont bloqués par le modèle objet Outlook, récupérez les objets Outlook à partir du champ d’Application de la `ThisAddIn` classe. Pour plus d'informations, consultez [Specific Security Considerations for Office Solutions](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Objet Explorer  
 L'objet <xref:Microsoft.Office.Interop.Outlook.Explorer> représente une fenêtre qui affiche le contenu d'un dossier comprenant des éléments tels que des messages électroniques, des tâches ou des rendez-vous. L'objet <xref:Microsoft.Office.Interop.Outlook.Explorer> inclut les méthodes et propriétés que vous pouvez utiliser pour modifier la fenêtre, ainsi que les événements qui sont déclenchés quand la fenêtre change.  
  
 Pour obtenir un objet <xref:Microsoft.Office.Interop.Outlook.Explorer> , effectuez l'une des opérations suivantes :  
  
-   Utilisez la propriété <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> pour accéder à tous les objets <xref:Microsoft.Office.Interop.Outlook.Explorer> dans Outlook.  
  
-   Utilisez la méthode <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> pour obtenir le <xref:Microsoft.Office.Interop.Outlook.Explorer> qui possède actuellement le focus.  
  
-   Utilisez la méthode GetExplorer de la <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> objet pour lequel obtenir le <xref:Microsoft.Office.Interop.Outlook.Explorer> du dossier actif.  
  
### <a name="inspector-object"></a>Objet Inspector  
 L'objet <xref:Microsoft.Office.Interop.Outlook.Inspector> représente une fenêtre qui affiche un élément unique, par exemple un message électronique, une tâche ou un rendez-vous. L'objet <xref:Microsoft.Office.Interop.Outlook.Inspector> inclut les méthodes et propriétés que vous pouvez utiliser pour modifier la fenêtre, ainsi que les événements qui sont déclenchés quand la fenêtre change.  
  
 Pour obtenir un objet <xref:Microsoft.Office.Interop.Outlook.Inspector> , effectuez l'une des opérations suivantes :  
  
-   Utilisez la propriété <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> pour accéder à tous les objets <xref:Microsoft.Office.Interop.Outlook.Inspector> dans Outlook.  
  
-   Utilisez la méthode <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> pour obtenir le <xref:Microsoft.Office.Interop.Outlook.Inspector> qui possède actuellement le focus.  
  
-   Utilisez la méthode GetInspector d’un élément spécifique, comme un <xref:Microsoft.Office.Interop.Outlook.MailItem> ou <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, pour récupérer l’inspecteur qui lui est associé.  
  
### <a name="mapifolder-object"></a>Objet MAPIFolder  
 L'objet <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> représente un dossier qui contient les messages électroniques, les contacts, les tâches et d'autres éléments. Outlook fournit 16 objets <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> par défaut.  
  
 Les objets <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> par défaut sont définis par les valeurs d'énumération <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> . Par exemple :  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox correspond à la **boîte de réception** dossier dans Outlook.  
  
 Pour obtenir un exemple qui montre comment accéder à une valeur par défaut <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> et créer un nouveau <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>, consultez [Comment : créer par programme les éléments de dossier de personnalisés](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>Objet MailItem  
 L'objet <xref:Microsoft.Office.Interop.Outlook.MailItem> représente un message électronique. Les objets<xref:Microsoft.Office.Interop.Outlook.MailItem> se trouvent généralement dans des dossiers, par exemple **Boîte de réception**, **Éléments envoyés**et **Boîte d'envoi**. <xref:Microsoft.Office.Interop.Outlook.MailItem> expose les propriétés et méthodes qui peuvent être utilisées pour créer et envoyer des messages électroniques.  
  
 Pour obtenir un exemple qui montre comment créer un message électronique, consultez [Comment : créer par programme un élément de messagerie](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>Objet AppointmentItem  
 L'objet <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> représente une réunion, un rendez-vous unique, ou un rendez-vous ou une réunion périodique, dans le dossier **Calendrier** . L'objet <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> inclut des méthodes qui effectuent des actions telles que répondre à des demandes de réunion ou les transférer, ainsi que des propriétés qui spécifient les détails de la réunion, par exemple le lieu et l'heure.  
  
 Pour obtenir un exemple qui montre comment créer un rendez-vous, consultez [Comment : créer par programmation une demande de réunion](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>Objet TaskItem  
 L'objet <xref:Microsoft.Office.Interop.Outlook.TaskItem> représente une tâche à exécuter dans un laps de temps spécifique. Les objets<xref:Microsoft.Office.Interop.Outlook.TaskItem> se trouvent dans le dossier **Tâches** .  
  
 Pour créer une tâche, utilisez la méthode [CreateItem](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) de l'objet <xref:Microsoft.Office.Interop.Outlook.Application> , puis passez la valeur <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> pour le paramètre.  
  
### <a name="contactitem-object"></a>Objet ContactItem  
 L'objet <xref:Microsoft.Office.Interop.Outlook.ContactItem>représente un contact dans le dossier **Contacts** . Les objets<xref:Microsoft.Office.Interop.Outlook.ContactItem> contiennent diverses informations de contact pour les personnes qu'ils représentent, par exemple des adresses postales, des adresses de messagerie et des numéros de téléphone.  
  
 Pour obtenir un exemple qui montre comment créer un contact, consultez [Comment : ajouter par programmation une entrée aux Contacts Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Pour obtenir un exemple qui montre comment rechercher un contact existant, consultez [Comment : rechercher par programme un Contact spécifique](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Utilisation de la documentation du modèle objet Outlook  
 Pour obtenir des informations complètes sur le modèle objet Outlook, vous pouvez consulter la documentation de référence de l'assembly PIA (Primary Interop Assembly) Outlook et la documentation de référence du modèle objet VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Documentation de référence de l'assembly PIA (Primary Interop Assembly)  
 La documentation de référence de l'assembly PIA Outlook décrit les types des assemblys PIA (Primary Interop Assembly) pour Outlook 2010. Pour plus d’informations, consultez [Documentation de référence de l’assembly PIA (Primary Interop Assembly)](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Outre la fourniture d'informations sur tous les types des assemblys PIA (Primary Interop Assembly), cette documentation propose également des informations supplémentaires sur la structure des assemblys PIA (Primary Interop Assembly), ainsi que des exemples de code pour les tâches courantes basées sur la technologie Automation dans Outlook.  
  
### <a name="vba-object-model-reference"></a>Documentation de référence du modèle objet VBA  
 La documentation de référence du modèle objet VBA présente le modèle objet Outlook tel qu'il est exposé au code VBA (Visual Basic pour Applications). Pour plus d’informations, consultez [Référence du modèle objet Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Tous les objets et membres mentionnés dans la documentation de référence du modèle objet VBA correspondent aux types et aux membres de l'assembly PIA Outlook. Par exemple, l’objet Inspector dans la référence du modèle objet VBA correspond à la <xref:Microsoft.Office.Interop.Outlook.Inspector> objet dans l’assembly PIA Outlook. Même si la documentation de référence du modèle objet VBA fournit des exemples de code pour la plupart des propriétés, méthodes et événements, vous devez traduire le code VBA fourni dans la documentation de référence en Visual Basic ou Visual C# pour pouvoir les utiliser dans un projet de complément Outlook VSTO créé à l'aide de Visual Studio.  
  
### <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Utilisation des éléments de contact](../vsto/working-with-contact-items.md)|Fournit des rubriques qui montrent comment effectuer des tâches avec des contacts.|  
|[Utilisation d’éléments de messagerie](../vsto/working-with-mail-items.md)|Fournit des rubriques qui montrent comment effectuer des tâches avec des éléments de messagerie.|  
|[Utilisation des dossiers](../vsto/working-with-folders.md)|Fournit des rubriques qui montrent comment effectuer des tâches avec des dossiers.|  
|[Utilisation des éléments du calendrier](../vsto/working-with-calendar-items.md)|Fournit des rubriques qui montrent comment effectuer des tâches avec des éléments du calendrier.|  
|[Guide pratique pour déterminer l’élément Outlook actuel par programmation](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Montre comment afficher le nom du dossier actuel, ainsi que certaines informations sur l'élément sélectionné.|  
  