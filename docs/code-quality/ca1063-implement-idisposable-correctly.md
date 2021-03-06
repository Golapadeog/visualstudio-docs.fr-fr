---
title: "CA1063 : Implémenter IDisposable correctement | Documents Microsoft"
ms.custom: 
ms.date: 02/12/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 29a2fbb82fd2795c675bfa249e213488913745a9
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063 : Implémenter IDisposable correctement

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

`IDisposable` n’est pas implémentée correctement. Voici quelques raisons pour lesquelles ce problème :

- IDisposable est réimplémenté dans la classe.

- Finalize est substitué à nouveau.

- Dispose est substitué.

- Dispose() n’est pas public, scellé ni Dispose nommé.

- Dispose (bool) n’est pas protégé, virtuel ou non scellé.

- Dans les types non scellés, Dispose() doit appeler Dispose (true).

- Pour les types déverrouillés, l’implémentation Finalize n’appelle pas le finaliseur de classe de cas ou de dispose (bool) un ou les deux.

Violation de l’un de ces modèles déclenche cet avertissement.

Chaque type unsealed qui déclare et implémente l’interface IDisposable doit fournir sa propre méthode Dispose (bool) void virtuelle protégée. Dispose() doit appeler Dipose (true) et Finalize doit appeler Dispose (false). Si vous créez un type unsealed qui déclare et implémente l’interface IDisposable, vous devez définir dispose (bool) et l’appeler. Pour plus d’informations, consultez [nettoyage des ressources non managées](/dotnet/standard/garbage-collection/unmanaged) dans les [les règles de conception de .NET Framework](/dotnet/standard/design-guidelines/index).

## <a name="rule-description"></a>Description de la règle

Tous les types IDisposable doivent implémenter le modèle Dispose correctement.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Examinez votre code et déterminer lequel des solutions suivantes corrigera cette violation.

- Supprimez IDisposable de la liste des interfaces qui sont implémentées par {0} et substituer l’implémentation de Dispose de la classe de base à la place.

- Supprimez le finaliseur du type {0}, substituez Dispose (bool disposing) et placez la logique de finalisation dans le chemin d’accès du code où 'disposing' a la valeur false.

- Suppression de {0}, substituez Dispose (bool disposing) et placez la logique dispose dans le chemin d’accès du code où 'disposing' a la valeur true.

- Vérifiez que {0} est déclaré comme public et sealed.

- Renommez les {0} en 'Dispose' et vérifiez qu’il est déclaré comme public et sealed.

- Assurez-vous que ce {0} est déclaré comme protected, virtual et unsealed.

- Modifiez le {0} afin qu’il appelle Dispose (true), puis appelle GC. SuppressFinalize sur l’instance d’objet actuelle ('this' ou 'Me' dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), puis retourne.

- Modifier afin qu’il appelle Dispose (false), puis retourne les {0}.

- Si vous créez un type unsealed qui déclare et implémente l’interface IDisposable, assurez-vous que l’implémentation de IDisposable suit le modèle qui est décrite plus haut dans cette section.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="pseudo-code-example"></a>Exemple de pseudo-code

Le pseudo-code suivant fournit un exemple général de la manière dont dispose (bool) doit être implémentée dans une classe qui utilise gérée et ressources natives.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```