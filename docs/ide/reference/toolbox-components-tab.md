---
title: "Boîte à outils, onglet Composants | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: aa91db706d7e1236162ef69e6fd31e791ed44dbb
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="toolbox-components-tab"></a>Boîte à outils, onglet Composants

Affiche les composants que vous pouvez ajouter aux concepteurs Visual Basic et C#. En plus des composants .NET Framework inclus avec Visual Studio, tels que les composants <xref:System.Messaging.MessageQueue> et <xref:System.Diagnostics.EventLog>, vous pouvez ajouter vos propres composants ou des composants tiers à cet onglet.
  
 Pour afficher cet onglet, dans le menu **Affichage**, sélectionnez **Boîte à outils**. Dans la **boîte à outils**, sélectionnez l’onglet **Composants**.  
  
 **BackgroundWorker**  
 Crée une instance du composant `System.ComponentModel.BackgroundWorker` qui peut exécuter une opération sur un thread dédié distinct.  
  
 **DirectoryEntry**  
 Crée une instance du composant <xref:System.DirectoryServices.DirectoryEntry> qui encapsule un nœud ou un objet dans la hiérarchie Active Directory et qui peut être utilisé pour interagir avec les fournisseurs de services Active Directory.  
  
 **DirectorySearcher**  
 Crée une instance du composant <xref:System.DirectoryServices.DirectorySearcher> que vous pouvez utiliser pour effectuer des requêtes sur Active Directory.  
  
 **ErrorProvider**  
 Crée une instance du composant `System.Windows.Forms.ErrorProvider` qui indique à l’utilisateur final qu’une erreur est associée à un contrôle sur un formulaire.  
  
 **EventLog**  
 Crée une instance du composant <xref:System.Diagnostics.EventLog> que vous pouvez utiliser pour interagir avec des journaux des événements système et personnalisés, ce qui inclut l’écriture d’événements dans un journal et la lecture de données de journal.
  
 **FileSystemWatcher**  
 Crée une instance du composant <xref:System.IO.FileSystemWatcher> que vous pouvez utiliser pour surveiller les modifications apportées à tout répertoire ou fichier auquel vous avez accès.
  
 **HelpProvider**  
 Crée une instance du composant `System.Windows.Forms.HelpProvider` qui fournit une aide contextuelle ou en ligne pour les contrôles.  
  
 **ImageList**  
 Crée une instance du composant `System.Windows.Forms.ImageList` qui fournit des méthodes pour gérer une collection d’objets `System.Drawing.Image`.  
  
 **MessageQueue**  
 Crée une instance du composant <xref:System.Messaging.MessageQueue> que vous pouvez utiliser pour interagir avec les files d’attente de messages, notamment pour lire des messages à partir de files d’attente et écrire des messages dans ces dernières, traiter des transactions et effectuer des tâches d’administration de files d’attente.

 **PerformanceCounter**  
 Crée une instance du composant <xref:System.Diagnostics.PerformanceCounter> que vous pouvez utiliser pour interagir avec les compteurs de performance Windows, notamment pour créer des catégories et des instances, lire des valeurs à partir de compteurs et effectuer des calculs sur des données de compteurs.
  
 **Process**  
 Crée une instance du composant <xref:System.Diagnostics.Process> que vous pouvez utiliser pour arrêter, démarrer et manipuler les données associées à des processus sur votre système.
  
 **SerialPort**  
 Crée une instance du composant `System.IO.Ports.SerialPort` qui fournit les E/S synchrones et pilotées par les événements, l’accès aux états épinglés et interrompus, ainsi que l’accès aux propriétés des pilotes série.  
  
 **ServiceController**  
 Crée une instance du composant <xref:System.ServiceProcess.ServiceController> que vous pouvez utiliser pour manipuler des services existants, notamment pour démarrer et arrêter des services, ainsi que pour envoyer des commandes vers ceux-ci.
  
 **Minuterie**  
 Crée une instance du composant <xref:System.Windows.Forms.Timer> que vous pouvez utiliser pour ajouter une fonctionnalité à durée définie à vos applications Windows. Pour plus d’informations, consultez [Timer, composant](/dotnet/framework/winforms/controls/timer-component-windows-forms).  
  
> [!NOTE]
>  Il existe également un composant <xref:System.Timers.Timer> basé sur le système que vous pouvez ajouter à la **boîte à outils**. Ce <xref:System.Timers.Timer> est optimisé pour les applications serveur. Le <xref:System.Windows.Forms.Timer> Windows Forms, quant à lui, convient mieux à une utilisation sur les Windows Forms.  
  
## <a name="see-also"></a>Voir aussi

[Programmation à l’aide de composants](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
[Procédures pas à pas relatives à la programmation de composants](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)  
[Boîte à outils](../../ide/reference/toolbox.md)