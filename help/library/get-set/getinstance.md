---
description: getInstance renvoie un objet ID de visiteur pour l’ID d’organisation Experience Cloud spécifié. Ceci est nécessaire pour initialiser l’objet ID de visiteur fourni à AppMeasurement par le biais de s.visiteur.
keywords: ID Service
seo-description: getInstance renvoie un objet ID de visiteur pour l’ID d’organisation Experience Cloud spécifié. Ceci est nécessaire pour initialiser l’objet ID de visiteur fourni à AppMeasurement par le biais de s.visiteur.
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: tm+mt
source-git-commit: d2bc0e7fedc4e48d51f5dad158f9f8bfcb0cb4f3

---


# getInstance{#getinstance}

getInstance renvoie un objet ID de visiteur pour l’ID d’organisation Experience Cloud spécifié. Ceci est nécessaire pour initialiser l’objet ID de visiteur fourni à AppMeasurement par le biais de s.visiteur.

**Syntaxe**

**JavaScript **

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
>*N’instanciez pas* la fonction Visitor avec `var visitor = new Visitor`. Vous devez utiliser l’appel de fonction approprié indiqué ici. Applies to [!UICONTROL VisitorAPI.js] code library v3.0 or higher.

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

Si `getInstance` ne trouve pas d’instance existante, une instance est créée et renvoyée. Cette fonction est similaire à la [`s_gi()` fonction ](https://docs.adobe.com/content/help/en/analytics/implementation/vars/functions/s-gi.html) de [!DNL AppMeasurement].

**Utilisation courante**

L’API du service [!DNL Experience Cloud] ID gère la liste de toutes les instances créées pour chaque [!DNL Adobe Experience Cloud] ID d’organisation. Si l’application qui utilise le service d’ID API ne transmet pas de référence à l’instance, elle peut la trouver en appelant `getInstance` au lieu d’en créer une autre. Cela permet également la prise en charge de plusieurs instances pour différentes organisations dans la même page/application Web.

Cela s’avère utile pour les applications qui n’ont pas une `init` phase claire, mais qui doivent invoquer l’API du service d’ID en plusieurs endroits. Vous pouvez appeler `getInstance` à tous ces emplacements et le premier à s’exécuter crée l’instance. L’instance existante est renvoyée par les appels qui suivent.
