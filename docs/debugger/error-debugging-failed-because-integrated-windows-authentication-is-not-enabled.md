---
title: "Erreur : Le débogage a échoué car l’authentification Windows intégrée n’est pas activée. | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3d66a2892378f04061907e383965c6c02096bf1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Erreur : le débogage a échoué, car l'authentification intégrée de Windows n'est pas activée
L'authentification de l'utilisateur qui a demandé le débogage a été empêchée en raison d'une erreur d'authentification. Cette erreur peut se produire lorsque vous essayez d'accéder à une application Web ou à un service Web XML. Cette erreur peut provenir, par exemple, du fait que l'authentification Windows intégrée n'est pas activée. Pour l'activer, suivez les étapes décrites dans Activer l'authentification Windows intégrée.  
  
 Si vous avez activé l’authentification Windows intégrée et que cette erreur persiste, il est possible que cette erreur est provoquée par **l’authentification Digest pour les serveurs de domaine Windows** est activé. Dans ce cas, contactez votre administrateur réseau.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Pour activer l'authentification intégrée Windows  
  
1.  Ouvrez une session sur le serveur web à l’aide d’un compte d’administrateur.  
  
2.  Cliquez sur **Démarrer** puis cliquez sur **le panneau de configuration**.  
  
3.  Dans **le panneau de configuration**, double-cliquez sur **outils d’administration**.  
  
4.  Double-cliquez sur **Internet Information Services**.  
  
5.  Cliquez sur le nœud du serveur web.  
  
     A **Sites Web** dossier s’ouvre sous le nom du serveur.  
  
6.  Vous pouvez configurer l’authentification pour tous les sites web ou pour certains sites web. Pour configurer l’authentification pour tous les sites Web, cliquez sur le **Sites Web** dossier, puis cliquez sur **propriétés**. Pour configurer l’authentification pour un site Web individuel, ouvrez le **Sites Web** dossier, cliquez sur le site Web individuel, puis cliquez sur **propriétés**.  
  
     Le **propriétés** boîte de dialogue s’affiche.  
  
7.  Cliquez sur le **sécurité du répertoire** onglet.  
  
8.  Dans le **anonymes et contrôle d’authentification** , cliquez sur **modifier**.  
  
     Le **les méthodes d’authentification** boîte de dialogue s’affiche.  
  
9. Sous **accès authentifié**, sélectionnez **l’authentification Windows intégrée**.  
  
10. Cliquez sur **OK** pour fermer la **les méthodes d’authentification** boîte de dialogue.  
  
11. Cliquez sur **OK** pour fermer la **propriétés** boîte de dialogue.  
  
12. Fermer le **Internet Information Services** fenêtre.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Pour activer l'authentification Windows intégrée dans Windows Vista/IIS 7  
  
1.  Ouvrez une session sur le serveur web à l’aide d’un compte d’administrateur.  
  
2.  Activez l'authentification Windows et la compatibilité avec la gestion IIS 6, si ce n'est déjà fait, en procédant comme suit :  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration** puis cliquez sur **programmes**.  
  
    2.  Sous **programmes et fonctionnalités**, cliquez sur **ou désactiver des fonctionnalités Windows d’activer**.  
  
         La boîte de dialogue Contrôle d'accès utilisateur s'affiche et vous invite à confirmer que vous êtes autorisé à poursuivre.  
  
    3.  Cliquez sur **Continuer**.  
  
         La boîte de dialogue Fonctionnalités Windows apparaît.  
  
    4.  Dans la liste des fonctionnalités, développez le **Internet Information Services** nœud.  
  
    5.  Sous **Internet Information Services**, développez le **Services World Wide Web** nœud.  
  
    6.  Sous **Services World Wide Web**, cliquez sur **sécurité**.  
  
    7.  Cliquez sur **l’authentification Windows**.  
  
    8.  Sous **Internet Information Services**, développez le **outils d’administration Web** nœud.  
  
    9. Sous **outils d’administration Web**, développez le **IIS 6 Management Compatibility** nœud, puis sélectionnez le **avec la métabase de IIS 6 et compatibilité avec la Configuration IIS 6** case à cocher.  
  
    10. Sous **outils d’administration Web**, sélectionnez **Console de gestion IIS** et cliquez sur **OK.**  
  
    11. Redémarrez l'ordinateur pour que ces modifications soient prises en compte.  
  
3.  Cliquez sur **Démarrer** puis, cliquez sur **le panneau de configuration**.  
  
4.  Cliquez sur **affichage classique**, puis double-cliquez sur **outils d’administration**.  
  
5.  Dans le **nom** colonne et double-cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
6.  Dans le **connexions** colonne, développez le nœud de votre serveur.  
  
     A **Sites Web** dossier s’ouvre sous le nom du serveur.  
  
7.  Développez le **Sites Web** nœud et cliquez sur le site Web pour lequel vous souhaitez activer l’authentification Windows intégrée.  
  
8.  L’intitulé du volet central est remplacé par le nom du site web sélectionné. Dans ce volet, sous la **IIS** titre, double-cliquez sur **authentification**.  
  
     L’intitulé du volet est remplacé par **authentification**.  
  
9. Dans le **authentification** volet, dans le **nom** colonne, avec le bouton droit **l’authentification Windows** puis cliquez sur **activer**.  
  
10. Fermer le **Gestionnaire des Services Internet (IIS)** fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’Applications Web : Erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Authentification Digest de Microsoft](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Exécution d’Applications Web sur Windows Vista avec IIS 7.0 et Visual Studio](http://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)