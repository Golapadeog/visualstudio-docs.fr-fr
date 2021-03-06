---
title: "Options, Éditeur de texte, Tous les langages | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.General
- VS.ToolsOptionsPages.Text_Editor.ResJSON.General
- vs.toolsoptionspages.text_editor.all_languages.scrollbars
helpviewer_keywords:
- Text Editor Options dialog box
- statement completion
- word wrap
- General dialog box
- line numbers
- virtual space
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3ef5133f1d92d9f18a62117e40a0788766dfe439
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="options-text-editor-all-languages"></a>Options, Éditeur de texte, Tous les langages
Cette boîte de dialogue vous permet de modifier le comportement par défaut de l’éditeur de code. Ces paramètres s’appliquent également à d’autres éditeurs basés sur l’éditeur de code, tels que le mode Source du concepteur HTML. Pour ouvrir cette boîte de dialogue, sélectionnez **Options** dans le menu **Outils**. Dans le dossier **Éditeur de texte**, développez le sous-dossier **Tous les langages**, puis choisissez **Général**.  
  
> [!CAUTION]
>  Cette page définit les options par défaut pour tous les langages de développement. N’oubliez pas que la réinitialisation d’une option dans cette boîte de dialogue entraîne la réinitialisation des options générales dans tous les langages quels que soient les choix effectués. Pour modifier les options de l’éditeur de texte pour un seul langage, développez le sous-dossier de ce langage et sélectionnez ses pages d’options.  
  
 Une coche grisée s’affiche quand une option a été sélectionnée dans les pages d’options générales pour certains langages de programmation mais pas pour d’autres.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="statement-completion"></a>Compléter automatiquement les instructions  
 Répertorier automatiquement les membres  
 Lorsque cette option est sélectionnée, les listes contextuelles des membres disponibles, les propriétés, les valeurs ou les méthodes sont affichées par IntelliSense lorsque vous tapez dans l’éditeur. Choisissez un élément dans la liste contextuelle pour l’insérer dans votre code. La sélection de cette option active l’option **Masquer les membres avancés**.  
  
 Masquer les membres avancés  
 Lorsque cette option est activée, les listes de saisie semi-automatique d’instructions contextuelles se limitent à l’affichage des éléments les plus couramment utilisés. Les autres éléments sont filtrés dans la liste.  
  
 Information sur les paramètres  
 Lorsque cette option est sélectionnée, la syntaxe complète de la procédure ou déclaration actuelle s’affiche sous le point d’insertion dans l’éditeur, avec tous ses paramètres disponibles. Le paramètre suivant que vous pouvez assigner est affiché en gras.  
  
## <a name="settings"></a>Paramètres  
 Activer l'espace virtuel  
 Lorsque cette option est sélectionnée et que l’option **Retour automatique à la ligne** est désactivée, vous pouvez cliquer hors de la limite d’une ligne de l’éditeur de code et saisir du texte. Cette fonctionnalité peut être utilisée pour placer des commentaires à un point précis en regard de votre code.  
  
 Retour automatique à la ligne  
 Lorsque cette option est sélectionnée, toute partie d’une ligne qui dépasse horizontalement de la zone affichable de l’éditeur est automatiquement affichée à la ligne suivante. La sélection de cette option active l’option **Afficher des glyphes visuels pour le retour automatique à la ligne**.  
  
> [!NOTE]
>  La fonctionnalité **Espace virtuel** est désactivée quand l’option **Retour automatique à la ligne** est activée.  
  
 Afficher des glyphes visuels pour le retour automatique à la ligne  
 Lorsque cette option est sélectionnée, un indicateur fléché de retour s’affiche à l’endroit où une ligne longue est automatiquement renvoyée à une deuxième ligne.  
  
 ![Capture d’écran LineBreakSymbol](../../ide/reference/media/linebreak.gif "linebreak")  
  
 Désactivez cette option si vous préférez ne pas afficher ces indicateurs.  
  
> [!NOTE]
>  Ces flèches de rappel ne sont pas ajoutées à votre code et ne sont pas imprimées. Elles ne sont utilisées qu'à titre de référence.  
  
 Appliquer les commandes Couper ou Copier aux lignes vides en l'absence de sélection  
 Cette option définit le comportement de l’éditeur lorsque vous placez le point d’insertion sur une ligne vide, ne sélectionnez rien, puis effectuez une action Copier ou Couper.  
  
-   Lorsque cette option est sélectionnée, la ligne vide est copiée ou coupée. Si vous effectuez ensuite une action Coller, une nouvelle ligne vide est insérée.  
  
-   Lorsque cette option est désactivée, la commande Couper supprime les lignes vides. Toutefois, les données figurant dans le Presse-papiers sont conservées. Par conséquent, si vous utilisez ensuite la commande Coller, le contenu le plus récemment copié dans le Presse-papiers est collé. Si vous n'avez rien copié auparavant, rien n'est collé.  
  
Ce paramètre n’a aucun effet sur les actions Copier ni Couper lorsqu’une ligne n’est pas vide. Si rien n'est sélectionné, toute la ligne est copiée ou coupée. Si vous effectuez ensuite une action Coller, le texte de la ligne toute entière et son caractère de ligne de fin sont collés.  
  
> [!TIP]
>  Pour afficher les indicateurs d’espaces, de tabulations et de fins de ligne et distinguer ainsi les lignes en retrait de celles qui sont complètement vides, sélectionnez **Avancé** dans le menu **Edition**, puis choisissez **Afficher les espaces blancs**.  
  
## <a name="display"></a>Afficher  
 Numéros de ligne  
 Lorsque cette option est sélectionnée, un numéro de ligne apparaît en regard de chaque ligne de code.  
  
> [!NOTE]
>  Ces numéros de lignes ne sont pas ajoutés à votre code et ne sont pas imprimés. Elles ne sont utilisées qu'à titre de référence.  
  
 Activer la navigation dans les URL par simple clic  
 Lorsque cette option est sélectionnée, le curseur de souris prend la forme d’une main avec un doigt pointé lorsqu’il passe sur une URL dans l’éditeur. Vous pouvez cliquer sur l'URL pour afficher la page indiquée dans votre navigateur Web.  
  
 Barre de navigation  
 Lorsque cette option est sélectionnée, la **barre de navigation** est affichée en haut de l’éditeur de code. Ses listes déroulantes **Objets** et **Membres** vous permettent de choisir un objet particulier dans votre code, de sélectionner parmi ses membres et d’accéder à la déclaration du membre sélectionné dans l’éditeur de code.  
  
## <a name="see-also"></a>Voir aussi  
 [Options, Éditeur de texte, Tous les langages, Onglets](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)   
 [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)