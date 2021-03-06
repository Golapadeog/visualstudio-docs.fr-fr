---
title: "Principes fondamentaux de la création d’applications avec Xamarin.Forms dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2018
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: 71470cd03844c7761afbd07c9d454214f5dc36ca
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Principes fondamentaux de la création d’applications avec Xamarin.Forms dans Visual Studio

Une fois que vous avez effectué les étapes dans [Setup and install](../cross-platform/setup-and-install.md) et [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md), cette procédure pas à pas vous montre comment créer une application de base (voir ci-dessous) avec Xamarin.Forms. Xamarin.Forms vous permet d’écrire tout le code de l’interface utilisateur une seule fois dans une bibliothèque de classes .NET Standard. Xamarin affiche ensuite automatiquement les contrôles de l’interface utilisateur native pour les plateformes iOS, Android et Windows universelle. Nous recommandons cette approche (plutôt qu’un projet partagé) car la bibliothèque .NET Standard inclut uniquement les API .NET prises en charge sur toutes les plateformes cibles, et parce que Xamarin.Forms vous permet de partager le code de l’interface utilisateur entre les plateformes.  
  
![Exemple d’application météo sur Android, iOS et Windows](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
Vous allez effectuer les opérations suivantes pour la générer :  
  
-   [Configurer votre solution](#solution)  
  
-   [Écrire le code de service de données partagé](#dataservice)  
  
-   [Commencer la rédaction du code de l’interface utilisateur partagé](#uicode)  
  
-   [Tester votre application avec l’émulateur Visual Studio pour Android](#test)  
  
-   [Terminer l’interface utilisateur avec une apparence native entre les plateformes](#finish)  
  
> [!TIP]
> Vous trouverez le code source complet de ce projet dans le [dépôt d’exemples Xamarin.Forms sur GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
##  <a name="solution"></a> Configurer votre solution  

Les étapes suivantes créent une solution Xamarin.Forms qui contient une bibliothèque de classes .NET Standard pour le code partagé et deux packages NuGet ajoutés.  
  
1.  Dans Visual Studio, créez une solution **Application multiplateforme (Xamarin.Forms)** et nommez-la **WeatherApp**. Recherchez le modèle en sélectionnant **Visual C#** et **Cross-Platform** dans la liste à gauche.  
  
     S’il n’y figure pas, vous devez peut-être installer Xamarin ou activer la fonctionnalité Visual Studio 2017. Consultez [Setup and install](../cross-platform/setup-and-install.md).  
  
     ![Création d’un projet d’application vide multiplateforme &#40;Xamarin.Forms&#41;](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Après avoir cliqué sur OK, vous aurez la possibilité de sélectionner des options. Choisissez **Application vide**, **Xamarin.Forms** et **.NET Standard** :

     ![Création d’un projet d’application multiplateforme](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  Après avoir cliqué sur OK pour créer la solution, vous disposez d’un certain nombre de projets individuels :  
  
    -   **WeatherApp** : bibliothèque .NET Standard dans laquelle vous écrivez du code partagé entre les plateformes, notamment une logique métier commune et le code de l’interface utilisateur à l’aide de Xamarin.Forms.  
  
    -   **WeatherApp.Android**: projet qui contient le code Android natif. Ce projet est défini comme projet de démarrage par défaut.  
  
    -   **WeatherApp.iOS**: projet qui contient le code iOS natif.  
  
    -   **WeatherApp.UWP**: le projet qui contient du code Windows 10 UWP.  
  
    > [!NOTE]
    >  Vous êtes libre de supprimer tous les projets pour une plateforme que vous ne ciblez pas.   
  
     Dans chaque projet natif, vous avez accès au concepteur natif pour la plateforme correspondante et pouvez implémenter des écrans et fonctionnalités spécifiques à la plateforme en fonction des besoins.  
  
4.  Mettez à niveau le package NuGet Xamarin.Forms dans votre solution vers la dernière version stable comme suit. Nous vous recommandons d’effectuer cette opération chaque fois que vous créez une solution Xamarin :  
  
    -   Sélectionnez **Outils > Gestionnaire de package NuGet > Gérer les packages NuGet pour la solution**.  
  
    -   Sous l’onglet **Mises à jour**, cochez le package **Xamarin.Forms** et cochez cette option pour mettre à jour tous les projets de votre solution. (Remarque : laissez les mises à jour pour Xamarin.Android.Support décochées.)  
  
    -   Mettez à jour le champ **Version** en sélectionnant **Dernière stable** pour la version disponible.  
  
    -   Cliquez sur **Installer**.  
  
         ![Mise à jour du package NuGet Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
5.  Ajoutez le package NuGet **Newtonsoft.Json** au projet **WeatherApp**, que vous allez utiliser pour traiter les informations récupérées à partir d’un service de données météo :  
  
    -   Dans le Gestionnaire de package NuGet (toujours ouvert depuis l’étape 4), sélectionnez l’onglet **Parcourir** et recherchez **Newtonsoft**.  
  
    -   Sélectionnez **Newtonsoft.Json**.  
  
    -   Cochez le projet **WeatherApp** (il s’agit du seul projet dans lequel vous devez installer le package).  
  
    -   Vérifiez que la valeur définie pour le champ **Version** est **Dernière stable** .  
  
    -   Cliquez sur **Installer**.  
  
    ![Localisation et installation du package NuGet Newtonsoft.Json](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  Répétez l’étape 5 ci-dessus pour rechercher et installer le package **Microsoft.Net.Http** .  
  
7.  Générez votre solution et vérifiez l’absence d’erreur de génération.  
  
##  <a name="dataservice"></a> Écrire le code de service de données partagé  

Le projet **WeatherApp** est l’emplacement où vous allez écrire du code pour la bibliothèque .NET Standard partagée entre les plateformes. La bibliothèque est automatiquement incluse dans les packages d’application générés par les projets iOS, Android et Windows.  
  
Pour exécuter cet exemple, vous devez tout d’abord vous inscrire pour obtenir une clé API gratuite sur [http://openweathermap.org/appid](http://openweathermap.org/appid).  
  
Les étapes suivantes permettent d’ajouter du code à la bibliothèque .NET Standard pour accéder aux données de ce service météo et stocker ces données :  
  
1.  Cliquez avec le bouton droit sur le projet **WeatherApp** et sélectionnez **Ajouter > Classe**. Dans la boîte de dialogue **Ajouter un nouvel élément** , nommez le fichier **Weather.cs**. Vous allez utiliser cette classe pour stocker les données du service de données météo.  
  
2.  Remplacez l’intégralité du contenu de **Weather.cs** par le code suivant :  
  
    ```csharp  
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```  
  
3.  Ajoutez au projet **WeatherApp** une autre classe, nommée **DataService.cs**, que vous allez utiliser pour traiter les données JSON du service de données météo.  
  
4.  Remplacez l’intégralité du contenu de **DataService.cs** par le code suivant :  
  
    ```csharp  
    using System.Net.Http;  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
    
    namespace WeatherApp  
    {  
        public class DataService  
        {  
            public static async Task<dynamic> getDataFromService(string queryString)  
            {  
                HttpClient client = new HttpClient();  
                var response = await client.GetAsync(queryString);  
  
                dynamic data = null;  
                if (response != null)  
                {  
                    string json = response.Content.ReadAsStringAsync().Result;  
                    data = JsonConvert.DeserializeObject(json);  
                }  
  
                return data;  
            }  
        }  
    }  
    ```  
  
5.  Ajoutez au projet **WeatherApp** une troisième classe nommée **Core** dans laquelle vous placerez la logique métier partagée. Ce code forme une chaîne de requête à l’aide du code postal, appelle le service météo, puis remplit une instance de la classe **Weather**.  
  
6.  Remplacez le contenu de **Core.cs** par le code suivant :  
  
    ```csharp  
    using System;  
    using System.Threading.Tasks;  
  
    namespace WeatherApp  
    {  
        public class Core  
        {  
            public static async Task<Weather> GetWeather(string zipCode)  
            {  
                //Sign up for a free API key at http://openweathermap.org/appid  
                string key = "YOUR KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  
  
                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);  
  
                if (results["weather"] != null)  
                {  
                    Weather weather = new Weather();  
                    weather.Title = (string)results["name"];                  
                    weather.Temperature = (string)results["main"]["temp"] + " F";  
                    weather.Wind = (string)results["wind"]["speed"] + " mph";                  
                    weather.Humidity = (string)results["main"]["humidity"] + " %";  
                    weather.Visibility = (string)results["weather"][0]["main"];  
  
                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);  
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);  
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);  
                    weather.Sunrise = sunrise.ToString() + " UTC";  
                    weather.Sunset = sunset.ToString() + " UTC";  
                    return weather;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
        }  
    }  
    ```  
  
7.  Générez le projet de bibliothèque **WeatherApp** pour vérifier que le code est correct.  
  
##  <a name="uicode"></a> Commencer la rédaction du code de l’interface utilisateur partagé  

Xamarin.Forms vous permet d’implémenter le code de l’interface utilisateur partagé dans la bibliothèque .NET Standard. Dans cette procédure, vous allez ajouter une page au projet avec un bouton qui met à jour son texte avec les données retournées par le code du service de données météo ajouté dans la section précédente :  
  
1.  Ajoutez une **page de contenu** nommée **WeatherPage.cs** en cliquant avec le bouton droit sur le projet **WeatherApp**, puis en sélectionnant **Ajouter > Nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Page de contenu**. Veillez à ne pas sélectionner **Page de contenu (C#)** ou **Affichage du contenu**. Nommez la page **WeatherPage.cs**.  
  
     ![Ajout d’une nouvelle page XAML Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     Xamarin.Forms étant basé sur XAML, cette étape crée un fichier **WeatherPage.xaml** ainsi que le fichier code-behind imbriqué **WeatherPage.xaml.cs**. Cela vous permet de générer l’interface utilisateur via XAML ou du code. Vous procéderez de l’une des deux façons dans cette procédure pas à pas.  
  
2.  Pour ajouter un bouton à l’écran WeatherPage, remplacez le contenu de **WeatherPage.xaml** par le code suivant :  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">  
      <Button x:Name="getWeatherBtn" 
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />  
    </ContentPage>  
    ```  
  
     Notez que le nom du bouton doit être défini à l’aide de l’attribut **x:Name** pour pouvoir faire référence à ce bouton par son nom depuis le fichier code-behind.  
  
3.  Pour ajouter un gestionnaire d’événements pour l’événement **Clicked** du bouton pour mettre à jour le texte du bouton, remplacez le contenu de **WeatherPage.xaml.cs** par le code ci-dessous. (Vous pouvez remplacer « 60601 » par un autre code postal).  
  
    ```csharp  
    using System;  
    using Xamarin.Forms;  
  
    namespace WeatherApp  
    {  
        public partial class WeatherPage: ContentPage  
        {  
            public WeatherPage()  
            {  
                InitializeComponent();  
  
                //Set the default binding to a default object for now  
                BindingContext = new Weather();  
            }  
  
            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
            {  
                Weather weather = await Core.GetWeather("60601");  
                getWeatherBtn.Text = weather.Title;  
            }  
        }  
    }  
    ```  
  
4.  Pour ouvrir **WeatherPage** en tant que premier écran quand l’application démarre, remplacez le constructeur par défaut dans **App.cs** par le code suivant :  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Générez le projet **WeatherApp** pour vérifier que le code est correct.  
  
##  <a name="test"></a> Tester votre application avec l’émulateur Visual Studio pour Android  

Vous êtes maintenant prêt à exécuter l’application ! À présent, exécutez simplement la version Android pour vérifier que l’application obtient des données du service météo. Par la suite, vous exécuterez également les versions iOS et UWP après avoir ajouté d’autres éléments d’interface utilisateur.   
  
1.  Définissez **WeatherApp.Android** comme projet de démarrage en cliquant dessus avec le bouton droit et en sélectionnant **Définir comme projet de démarrage**.  
  
2.  Dans la barre d’outils Visual Studio, **WeatherApp.Android** est répertorié comme projet cible. Sélectionnez l’un des émulateurs Android pour le débogage et appuyez sur **F5**. Nous vous recommandons d’utiliser l’une des options de l’émulateur **Visual Studio** pour l’exécution de l’application dans l’émulateur Visual Studio pour Android.  
  
     ![Sélection d’une cible de débogage de l’émulateur Android](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  Quand l’application démarre dans l’émulateur, cliquez sur le bouton **Get Weather** . Le texte du bouton doit être mis à jour et contenir **Chicago**, qui est la propriété *Title* des données récupérées à partir du service météo.  
  
     ![Application météo Weather App avant et après avoir appuyé sur le bouton](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a> Terminer l’interface utilisateur avec une apparence native entre les plateformes  

Xamarin.Forms affiche les contrôles de l’interface utilisateur native pour chaque plateforme afin que votre application obtienne automatiquement une apparence native. Pour mieux vous rendre compte , terminez l’interface utilisateur avec un champ d’entrée pour un code postal, puis affichez les données météo retournées par le service.  
  
1.  Remplacez le contenu de **WeatherPage.xaml** par le code ci-dessous. Les éléments nommés à l’aide de l’attribut **x:Name**, comme décrit précédemment, peuvent être référencés à partir du code. Xamarin.Forms fournit également un certain nombre d[’options de disposition](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com). Ici, WeatherPage utilise [Grid](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) (xamarin.com) et [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
            
                <Label Text="Search by Zip Code" 
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />
            
                <Label x:Name="zipCodeLabel" Text="Zip Code:" 
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />
            
                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />
            
                <Button x:Name="getWeatherBtn" Text="Get Weather" 
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>  
     ```  
  
     Bien que cela n’est pas indiqué ici, vous pouvez utiliser la balise **OnPlatform** pour sélectionner une valeur de propriété spécifique à la plateforme actuelle sur laquelle l’application est exécutée (consultez [External XAML Syntax](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (xamarin.com). Dans le fichier code-behind, vous pouvez utiliser l’ [API Device.OnPlatform](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) dans le même but.  
  
2.  Dans **WeatherPage.xaml.cs**, remplacez le gestionnaire d’événements **GetWeatherBtn_Clicked** par le code ci-dessous. Ce code vérifie qu’un code postal figure dans le champ d’entrée, récupère les données pour ce code postal, affecte l’instance résultante de **Weather** au contexte de liaison de la totalité de la page, puis définit « Rechercher à nouveau » comme texte du bouton. Notez que chaque étiquette dans l’interface utilisateur est liée à une propriété de la classe **Weather** ; ainsi, quand vous affectez une instance de **Weather** au contexte de liaison de l’écran, ces étiquettes sont automatiquement mises à jour.  
  
    ```csharp  
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
    {  
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
        {  
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
            BindingContext = weather;  
            getWeatherBtn.Text = "Search Again";  
        }  
    }  
    ```  
  
3.  Exécutez l’application sur les trois plateformes (Android, iOS et Windows) en cliquant avec le bouton droit sur le projet approprié, en sélectionnant **Définir comme projet de démarrage** et en démarrant l’application sur un appareil, dans l’émulateur ou dans le simulateur. Entrez un code postal valide à cinq chiffres des États-Unis et appuyez sur le bouton **Get Weather** pour afficher les données météo de cette région, comme indiqué ci-dessous. Visual Studio doit être connecté à un ordinateur Mac OS X sur votre réseau pour le projet iOS.  
  
     ![Exemple d’application météo sur Android, iOS et Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
Le code source complet de ce projet est dans le [dépôt d’exemples Xamarin.Forms sur GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).