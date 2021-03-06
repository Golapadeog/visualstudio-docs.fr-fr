---
title: "Procédure pas à pas : création d’une application simple avec C# ou Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 10/03/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: b33816e074cf63826c931bcda0978ebdb5bb8bbe
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="walkthrough-create-a-simple-application-with-c-or-visual-basic"></a>Procédure pas à pas : création d'une application simple avec C# ou Visual Basic
Avec cette procédure pas à pas, vous allez vous familiariser avec la plupart des outils, boîtes de dialogue et concepteurs que vous pouvez utiliser quand vous développez des applications avec Visual Studio. Vous allez créer une application simple « Hello, World », concevoir l’interface utilisateur, ajouter du code et déboguer des erreurs, tout en découvrant l’utilisation de l’environnement de développement intégré (IDE).
  
##  <a name="BKMK_ConfigureIDE"></a> Configurer l'IDE  
Quand vous démarrez Visual Studio pour la première fois, vous êtes invité à vous connecter. Cette étape est facultative pour cette procédure pas à pas. Ensuite, vous pouvez voir s’afficher une boîte de dialogue qui vous invite à choisir vos paramètres de développement et le thème de couleur. Conservez les valeurs par défaut et choisissez **Démarrer Visual Studio**.  

![Boîte de dialogue Choisir les paramètres](../ide/media/exploreide-settings.png "exploreide-settings")
  
Après le démarrage de Visual Studio, vous voyez les fenêtres Outil, les menus, les barres d’outils et l’espace de la fenêtre principale. Les fenêtres Outil sont ancrées sur les côtés gauche et droit de la fenêtre d'application. **Lancement rapide**, la barre de menus et la barre d'outils standard sont situés en haut. La **page de démarrage**est située au centre de la fenêtre d'application. Lorsque vous chargez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans l'espace où se trouve la **Page de démarrage** . Quand vous développez une application, vous passez la majeure partie de votre temps dans cette zone centrale.  
  
