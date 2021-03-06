---
title: Concepts de base de Windows Installer | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1a9f895db0d202dd573e7c665b1185f6e3f4b751
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-installer-basics"></a>Concepts de base de Windows Installer
Le programme d’installation de Windows installe et désinstalle des applications ou des logiciels sur l’ordinateur d’un utilisateur, effectuer ces tâches dans des unités appelées des composants de Windows Installer (parfois appelés WICs ou simplement des composants). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le décompte de références pour les installations à l’aide de Windows Installer.  
  
 Pour une documentation complète sur le programme d’installation de Windows, consultez la rubrique de développement Platform SDK, [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Création d’un VSPackage  
 Programme d’installation de Windows utilise des packages d’installation, qui contiennent des informations Windows Installer a besoin pour installer, désinstaller ou réparer un produit et exécuter l’interface utilisateur de configuration (IU). Chaque package d’installation inclut un fichier .msi, qui contient une base de données de l’installation, un flux d’informations de résumé et flux de données pour les différentes parties de l’installation. Pour utiliser le programme d’installation, vous devez créer une installation. Étant donné que le programme d’installation organise les installations autour du concept de composants et stocke des informations sur l’installation dans une base de données relationnelle, le processus de la création d’un package d’installation largement implique les étapes suivantes :  
  
1.  Planifier votre installation de création pour prendre en charge de votre contrôle de version et les stratégies de côte-à-côte.  
  
2.  Identifier les fonctionnalités à présenter aux utilisateurs.  
  
3.  Organiser le VSPackage et les dépendances de composants.  
  
4.  Remplir la base de données de l’installation avec les informations.  
  
5.  Valider le package d’installation.  
  
 Cette documentation concerne principalement les premier et troisième étapes du processus. Au cours de ces étapes vous organisez vos fonctionnalités VSPackage en WICs donc vous pouvez le cadre de votre contrôle de version et la maintenance de stratégie pour prendre en compte pour les versions ultérieures de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Les trois étapes restantes sont traitées en détail dans la documentation de Windows Installer dans le Kit de développement de plate-forme.  
  
## <a name="key-terms"></a>Termes clés  
 Voici les définitions des termes clés liés à la technologie Windows Installer.  
  
 Ressource  
 Fichiers, des clés de Registre, des raccourcis, ou, et ainsi de suite qui peuvent être installés sur un ordinateur. Ces ressources sont regroupées logiquement dans des composants de Windows Installer.  
  
 Composant de programme d’installation de Windows (WIC)  
 Unité de base d’installation qui représente un regroupement logique des ressources connexes qui sont installés et désinstallés en tant qu’unité. Composants de Windows Installer sont identifiés par un ID de composant unique ou GUID. En outre, Windows Installer conserve son niveau WIC de comptage de références. Pour une flexibilité maximale de contrôle de version, incluez pas plus d’une ressource principale, comme une DLL, dans un WIC donné. Notez qu’après avoir identifié et remplir un WIC, lui donner un GUID et le déployer, vous ne pouvez pas modifier sa composition. Pour plus d’informations, consultez [organiser des Applications en composants](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Package (package redistribuable)  
 Une unité de déploiement qui se compose d’un fichier .msi et des fichiers de la source externe auquel ce fichier peut pointer. Un package contient toutes les informations de Windows Installer a besoin pour exécuter l’interface utilisateur et à installer ou désinstaller l’application.  
  
 fichier .msi  
 Un fichier de stockage structuré COM qui contient les instructions et les données requises pour installer une application. Chaque package contient au moins un fichier .msi. Le fichier .msi contient la base de données du programme d’installation, un flux d’informations résumées et éventuellement une ou plusieurs transformations et des fichiers source internes. Installation de fichiers peuvent être compressés dans un fichier CAB et stockées dans un flux de données dans le fichier .msi ou stockées, compressés ou non compressés, en dehors du fichier .msi sur le support source. Pour plus d’informations, consultez [Extensions de fichier du programme d’installation Windows](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Mise en œuvre de règles Windows Installer  
 Deux ensembles de règles déterminent le déploiement de ressources via les composants de votre installation. Un ensemble de règles est géré par le programme d’installation de Windows, alors que vous devez appliquer le second ensemble en tant qu’auteur de l’installation.  
  
> [!NOTE]
>  L’application de règles Windows Installer se produit uniquement si vous exécutez une validation de votre fichier .msi. Néanmoins, vous sont indispensable pour traiter ces règles comme meilleures pratiques. Pour plus d’informations, consultez [validation d’une base de données de l’Installation](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) et [la Validation du Package](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Règles appliquées au programme d’installation  
  
-   Tous les fichiers dans un composant donné doivent être installés dans le même répertoire. À l’inverse, les fichiers installés pour séparer les dossiers doivent appartenir pour séparer les composants.  
  
-   Il peut y avoir qu’un seul chemin de la clé par le composant. Le chemin de clé est simplement une fichier de clé de Registre ou qui représente le composant entier.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilités du fournisseur de composant  
  
-   Les deux ressources qui peut être fourni séparément dans les versions ultérieures doivent exister dans différents composants. Ressources doivent être regroupées dans le même composant uniquement lorsque vous êtes certain que ces ressources ne seront jamais distribué séparément. En fait, il est recommandé que toutes les ressources principales (DLL, par exemple) existent toujours dans WICs distincts. Pour plus d’informations, consultez [définition des composants de programme d’installation](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Aucune ressource de version ne doit expédier jamais dans plusieurs WIC.  
  
## <a name="see-also"></a>Voir aussi  
 [Que se passe-t-il si les règles de composant sont interrompues ?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)