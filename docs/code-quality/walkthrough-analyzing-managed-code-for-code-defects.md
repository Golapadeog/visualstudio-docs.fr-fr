---
title: "Analyse de la procédure pas à pas du Code managé pour les erreurs de Code | Documents Microsoft"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e1c708f31d31dd811017015cd37c7e60d49beef9
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Procédure pas à pas : Défauts analyse du code pour le code managé

Dans cette procédure pas à pas, vous allez analyser un projet managé pour les erreurs de code à l’aide de l’outil d’analyse du code.

Cette procédure pas à pas vous guide tout au long de l’utilisation de l’analyse du code pour analyser les assemblys de code managé .NET pour la conformité avec les règles de conception de Microsoft .NET Framework.

## <a name="create-a-class-library"></a>Créer une bibliothèque de classes

### <a name="to-create-a-class-library"></a>Pour créer une bibliothèque de classes

1. Sur le **fichier** menu, choisissez **nouveau** > **projet...** .

1. Dans le **nouveau projet** boîte de dialogue, développez **installé** > **Visual C#**, puis choisissez **de bureau Windows classique**.

1. Choisissez le **bibliothèque de classes (.NET Framework)** modèle.

1. Dans le **nom** zone de texte, tapez **CodeAnalysisManagedDemo** puis cliquez sur **OK**.

1. Une fois le projet est créé, ouvrez le *Class1.cs* fichier.

1. Remplacez le texte existant dans le fichier Class1.cs par le code suivant :

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Enregistrez le fichier Class1.cs.

## <a name="analyze-the-project"></a>Analyser le projet

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Pour analyser un projet managé pour les erreurs de code

1. Sélectionnez le projet CodeAnalysisManagedDemo dans **l’Explorateur de solutions**.
  
1. Dans le menu **Projet**, cliquez sur **Propriétés**.
  
     La page de propriétés CodeAnalysisManagedDemo s’affiche.
  
1. Choisissez le **l’analyse du Code** onglet.
  
1. Assurez-vous que **activer l’analyse du Code sur la Build** est activée.
  
1. À partir de la **exécuter cet ensemble de règles** la liste déroulante, sélectionnez **toutes les règles Microsoft**.
  
1. Sur le **fichier** menu, cliquez sur **enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés.
  
1. Sur le **générer** menu, cliquez sur **CodeAnalysisManagedDemo de Build**.
  
    Les avertissements de build du projet CodeAnalysisManagedDemo sont affichés dans le **liste d’erreurs** et **sortie** windows.

## <a name="correct-the-code-analysis-issues"></a>Corrigez les problèmes d’analyse de code

### <a name="to-correct-code-analysis-rule-violations"></a>Pour corriger les violations de règles code analysis

1. Sur le **vue** menu, choisissez **liste d’erreurs**.

    Selon le profil de développeur que vous avez choisi, vous devez pointer vers **autres fenêtres** sur la **vue** menu, puis choisissez **liste d’erreurs**.

1. Dans **l’Explorateur de solutions**, choisissez **afficher tous les fichiers**.

1. Développez le nœud Propriétés, puis ouvrez le *AssemblyInfo.cs* fichier.

1. Utilisez les conseils suivants pour corriger les avertissements :

   [CA1014 : Marquer les assemblys avec CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design : 'demo' doit être marqué avec CLSCompliantAttribute et sa valeur doit être true.

   1. Ajoutez le code `using System;` dans le fichier AssemblyInfo.cs.

   1. Ensuite, ajoutez le code `[assembly: CLSCompliant(true)]` à la fin du fichier AssemblyInfo.cs.

   [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : ajoutez le constructeur suivant à cette classe : public demo (String)

   1. Ajoutez le constructeur `public demo (String s) : base(s) { }` à la classe `demo`.

   [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : ajoutez le constructeur suivant à cette classe : public demo (String, Exception)

   1. Ajoutez le constructeur `public demo (String s, Exception e) : base(s, e) { }` à la classe `demo`.

   [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : ajoutez le constructeur suivant à cette classe : protected demo (SerializationInfo, StreamingContext)

   1. Ajoutez le code `using System.Runtime.Serialization;` au début du fichier Class1.cs.

   1. Ensuite, ajoutez le constructeur`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032 : Implémenter des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design : ajoutez le constructeur suivant à cette classe : public demo()

   1. Ajoutez le constructeur `public demo () : base() { }` à la classe `demo` **.**

   [CA1709 : La casse des identificateurs doivent être correctement](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : corrigez la casse du nom de l’espace de noms 'testCode' en le redéfinissant sur « TestCode ».

   1. Modifier la casse de l’espace de noms `testCode` à `TestCode`.

   [CA1709 : La casse des identificateurs doivent être correctement](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : corrigez la casse du nom de type « demo » en le redéfinissant sur « Demo ».

   1. Modifier le nom du membre à `Demo`.

   [CA1709 : La casse des identificateurs doivent être correctement](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming : corrigez la casse du nom de membre 'item' en le redéfinissant sur « Item ».

   1. Modifier le nom du membre à `Item`.

   [CA1710 : Les identificateurs doivent porter un suffixe correct](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming : Renommez 'testCode.Demo qu’il se » se termine par 'Exception'.

   1. Modifier le nom de la classe et ses constructeurs pour `DemoException`.

   [CA2210 : Les assemblys doivent avoir des noms forts valides](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): signer 'CodeAnalysisManagedDemo' avec une clé de nom fort.

   1. Sur le **projet** menu, choisissez **CodeAnalysisManagedDemo propriétés**.

      Les propriétés du projet s’affichent.

   1. Choisissez l'onglet **Signature** .

   1. Sélectionnez le **signer l’assembly** case à cocher.

   1. Dans le **choisir un fichier de clé de nom de chaîne** liste, sélectionnez  **\<nouveau... >**.

      Le **créer une clé de nom fort** boîte de dialogue s’affiche.

   1. Dans le **nom de fichier de clé**, tapez TestKey.

   1. Entrez un mot de passe, puis cliquez **OK**.

   1. Sur le **fichier** menu, choisissez **enregistrer les éléments sélectionnés**, puis fermez les pages de propriétés.

   [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage : ajoutez un attribut [Serializable] type 'demo' car ce type implémente ISerializable.

   1. Ajouter le `[Serializable ()]` à la classe d’attribut `demo`.

   Après avoir effectué les modifications, le fichier Class1.cs doit se présenter comme suit :

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Regénérez le projet.

## <a name="exclude-code-analysis-warnings"></a>Exclure les avertissements d’analyse du code

### <a name="to-exclude-code-defect-warnings"></a>Pour exclure les avertissements d’erreur de code

1. Pour chaque avertissement restants, procédez comme suit :

    1. Sélectionnez l’avertissement dans la **liste d’erreurs**.

    1. Dans le menu contextuel ou le contexte, choisissez **supprimer** > **dans le fichier de Suppression**.

1. Regénérez le projet.

     Le projet se génère sans les avertissements ou erreurs.

## <a name="see-also"></a>Voir aussi

[Analyse du code pour le code managé](../code-quality/code-analysis-for-managed-code-overview.md)