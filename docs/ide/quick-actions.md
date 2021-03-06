---
title: Actions rapides | Microsoft Docs
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload: multiple
ms.openlocfilehash: 259e033aa32caaca59f37d7dc77ac095b4709878
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="quick-actions"></a>Actions rapides

Les actions rapides vous permettent de refactoriser, générer ou modifier facilement le code en une seule action. Les actions rapides sont disponibles pour les fichiers C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) et Visual Basic. Certaines actions sont spécifiques à un langage, d’autres s’appliquent à tous les langages.

Les actions rapides peuvent être appliquées en utilisant l’icône d’ampoule ![Petite icône en forme d’ampoule](media/vs2015_lightbulbsmall.png) ou en appuyant sur **Ctrl**+**.** quand votre curseur se trouve sur la ligne de code appropriée. Une ampoule apparaît si votre code est souligné d’une ligne ondulée rouge et qu’une suggestion pour résoudre le problème est disponible dans Visual Studio. Par exemple, si une erreur est signalée par un soulignement rouge ondulé, une ampoule apparaît lorsque des corrections sont disponibles pour cette erreur.

Des éditeurs tiers peuvent fournir des diagnostics et des suggestions personnalisés pour n'importe quel langage, par exemple dans le cadre d'un SDK. Dans ce cas, les ampoules Visual Studio s'allument en fonction des règles établies.

## <a name="to-see-a-light-bulb"></a>Pour afficher une ampoule

1. Dans de nombreux cas, les ampoules apparaissent spontanément lorsque vous passez la souris au niveau de l’erreur ou dans la marge gauche de l’éditeur lorsque vous déplacez le point d’insertion dans une ligne qui contient une erreur. Si vous remarquez une ligne ondulée rouge, vous pouvez pointer dessus avec la souris pour afficher l'ampoule. Vous pouvez aussi déclencher l'apparition d'une ampoule quand vous utilisez la souris ou le clavier pour vous rendre quelque part sur la ligne où le problème se produit.

1. Appuyez sur **Ctrl**+**.** sur une ligne pour appeler l’ampoule et accéder directement à la liste des corrections éventuelles.

   ![Ampoule avec pointage de la souris](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")

## <a name="to-see-potential-fixes"></a>Pour afficher les corrections éventuelles

Cliquez sur la flèche bas ou sur le lien Afficher les corrections éventuelles pour afficher une liste d'actions rapides que l'ampoule peut effectuer pour vous.

![Ampoule développée](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="see-also"></a>Voir aussi

[Génération de code dans Visual Studio](../ide/code-generation-in-visual-studio.md)  
[Actions rapides courantes](../ide/common-quick-actions.md)  
[Styles de code et actions rapides](../ide/code-styles-and-quick-actions.md)  
[Écriture et refactorisation du code (C++)](/cpp/ide/writing-and-refactoring-code-cpp)