![IDE avec les paramètres généraux appliqués](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE-IDEwithgeneralsettings")  
  
##  <a name="BKMK_CreateApp"></a> Créer une application simple  
  
### <a name="create-the-project"></a>Créer le projet  
Lorsque vous créez une application dans Visual Studio, vous créez d'abord un projet et une solution. Pour cet exemple, vous allez créer un projet WPF (Windows Presentation Foundation).  
  
#### <a name="to-create-the-wpf-project"></a>Pour créer le projet WPF  
  
1.  Créer un nouveau projet. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     ![Dans la barre de menus, choisissez Fichier, Nouveau, Projet](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")  
  
2.  Choisissez le modèle Application WPF Visual Basic ou Application WPF Visual C# en choisissant, dans le volet gauche, **Installé**, **Visual C#**, **Bureau classique Windows**, par exemple, puis en choisissant **Application WPF (.NET Framework)** dans le volet central.  Nommez le projet HelloWPFApp en bas de la boîte de dialogue Nouveau projet.  
  
     ![Créer un projet WPF C#, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE-NewProjectcsharp")  
  
Visual Studio crée la solution et le projet HelloWPFApp, et affiche les différents fichiers dans **l’Explorateur de solutions**. Le Concepteur WPF affiche un mode Design et une vue XAML pour MainWindow.xaml en mode Fractionné. Vous pouvez faire glisser le séparateur pour afficher une partie plus ou moins grande de chacune des vues.  Vous pouvez choisir d'afficher uniquement le mode visuel ou uniquement le mode XAML. (Pour plus d’informations, consultez [Concepteur WPF pour les développeurs Windows Forms](http://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca).) Les éléments suivants apparaissent dans l' **Explorateur de solutions**:  
  
![Explorateur de solutions avec les fichiers HelloWPFApp chargés](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE-HelloWPFAppFiles")  
  
Après avoir créé le projet, vous pouvez le personnaliser. Dans la fenêtre **Propriétés** (disponible dans le menu **Affichage** ), vous pouvez afficher et modifier les options des éléments du projet, des contrôles et des autres éléments d'une application.  
  
#### <a name="to-change-the-name-of-mainwindowxaml"></a>Pour modifier le nom de MainWindow.xaml  
Donnons un nom plus spécifique à MainWindow.  

1. Dans l' **Explorateur de solutions**, sélectionnez MainWindow.xaml. Vous devez normalement voir la fenêtre **Propriétés**. Si ce n’est pas le cas, choisissez le menu **Affichage**, puis l’élément **Fenêtre Propriétés**.  
2. Remplacez la propriété **Nom de fichier** par `Greetings.xaml`.  
  
     ![Fenêtre Propriétés avec Nom de fichier en surbrillance](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE-FilenameinPropertiesWindow")  
  
     Dans **l’Explorateur de solutions**, le nom du fichier est maintenant Greetings.xaml et le nom du fichier de code imbriqué est maintenant Greetings.xaml.vb ou Greetings.xaml.cs. Ce fichier de code est imbriqué sous le nœud de fichier .xaml pour montrer que les deux fichiers sont étroitement liés.  
  
### <a name="design-the-user-interface-ui"></a>Créer l'interface utilisateur  
Nous allons ajouter trois types de contrôles à cette application : un contrôle TextBlock, deux contrôles RadioButton et un contrôle Button.  
  
#### <a name="to-add-a-textblock-control"></a>Pour ajouter un contrôle TextBlock  
  
1.  Ouvrez la fenêtre **Boîte à outils** en choisissant le menu **Affichage** , puis l'élément **Boîte à outils** .  
  
2.  Dans la fenêtre **Boîte à outils**, développez le nœud **Contrôles WPF communs** pour afficher le contrôle TextBlock.  
  
     ![Boîte à outils avec le contrôle TextBlock en surbrillance](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE-TextBlockToolbox")  
  
3.  Ajoutez un contrôle TextBlock à l’aire de conception en choisissant l’élément **TextBlock** et en le faisant glisser vers la fenêtre de l’aire de conception. Centrez le contrôle vers le haut de la fenêtre.  
  
Votre fenêtre doit ressembler à l'illustration suivante :  
  
![Contrôle TextBlock sur le formulaire Greetings](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE-GreetingswithTextblockonly")  
  
Le balisage XAML doit ressembler à ce qui suit :  
  
```xaml  
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>  
```  

#### <a name="to-customize-the-text-in-the-text-block"></a>Pour personnaliser le texte du bloc de texte  
  
1.  Dans la vue XAML, localisez la balise de TextBlock, puis remplacez l'attribut Text :  

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```  
  
2.  Recentrez l’élément TextBlock si nécessaire, puis enregistrez vos modifications en appuyant sur **Ctrl+S** ou en utilisant l’élément de menu **Fichier**.  
  
Vous ajouterez ensuite deux contrôles [RadioButton](/dotnet/framework/wpf/controls/radiobutton) au formulaire.  
  
#### <a name="to-add-radio-buttons"></a>Pour ajouter des cases d'option  
  
1.  Dans la fenêtre **Boîte à outils**, recherchez le contrôle **RadioButton**.  
  
     ![Fenêtre Boîte à outils avec le contrôle RadioButton sélectionné](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE-RadioButtonToolbox")  
  
2.  Ajoutez deux contrôles RadioButton à l’aire de conception en choisissant l’élément **RadioButton** et en le faisant glisser vers la fenêtre de l’aire de conception. Déplacez les boutons (en les sélectionnant et en utilisant les flèches) pour les placer côte à côte sous le contrôle TextBlock.  
  
     Votre fenêtre doit se présenter comme suit :  
  
     ![Formulaire Greetings avec un bloc de texte et deux cases d’option](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE-Greetingswithradiobuttons")  
  
3.  Dans la fenêtre **Propriétés** du contrôle RadioButton de gauche, affectez à la propriété **Nom** (propriété en haut de la fenêtre **Propriétés**) la valeur **HelloButton**.  

     ![Fenêtre Propriétés de RadioButton](../ide/media/exploreide-buttonproperties.png "exploreide-buttonproperties")  
  
4.  Dans la fenêtre **Propriétés** du contrôle RadioButton de droite, remplacez la valeur de la propriété **Name** par **GoodbyeButton**, puis enregistrez les modifications.  
  
Vous pouvez maintenant afficher du texte pour chaque contrôle RadioButton. La procédure suivante met à jour la propriété **Contenu** d'un contrôle RadioButton.  
  
#### <a name="to-add-display-text-for-each-radio-button"></a>Pour ajouter un texte à afficher pour chaque case d'option  
  
1.  Sur l’aire de conception, ouvrez le menu contextuel du contrôle HelloButton en cliquant avec le bouton droit sur HelloButton, choisissez **Modifier le texte**, puis entrez « Hello ».  
  
2.  Ouvrez le menu contextuel du contrôle GoodbyeButton en cliquant avec le bouton droit sur GoodbyeButton, choisissez **Modifier le texte**, puis entrez « Goodbye ».  

### <a name="to-set-a-radio-button-to-be-checked-by-default"></a>Pour définir une case d’option activée par défaut  
Dans cette étape, nous allons définir la case d’option HelloButton pour qu’elle soit activée par défaut. Ainsi, il y a toujours une des deux cases d’option qui est activée.  

Dans l’affichage XAML, recherchez la balise du contrôle HelloButton et ajoutez un attribut **IsChecked** :

```xaml
IsChecked="True"
```  

Le dernier élément de l’interface utilisateur que vous ajouterez est un contrôle [Button](/dotnet/framework/wpf/controls/button).  
  
#### <a name="to-add-the-button-control"></a>Pour ajouter le contrôle bouton  
  
1.  Dans la fenêtre **Boîte à outils**, recherchez le contrôle **Button**, puis ajoutez-le à l’aire de conception sous les contrôles RadioButton en le faisant glisser vers le formulaire en mode Design.  
  
2.  Dans l’affichage XAML, changez la valeur de l’élément **Content** du contrôle Button de `Content="Button"` en `Content="Display"`, puis enregistrez les modifications.  
  
     La balise doit ressembler à l'exemple suivant :  
     `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`  
  
     Votre fenêtre doit ressembler à l'illustration suivante.  
  
     ![Formulaire Greetings avec des étiquettes de contrôle](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE-Greetingswithconrollabels")  
  
### <a name="add-code-to-the-display-button"></a>Ajouter du code au bouton d'affichage  
Quand cette application s’exécute, un message s’affiche si un utilisateur choisit une case d’option et choisit ensuite le bouton **Afficher**. Un message s'affiche pour Hello et un autre pour Goodbye. Pour créer ce comportement, vous ajouterez du code à l’événement Button_Click dans Greetings.xaml.vb ou Greetings.xaml.cs.  
  
#### <a name="add-code-to-display-message-boxes"></a>Ajoutez le code pour afficher des boîtes de message    
1.  Dans l'aire de conception, double-cliquez sur le bouton **Afficher** .  
  
     Greetings.xaml.vb ou Greetings.xaml.cs s'ouvre, avec le curseur dans l'événement Button_Click. 
  
    ```vb  
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)  
  
    End Sub  
    ```    
    ```csharp  
    private void Button_Click_1(object sender, RoutedEventArgs e)  
    {  
  
    }  
    ```  
  
2.  Entrez le code suivant :  
  
    ```vb  
    If HelloButton.IsChecked = True Then  
        MessageBox.Show("Hello.")  
    ElseIf GoodbyeButton.IsChecked = True Then 
        MessageBox.Show("Goodbye.")  
    End If  
  
    ```    
    ```csharp  
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```  
  
3.  Enregistrez l'application.  
  
##  <a name="BKMK_DebugTest"></a> Déboguer et tester l'application  
Vous déboguerez ensuite l’application pour rechercher les erreurs et tester l’affichage correct des deux boîtes de message. Les instructions suivantes expliquent comment générer et lancer le débogueur. Pour plus d’informations, vous pourrez ultérieurement consulter [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) et [Debugging WPF](../debugger/debugging-wpf.md) .  
  
### <a name="find-and-fix-errors"></a>Rechercher et corriger des erreurs  
Dans cette étape, vous allez rechercher l’erreur que nous avons provoquée précédemment en changeant le nom du fichier MainWindow.xaml.  
  
#### <a name="to-start-debugging-and-find-the-error"></a>Pour démarrer le débogage et rechercher l'erreur  
  
1.  Démarrez le débogueur en sélectionnant **Déboguer**, puis **Démarrer le débogage**.  
  
     ![Commande Démarrer le débogage du menu Débogage](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")  
  
     Une fenêtre **Mode arrêt** s’affiche. La fenêtre **Sortie** indique qu’une exception IOException s’est produite : Impossible de trouver la ressource « mainwindow.xaml ».  
  
2.  Arrêtez le débogueur en choisissant **Déboguer**, **Arrêter le débogage**.  
  
     ![Commande Arrêter le débogage du menu Débogage](../ide/media/exploreide-stopdebugging.png "ExploreIDE-StopDebugging")  
  
Nous avons renommé MainWindow.xaml en Greetings.xaml au début de cette procédure, mais le code continue de faire référence à mainwindow.xaml comme URI de démarrage de l’application. Cela explique pourquoi le projet ne démarre pas.  
  
#### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Pour spécifier Greetings.xaml comme l'URI de démarrage  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le fichier App.xaml (dans le projet C#) ou le fichier Application.xaml (dans le projet Visual Basic).  
  
2.  Remplacez `StartupUri="MainWindow.xaml"` par `StartupUri="Greetings.xaml"`, puis enregistrez les modifications.  
  
Redémarrez le débogueur (appuyez sur **F5**). Vous devez voir la fenêtre Greetings de l'application. Maintenant, fermez la fenêtre d’application pour arrêter le débogage.  
  
### <a name="to-debug-with-breakpoints"></a>Pour déboguer avec des points d'arrêt  
Vous pouvez tester le code pendant le débogage en ajoutant des points d’arrêt. Vous pouvez ajouter des points d’arrêt en choisissant **Déboguer**, **Basculer le point d’arrêt**, en cliquant dans la marge gauche de l’éditeur à côté de la ligne de code où mettre le point d’arrêt, ou en appuyant sur **F9**.  
  
#### <a name="to-add-breakpoints"></a>Pour ajouter des points d'arrêt  
  
1.  Ouvrez Greetings.xaml.vb ou Greetings.xaml.cs, puis sélectionnez la ligne suivante : `MessageBox.Show("Hello.")`  
  
2.  Ajoutez un point d'arrêt à partir du menu en sélectionnant **Déboguer**, puis **Basculer le point d'arrêt**.  
  
     ![Commande Basculer le point d’arrêt du menu Débogage](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint")  
  
     Un cercle rouge apparaît à côté de la ligne de code dans la bordure gauche de la fenêtre de l’éditeur.  
  
3.  Sélectionnez la ligne suivante : `MessageBox.Show("Goodbye.")`.  
  
4.  Appuyez sur la touche **F9** pour ajouter un point d’arrêt, puis sur la touche **F5** pour démarrer le débogage.  
  
5.  Dans la fenêtre **Greetings** , choisissez la case d'option **Hello** , puis le bouton **Afficher** .  
  
     La ligne `MessageBox.Show("Hello.")` est mise en surbrillance en jaune. Dans la partie inférieure de l'IDE, les fenêtres Automatique, Variables locales et Espion sont ancrées ensemble sur le côté gauche. Les fenêtres Pile des appels, Points d'arrêt, Commande, Immédiat et Sortie sont ancrées ensemble sur le côté droit.  
  
6.  Dans la barre de menus, choisissez **Déboguer**, **Pas à pas sortant**.  
  
     L’application reprend l’exécution et une boîte de message affiche le mot « Hello ».  
  
7.  Choisissez le bouton **OK** dans la boîte de message pour la fermer.  
  
8.  Dans la fenêtre **Greetings** , choisissez la case d'option **Goodbye** , puis le bouton **Afficher** .  
  
     La ligne `MessageBox.Show("Goodbye.")` est mise en surbrillance en jaune.  
  
9. Appuyez sur la touche **F5** pour continuer le débogage. Lorsque la boîte de message s'affiche, choisissez le bouton **OK** sur la boîte de message pour la fermer.  
  
10. Fermez la fenêtre d’application pour arrêter le débogage.  
  
11. Dans la barre de menus, choisissez **Débogage**, **Désactiver tous les points d'arrêt**.  
  
### <a name="build-a-release-version-of-the-application"></a>Générer une version Release de l'application  
 Maintenant que vous avez vérifié que tout fonctionne, vous pouvez préparer une version Release de l’application.  
  
#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Pour nettoyer les fichiers solution et générer une version Release  
  
1.  Dans le menu principal, sélectionnez **Générer**, **Nettoyer la solution** pour supprimer les fichiers intermédiaires et les fichiers de sortie créés pendant les générations précédentes. Cette opération n'est pas nécessaire, mais elle nettoie les sorties des versions Debug.  
  
     ![Commande Nettoyer la solution du menu Générer](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")  
  
2.  Remplacez la configuration de build **Debug** pour HelloWPFApp par **Release** à l’aide du contrôle de liste déroulante de la barre d’outils (« Debug » est actuellement affiché).  
  
     ![Barre d’outils Standard avec Version finale sélectionné](../ide/media/exploreide-releaseversion.png "ExploreIDE-ReleaseVersion")  
  
3.  Générez la solution en choisissant **Générer**, puis **Générer la solution**.  
  
     ![Commande Générer la solution du menu Générer](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
Félicitations ! Vous avez terminé cette procédure. Le fichier .exe que vous avez généré se trouve sous le répertoire de votre solution et de votre projet (...\HelloWPFApp\HelloWPFApp\bin\Release\\). Pour explorer d’autres exemples, consultez [Visual Studio Samples](../ide/visual-studio-samples.md).  
  
## <a name="see-also"></a>Voir aussi
[Nouveautés de Visual Studio 2017](../ide/whats-new-in-visual-studio.md)   
[Bien démarrer avec le développement dans Visual Studio](../ide/get-started-developing-with-visual-studio.md)   
[Conseils de productivité](../ide/productivity-tips-for-visual-studio.md)