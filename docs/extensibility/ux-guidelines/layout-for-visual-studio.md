---
title: Mise en page pour Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ef3c590a82fc3a7b89d21684ffe2e4b0f216ca98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="layout-for-visual-studio"></a>Mise en page pour Visual Studio
La majorité des boîtes de dialogue Visual Studio sont [mise en page de la boîte de dialogue utilitaire](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), qui sont l’unthemed boîtes de dialogue standard suivez [principes de mise en page de boîte de dialogue Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx). Lorsque Visual Studio s’à actualiser son interface utilisateur, certaines des boîtes de dialogue plus apparents ont une nouvelle conception qui établit les expériences de comme définition de produit. Ces [mise en page de boîte de dialogue à thème](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) ont une apparence à thème.  
  
##  <a name="BKMK_UtilityDialogLayout"></a>Mise en page de boîte de dialogue utilitaire  
  
-   Tous les contrôles dans une boîte de dialogue Utilitaire doivent démarrer à l’angle supérieur gauche et vers le bas de flux.  
  
-   Center jamais des contrôles sur une boîte de dialogue pour remplir une zone importante.  
  
-   Utilisez la police d’environnement pour tout texte de la boîte de dialogue. Lorsque vous écrivez une spécification visual, spécifiez la police d’environnement au lieu de sélectionner une police particulière et une taille. Consultez [la police d’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Utilisation de l’espacement contrôle cohérent et la sélection élective pour prendre en charge l’objectif de qualité de savoir-faire.  
  
-   Les boîtes de dialogue peuvent devenir plus complexes à partir d’un plus grand nombre de contrôles, une juxtaposition unique des contrôles ou les deux. Dans ce cas complex, permettre suffisamment d’espace entre les regroupements de contrôle pour permettre à l’utilisateur un flux logique d’analyse.  
  
### <a name="utility-dialog-layout-examples"></a>Exemples de mise en page de boîte de dialogue utilitaire  
 Toutes les dimensions sont exprimées en pixels.  
  
 ![Espacement de boîte de dialogue pour les étiquettes au-dessus des contrôles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "a_UtilitySpacingAbove-0801")  
  
 **Figure 08.01-a : Espacement des recommandations pour les boîtes de dialogue utilitaire avec des étiquettes au-dessus des contrôles**  
  
 ![Espacement de boîte de dialogue pour les étiquettes à gauche des contrôles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "b_UtilitySpacingLeft-0801")  
  
 **Figure 08.01-b : Espacement des recommandations pour les boîtes de dialogue utilitaire avec des étiquettes à gauche des contrôles**  
  
### <a name="layout-details"></a>Détails de la mise en page  
  
#### <a name="margins"></a>Marges  
  
-   Toutes les boîtes de dialogue doivent avoir une bordure de 12 pixels autour de tous les bords.  
  
-   Les marges dans un intervalle de groupe doivent être 9 pixels du bord de l’image.  
  
-   Les marges d’un contrôle onglet doivent être 6 pixels du bord du contrôle onglet.  
  
#### <a name="command-buttons"></a>Boutons de commande  
  
-   Boutons de commande fonctionnent dans le cadre de la boîte de dialogue, pas sur le contenu. Ils doivent être placés dans la partie inférieure droite et doivent avoir suffisamment d’espace variable ci-dessus pour définir les boutons clairement séparés.  
  
-   S’il existe des boutons horizontales qui opèrent dans la boîte de dialogue, la configuration de bouton de commande alternatif est une pile verticale en haut à droite. Consultez [boutons de commande intérieurs](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) ci-dessous.  
  
-   L’espace à gauche des boutons de commande (gauche/centre en bas de la boîte de dialogue) est considéré comme partie de la « bande » des contrôles d’opération de boîte de dialogue. La seule chose qui doit empiéter sur cet espace est un lien d’aide qui s’applique à la tâche globale ou de la boîte de dialogue.  
  
-   Boutons de commande doit être de 75 x 23 pixels.  
  
-   Boutons de commande doit être 6 pixels éloignés.  
  
 ![Alignement du bouton base](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "c_ButtonAlign-0801")  
  
 **Figure 08.01-c : Alignement des boutons de base**  
  
#### <a name="labels"></a>Étiquettes  
  
-   Aligner à gauche toutes les étiquettes.  
  
-   Pour les étiquettes qui se situent au-dessus d’un contrôle, ils doivent aligner à gauche précisément avec le contrôle en dessous, et le bas de l’étiquette doit être 5 pixels au-dessus de l’autre contrôle (par exemple, une zone de liste déroulante).  
  
-   Pour les étiquettes situées à gauche des contrôles, la largeur minimale entre l’étiquette et le contrôle d’entrée est de 10 pixels. Une deuxième colonne implicite doit être établie pour aligner les zones de texte, zones de liste déroulante ou d’autres contrôles.  
  
-   Les étiquettes sont de casse de la phrase et sont suivies par un signe deux-points. Consultez [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### <a name="distance-between-controls"></a>Distance entre les contrôles  
 Contrôles de pile raisonnablement. Il n’existe aucune indication absolue pour l’espacement entre les contrôles empilées. La précision entre les contrôles peut-être varier légèrement entre les boîtes de dialogue. L’espacement recommandée est 20 pixels pour les paires de contrôle/étiquette verticale et 9 pixels pour les paires contrôle horizontal/étiquette. L’espacement minimal de contrôles pour les paires horizontales est 6 pixels.  
  
 ![Recommandé de distance entre les contrôles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "d_ControlDistance-0801")  
  
 **Figure 08.01-d: Des recommandations pour la distance entre les contrôles**  
  
#### <a name="control-indentation"></a>Mise en retrait du contrôle  
 Lorsque les contrôles sont imbriqués, aligner les contrôles internes horizontalement sur le bord gauche du contrôle ci-dessus, généralement l’étiquette.  
  
 ![Imbriqué alignement](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "e_ControlAlign-0801")  
  
 **Figure 08.01-e : Alignement des contrôles imbriqués**  
  
#### <a name="control-width"></a>Largeur du contrôle  
 La largeur d’une zone de texte ou d’autres contrôles similaires doit être pas plue de l’entrée moyenne pour le champ. La moyenne des mots anglais sont cinq caractères. Par exemple, une zone de texte qui nécessite un nom de chemin d’accès long doit être tant que la mise en page horizontale permet, tandis que d’une liste déroulante pour les noms de plateforme doivent être uniquement une longueur qui autorise l’entrée la plus longue.  
  
#### <a name="helper-text"></a>Texte d’aide  
  
-   Une boîte de dialogue peut afficher le texte d’aide qui fournit des informations supplémentaires sur l’objectif de la boîte de dialogue. En général, cela se situe en haut et peut être des phrases de 1 à 2.  
  
-   La longueur de ligne doit être une largeur à l’aise pour un utilisateur à analyser et à lire. Une boîte de dialogue moyenne doit être pas plus de 550 pixels de largeur.  
  
####  <a name="BKMK_InteriorCommandButtons"></a>Boutons de commande intérieurs  
 Les boîtes de dialogue plus complexes, un contrôle interne peut contenir ses propres boutons associés, qui peut affecter l’emplacement où se trouvent les boutons de la validation de la boîte de dialogue.  
  
-   Utilisez un alignement vertical (colonne) de l’intérieur des boutons lorsque **OK**/**Annuler** est orienté horizontalement dans le coin inférieur droit.  
  
-   Utilisez un alignement horizontal (ligne) de l’intérieur des boutons lorsque **OK**/**Annuler** sont orientés verticalement dans le coin supérieur droit. Cette situation est moins fréquent.  
  
-   Taille du bouton intérieurs doit cibler la taille des boutons standard de pixels correspondant à la taille de 75 x 23 **OK**/**Annuler** boutons lorsque cela est possible. Si une étiquette de bouton rend le bouton de dépassement de la taille du bouton standard, les autres boutons de ce groupe doivent s’aligner avec cette taille plus large.  
  
 ![Boutons OK horizontale et annuler](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "f_HorizOKCan-0801")  
  
 **Figure 08.01-f: Boutons intérieur Vertical horizontal OK/Annuler**  
  
 ![Boutons OK vertical et annuler](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "g_VertOKCan-0801")  
  
 **Figure 08.01-g: Horizontal intérieurs boutons OK/Annuler verticaux**  
  
#### <a name="browse-button"></a>[Parcourir...] bouton  
 **[Parcourir...]**  boutons qui suivent une zone de texte doit spécifier « Parcourir... » dans leur intégralité, y compris les points de suspension. Si l’espace est limité ou il existe plusieurs **[Parcourir...]**  boutons à l’écran, le bouton peut être réduit à simplement les points de suspension.  
  
##  <a name="BKMK_ThemedDialogLayout"></a>Mise en page de boîte de dialogue à thème  
 Les boîtes de dialogue à thème dans Visual Studio ont une apparence plus claire et offrent davantage d’espace blanc. Typographie fournit plus d’importance et présentant un intérêt, interligne plus ouvrir et une variante de tailles de police et le poids de l’offre. Lorsque cela est possible, les barres de titre et chrome ont été réduits ou supprimés. La disposition de ces boîtes de dialogue doit suivre ce modèle de base :  
  
1.  L’arrière-plan de la boîte de dialogue est blanc.  
  
2.  Il existe une bordure de la règle de 1 pixel dans un valeur moyenne de gris.  
  
3.  Le titre de la boîte de dialogue n’est plus se trouve dans une barre de titre, mais il fournit un intérêt visuel et une accentuation dans une taille supérieure. (Consultez la section de taille de police de [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)  
  
4.  Les étiquettes couplées avec un texte supplémentaire, telle qu’une description, doivent être **police d’environnement + gras**.  
  
5.  Colonnes intérieurs sont séparés par une règle de 1 pixel en gris clair.  
  
6.  Les liaisons par défaut n’ont aucun trait de soulignement. États pointage et appuyés ont une modification de la couleur et le trait de soulignement.  
  
7.  Valider des boutons (comme **OK**/**Annuler**) se trouvent dans le coin inférieur droit.  
  
### <a name="themed-dialog-layout-examples"></a>Exemples de mise en page de boîte de dialogue à thème  
 ![Mise en page de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "h_ThemedDialog-0801")  
  
 **Figure 08.01-h : Boîte de dialogue à thème**  
  
 ![Dimensions de la boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "i_ThemedDialogDimensions-0801")  
  
 **Figure 08.01-i Dialogue à thème - Dimensions**  
  
 ![Polices de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "j_ThemedDialogFonts-0801")  
  
 **Figure 08.01-j : Dialogue à thème - polices**  
  
 ![Couleurs de la boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "k_ThemedDialogColors-0801")  
  
 **Figure 08.01-k : Dialogue à thème - des couleurs**  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles d’application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Contrôles (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Boîtes de dialogue (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)