---
title: "Élément de liste déroulante | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9980232a7927bf1ae2df9d5f6329a57a031d3f56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="combo-element"></a>Élément de liste déroulante
Définit des commandes qui s’affichent dans une zone de liste déroulante. Il existe quatre types de zones de liste déroulante, comme suit : DropDownCombo, DynamicCombo, IndexCombo et MRUCombo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|GUID|Obligatoire. GUID de l’identificateur de commande/ID GUID.|  
|ID|Obligatoire. ID de l’identificateur de commande/ID GUID.|  
|defaultWidth|Obligatoire. Entier qui spécifie une largeur en pixels de la zone de liste déroulante.|  
|idCommandList|Obligatoire. Un ID qui est envoyé à la cible de commande active pour récupérer la liste des éléments à afficher dans la zone de liste déroulante. L’ID sera dans la même étendue GUID en tant que le contrôle.|  
|priority|Facultatif. Une valeur numérique qui spécifie la priorité.|  
|type|Facultatif. Valeur énumérée qui spécifie le type de bouton.<br /><br /> Si non, utilise le bouton.<br /><br /> DropDownCombo<br /> Le VSPackage est chargé pour remplir le contenu de cette zone de liste déroulante. L’utilisateur ne peut pas taper quoi que ce soit dans la zone de texte de ce menu déroulant.<br /><br /> DynamicCombo<br /> Le VSPackage est chargé pour remplir le contenu de cette zone de liste déroulante. L’utilisateur peut modifier cette liste déroulante et sélectionnez également les éléments qu’il contient.<br /><br /> IndexCombo<br /> Identique à DynamicCombo, sauf qu’elle déclenche l’index de l’élément plutôt que son texte.<br /><br /> MRUCombo<br /> Rempli par l’environnement de développement intégré (IDE) pour le compte le VSPackage.  L’utilisateur peut modifier cette zone de liste modifiable. L’IDE se souvient jusqu'à 16 dernières écritures par zone de liste déroulante.<br /><br /> Lorsque l’utilisateur sélectionne un élément dans la zone de liste déroulante, ou passe à un nouvel élément, l’IDE notifie le VSPackage approprié.|  
|Condition|Facultatif. Consultez [attributs conditionnels](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|Parent|Facultatif. L’élément parent du bouton.|  
|CommandFlag|Obligatoire. Consultez [élément de l’indicateur de commande](../extensibility/command-flag-element.md). Voici les valeurs CommandFlag valides pour un bouton.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Les touches filtres<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Chaînes|Obligatoire. Consultez [chaînes élément](../extensibility/strings-element.md). L’élément de ButtonText enfant doit être défini.|  
|Annotation|Commentaire facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément Commands](../extensibility/commands-element.md)|Représente la collection de commandes dans la barre d’outils du VSPackage.|  
  
## <a name="example"></a>Exemple  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)