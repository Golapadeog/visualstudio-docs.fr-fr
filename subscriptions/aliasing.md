---
title: "La connexion aux abonnements Visual Studio peut échouer avec des alias | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/2/2018
Ms.topic: Get-Started-Article
Description: Sign-in may fail if aliases or friendly names are used.
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 8c07bc8d3cf674d86c2152ff80f20e4fac003fc3
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-with-aliases"></a>La connexion aux abonnements Visual Studio peut échouer avec des alias

Selon le type de compte utilisé pour vous connecter, les abonnements disponibles peuvent ne pas s’afficher correctement durant la connexion au site [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Ce cas peut se produire si l’utilisateur emploie des « alias » ou des « noms conviviaux » au lieu de l’identité de connexion à laquelle l’abonnement est affecté. On parle ici d’utilisation d’alias. 

## <a name="what-is-aliasing"></a>Qu’est-ce que l’utilisation d’alias ?

L’utilisation d’alias fait référence aux utilisateurs qui emploient des identités différentes pour se connecter à Windows (ou à leur compte Active Directory) et accéder à leur messagerie électronique.

Une entreprise peut par exemple posséder un service en ligne Microsoft pour sa connexion active (comme JohnD@contoso.com), mais les utilisateurs accèdent à leurs comptes de messagerie à l’aide d’alias ou de noms conviviaux (comme John.Doe@contoso.com).  Pour de nombreux clients qui gèrent leurs abonnements à travers le Centre de gestion des licences en volume (VLSC), cela peut se traduire par un échec de la connexion, car l’adresse e-mail fournie (John.Doe@contoso.com) ne correspond pas à l’adresse d’annuaire (JohnD@contoso.com) requise pour une authentification correcte via l’option « Compte professionnel ou scolaire ».

## <a name="as-an-administrator-what-options-do-i-have"></a>En tant qu’administrateur, quelles options ai-je à ma disposition ?

En tant qu’administrateur, vous avez le choix entre deux options pour garantir la connexion correcte de vos abonnés au site [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs). 
1. La première option (recommandée) consiste à utiliser le compte d’annuaire en tant qu’adresse attribuée dans le Centre de gestion des licences en volume (VLSC). Pour plus d’informations, consultez la section [Attribution d’un compte d’annuaire à des abonnés](#assigning-subscribers-to-a-directory-account) de cet article.
2. La deuxième option (moins sécurisée) consiste à permettre à vos abonnés d’associer leur adresse e-mail « professionnelle ou scolaire » à un compte « personnel » (également appelé compte Microsoft ou MSA). Pour plus d’informations, consultez la section [Définition d’un compte professionnel ou scolaire en tant que compte personnel](#defining-a-work-or-school-account-as-a-personal-account ) de cet article.

> [!NOTE]
> Dès que votre entreprise aura migré vers le nouveau [portail de gestion](https://manage.visualstudio.com) des abonnements Visual Studio, vous pourrez bénéficier de la nouvelle expérience d’administration qui permet de fournir à la fois des adresses e-mail et des adresses d’annuaire en tant qu’éléments de profil des abonnés.  Découvrez-en plus sur [la migration](https://support.microsoft.com/help/4013930/visual-studio-subscriptions-administrator-migration-details).

## <a name="as-a-subscriber-what-options-do-i-have"></a>En tant qu’abonné, quelles options ai-je à ma disposition ?

En tant qu’abonné, il est important de collaborer dans un premier temps avec votre administrateur pour bien comprendre la configuration des identités de votre entreprise.  Si nécessaire, votre administrateur peut avoir à mettre à jour les paramètres de votre compte à partir de son portail d’administration, ou vous devrez peut-être créer un compte Microsoft (MSA) en utilisant votre adresse e-mail d’entreprise.  Avant d’effectuer les étapes requises pour créer un compte MSA, contactez votre administrateur pour vous renseigner sur les stratégies ou problèmes liés à cette action.  Pour plus d’informations, consultez la section [Définition d’un compte professionnel ou scolaire en tant que compte personnel](#defining-a-work-or-school-account-as-a-personal-account ) de cet article.  

## <a name="assigning-subscribers-to-a-directory-account"></a>Attribution d’un compte d’annuaire à des abonnés 

Dans tous les cas, le Gestionnaire d’abonnements du Centre de gestion des licences en volume (VLSC) doit utiliser l’adresse d’annuaire pour les nouveaux abonnés ou mettre à jour l’adresse e-mail pour les abonnés « existants ».  Il est important de souligner le fait que quand l’adresse d’annuaire est utilisée, les nouveaux abonnés ne reçoivent pas de message de bienvenue. L’administrateur doit par conséquent notifier l’abonné qu’un abonnement lui a été attribué.  Après avoir effectué les étapes ci-dessous, vous pouvez, si vous le souhaitez, utiliser le [modèle](#notifying-your-subscribers-with-directory-addresses) de message électronique pour notifier vos abonnés et les aider à réaliser le processus de connexion.

### <a name="adding-new-subscribers"></a>Ajout de nouveaux abonnés
Suivez les étapes ci-dessous pour ajouter un nouvel abonné avec un compte d’annuaire.

1. Accédez au [Centre de gestion des licences en volume](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) et connectez-vous.
2. Sur la page d’administration de VLSC, cliquez sur **Abonnements**, puis sur **Abonnements Visual Studio**.

    ![Menu Abonnements](_img//vlsc/vlsc-subscriptions.png)

3. Cliquez sur le **numéro de contrat** associé à l’abonnement Visual Studio.

    ![Sélection du contrat](_img/vlsc/vlsc-agreement.png)

4. Cliquez sur **Attribuer un abonnement**.

    ![Attribution d’un abonnement](_img/vlsc/vlsc-assign.png)

5. Sélectionnez le **niveau d’abonnement** souhaité.

    ![Niveau d'abonnement](_img/vlsc/vlsc-subscription-level.png)
    
6. Vérifiez que vous disposez d’abonnements disponibles à attribuer, puis cliquez sur **Suivant**.
7.  Entrez les détails de l’abonné et l’adresse d’annuaire dans le champ Adresse e-mail, puis cliquez sur **Suivant**.

    ![Adresse de messagerie](_img/vlsc/vlsc-email-address.png)
    
8. Confirmez les informations de l’abonné et cliquez sur **Terminer**.

9. Notifiez l’abonné de son nouvel abonnement à l’aide du [modèle](#notifying-your-subscribers-with-directory-addresses) ci-dessous.

### <a name="updating-an-existing-subscriber"></a>Mise à jour d'un abonné existant
Suivez les étapes ci-dessous pour mettre à jour un abonné existant avec un compte d’annuaire.

1. Accédez au [Centre de gestion des licences en volume](https://www.microsoft.com/Licensing/servicecenter/default.aspx) (VLSC) et connectez-vous.

2. Sur les pages d’administration de VLSC, cliquez sur **Abonnements**, puis sur **Abonnements Visual Studio**.

3. Cliquez sur le **numéro de contrat** associé à l’abonnement Visual Studio.

4. Cliquez sur la **flèche vers le bas** dans la barre de recherche.

5. Recherchez l’abonné à l’aide du champ « Adresse e-mail ».

6. Dans la liste des résultats, cliquez sur le **nom** de l’abonné.

7. Cliquez sur **Modifier**.

8. Remplacez l’adresse du champ Adresse e-mail par l’adresse d’annuaire souhaitée, puis cliquez sur **Enregistrer**.

9. Notifiez l’abonné de son nouvel abonnement à l’aide du modèle de message électronique ci-dessous.

### <a name="notifying-your-subscribers-with-directory-addresses"></a>Notification de vos abonnés avec des adresses d’annuaire
Étant donné que le message de bienvenue ne sera pas correctement envoyé à votre abonné, copiez et collez le message ci-dessous dans un e-mail et envoyez-le à votre abonné. Remplacez %TEXTE% par les informations appropriées pour chaque abonné.

----------- Copiez le texte suivant (Ctrl+C) -----------

Bonjour %NOM DE L’ABONNÉ%,

Un abonnement Visual Studio vous a été attribué.  Accédez au site https://my.visualstudio.com et connectez-vous à l’aide de votre adresse %ADRESSE D’ANNUAIRE% pour activer et accéder à votre abonnement. 

En cas de problème, veuillez contacter l’équipe de support (https://www.visualstudio.com/subscriptions/support/).

En bas de la page, sélectionnez les options suivantes :
   - Support pour les comptes, les abonnements et la facturation
   - Sous Problème, sélectionnez le support pour la connexion aux abonnements
   - Sélectionnez le pays approprié
   - Sélectionnez l’option de support assisté souhaitée

----------- Fin du texte -----------



## <a name="defining-a-work-or-school-account-as-a-personal-account"></a>Définition d’un compte professionnel ou scolaire en tant que compte personnel 
Reportez-vous aux instructions décrites dans la section [Attribution d’un compte d’annuaire à des abonnés](#assigning-subscribers-to-a-directory-account) pour ajouter un nouvel utilisateur ou mettre à jour l’adresse e-mail d’un utilisateur dans le Centre de gestion des licences en volume (VLSC).  Si l’adresse e-mail n’est pas reconnue par l’annuaire, l’utilisateur devra procéder à la création d’un nouveau compte pour définir l’adresse e-mail en tant que compte personnel.  À court terme, l’équipe des abonnements Visual Studio a mis en place une exemption de la stratégie d’identité définie ci-dessous, mais nous investissons actuellement dans les ressources nécessaires pour supprimer cette stratégie.

> [!WARNING]
> Microsoft ne recommande pas la combinaison d’identités « professionnelles et scolaires » avec des identités « personnelles ».  En effet, avec ce type de combinaison, l’entreprise perd la propriété et le contrôle du compte, et l’employé peut continuer à accéder à des produits ou services spécifiques, même après avoir quitté l’entreprise.  Pour plus d’informations, consultez ce [billet de blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/15/cleaning-up-the-azure-ad-and-microsoft-account-overlap/), publié par l’équipe chargée des identités Microsoft.

### <a name="defining-an-email-address-as-a-personal-account"></a>Définition d’une adresse e-mail en tant que compte personnel
Quand un abonnement a été attribué à l’abonné, ce dernier reçoit un e-mail lui demandant d’accéder au site https://my.visualstudio.com pour pouvoir bénéficier de tous les avantages de son abonnement.  La tentative de connexion à l’abonnement Visual Studio échouera, avec un message d’erreur indiquant que le compte n’est pas reconnu.  Avant la connexion au site https://my.visualstudio.com, demandez à votre abonné de suivre ces instructions.  Si nécessaire, vous pouvez utiliser ce [modèle](#notifying-your-subscribers-using-personal-accounts) pour notifier votre abonné après lui avoir attribué un abonnement.

1. Accédez au site https://my.visualstudio.com et cliquez sur **Créer un compte Microsoft**.

2. Renseignez les champs :
    - Entrez l’adresse e-mail ayant reçu le message de bienvenue dans la zone Someone@example.com.
    - Créez votre mot de passe.
    - Choisissez vos paramètres de type promotionnel.
    - Cliquez sur **Suivant**.

3. Réalisez les étapes de validation, puis cliquez sur **Suivant**.

4. Les nouveaux utilisateurs devront peut-être compléter le profil Visual Studio.

5. L’abonnement et les avantages devraient maintenant être visibles.

### <a name="notifying-your-subscribers-using-personal-accounts"></a>Notification à vos abonnés utilisant des comptes personnels

Dans le scénario décrit précédemment, votre abonné reçoit un « message de bienvenue », mais en raison de l’utilisation d’alias, il est possible qu’il ne parvienne pas à se connecter.  Vous pouvez utiliser le texte ci-dessous pour informer votre abonné des étapes mentionnées précédemment et pour lui recommander des options de support, si nécessaire.  Remplacez %TEXTE% par les informations appropriées pour chaque abonné.

----------- Copiez le texte suivant (Ctrl+C) -----------

Bonjour %NOM DE L’ABONNÉ%,

Un abonnement Visual Studio vous a été attribué. Il se peut que vous ayez été redirigé vers le site https://my.visualstudio.com pour vous connecter, selon votre message de bienvenue.  Bien qu’il s’agisse du site web correct pour bénéficier des avantages, notre organisation vous invite à réaliser quelques étapes supplémentaires pour pouvoir accéder au site.  Suivez les instructions ci-dessous pour créer facilement un « compte Microsoft » lié à notre adresse e-mail d’entreprise.  Après avoir réalisé ces étapes, vous devrez utiliser votre adresse e-mail pour accéder aux avantages de l’abonnement.
1. Accédez au site https://my.visualstudio.com.

2. Cliquez sur Créer un compte Microsoft à droite.

3. Remplissez le formulaire : 
    - Utilisez votre adresse e-mail d’entreprise dans la zone someone@example.com.
    - Entrez un mot de passe.
    - Sélectionnez vos préférences de type promotionnel.
    - Cliquez sur Suivant

4. Réalisez les étapes de validation du compte.

5. Si nécessaire, complétez le profil Visual Studio.

6. Vos avantages devraient à présent être affichés.

Remarque : La prochaine fois que vous vous connecterez au site https://my.visualstudio.com, vous serez peut-être invité à sélectionner le compte que vous souhaitez utiliser (par exemple, « Compte professionnel ou scolaire » ou « Compte personnel »).  Une fois les étapes ci-dessus réalisées, vous devrez utiliser l’option « Compte personnel ».

En cas de problème, veuillez contacter l’équipe de support (https://www.visualstudio.com/subscriptions/support/).

En bas de la page, sélectionnez les options suivantes :
   - Support pour les comptes, les abonnements et la facturation
   - Sous Problème, sélectionnez le support pour la connexion aux abonnements
   - Sélectionnez le pays approprié
   - Sélectionnez l’option de support assisté souhaitée

----------- Fin du texte -----------