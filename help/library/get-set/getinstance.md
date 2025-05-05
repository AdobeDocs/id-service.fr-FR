---
description: getInstance renvoie un objet ID de visiteur pour l’ID d’organisation Experience Cloud spécifié. Cela est nécessaire pour initialiser l’objet ID de visiteur fourni à AppMeasurement via s.visitor.
keywords: Service d’ID
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 96%

---

# getInstance{#getinstance}

getInstance renvoie un objet ID de visiteur pour l’ID d’organisation Experience Cloud spécifié. Cela est nécessaire pour initialiser l’objet ID de visiteur fourni à AppMeasurement via s.visitor.

**Syntaxe**

**JavaScript &#x200B;**

```js
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

>[!CAUTION]
>
>*N’instanciez pas* la fonction Visitor avec `var visitor = new Visitor`. Vous devez utiliser l’appel de fonction approprié indiqué ici. S’applique à la bibliothèque de code [!UICONTROL VisitorAPI.js] version 3.0 ou ultérieure.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ORGANIZATION-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Si `getInstance` ne trouve pas d’instance existante, une instance est créée et renvoyée. Ceci est similaire à la fonction [`s_gi()`](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=fr) dans [!DNL AppMeasurement].

**Utilisation courante**

L’API du service [!DNL Experience Cloud] ID gère la liste de toutes les instances créées pour chaque [!DNL Adobe Experience Cloud] ID d’organisation. Si l’application qui utilise le service d’ID API ne transmet pas de référence à l’instance, elle peut la trouver en appelant `getInstance` au lieu d’en créer une autre. Cela permet également la prise en charge de plusieurs instances pour différentes organisations dans la même page/application Web.

Cela s’avère utile pour les applications qui n’ont pas une `init` phase claire, mais qui doivent invoquer l’API du service d’ID en plusieurs endroits. Vous pouvez appeler `getInstance` à tous ces emplacements et le premier à s’exécuter crée l’instance. L’instance existante est renvoyée par les appels qui suivent.
