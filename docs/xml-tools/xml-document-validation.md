---
title: Validation de documents XML | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c4be3c2f5428b7b2c246c1649a73ae8584ffe28e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xml-document-validation"></a>Validation de documents XML
L’éditeur XML vérifie la syntaxe XML 1.0 et effectue une validation des données en cours de frappe. L'éditeur peut effectuer cette validation à l'aide d'une définition de type de document (DTD) ou d'un schéma. Des soulignements ondulés rouges marquent les erreurs XML 1.0 correctement construites. Des soulignements ondulés bleus marquent les erreurs sémantiques d'après la validation de la DTD ou du schéma. La liste d'erreurs comporte une entrée pour chaque erreur détectée. Vous pouvez également afficher le message d'erreur en plaçant le curseur sur la ligne ondulée.  
  
 Les schémas utilisés pour la validation sont recherchés en fonction de la comparaison du `targetNamespace` d'un schéma compilé à la déclaration xmlns de l'élément. Les schémas compilés sont chargés à partir d'un des emplacements suivants, répertoriés par ordre de priorité :  
  
-   Nom de fichier spécifié dans le **schémas** champ de la fenêtre de propriétés de document.  
  
-   Une DTD ou un schéma inline  
  
-   Une DTD externe ou un attribut `xsd:schemaLocation` et `xsd:noNamespaceSchemaLocation`  
  
-   Un URI d'espace de noms de schéma XDR « x-schema »  
  
Des schémas peuvent également être recherchés dans les emplacements supplémentaires suivants lorsque le schéma contient un espace de noms cible non vide :  
  
-   Une autre fenêtre d'éditeur qui contient le schéma  
  
-   Un schéma contenu dans la solution actuelle  
  
-   Un schéma du répertoire de cache de schéma  
  
## <a name="xslt-files"></a>Fichiers XSLT  
 Lorsque vous modifiez un fichier XSLT, le fichier xslt.xsd situé du cache de schéma est utilisé pour la validation. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. Les erreurs provenant du compilateur XSLT sont signalées par des soulignements ondulés rouges.  
  
## <a name="xml-schema-xsd-files"></a>Fichiers XSD (XML schema definition)  
 Lorsque vous modifiez un fichier de schéma XML, le fichier xsdschema.xsd situé dans le cache de schéma est utilisé pour la validation. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. Les erreurs de compilation sont signalées de la même façon.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur XML](../xml-tools/xml-editor.md)