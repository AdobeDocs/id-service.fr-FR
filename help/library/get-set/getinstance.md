---
description: getInstance renvoie un objet d’identification visiteur pour l’ID d’organisation Experience Cloud spécifié. Cela est requis pour initialiser l’objet d’identification visiteur fourni à AppMeasurement par le biais de s.visitor.
keywords: Service d’identification
seo-description: getInstance renvoie un objet d’identification visiteur pour l’ID d’organisation Experience Cloud spécifié. Cela est requis pour initialiser l’objet d’identification visiteur fourni à AppMeasurement par le biais de s.visitor.
seo-title: getInstance
title: getInstance
uuid: 259b88a6-e3d0-4aab-b935-566099bdab98
translation-type: ht
source-git-commit: f7f23d89649a888f5e9d8c94526b550fbda7045b

---


# getInstance{#getinstance}

getInstance renvoie un objet d’identification visiteur pour l’ID d’organisation Experience Cloud spécifié. Cela est requis pour initialiser l’objet d’identification visiteur fourni à AppMeasurement par le biais de s.visitor.

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

Si `getInstance` ne trouve pas d’instance existante, une instance est créée et renvoyée. Ce comportement est similaire à celui de la [ `s_gi()` fonction ](https://marketing.adobe.com/resources/help/fr_FR/sc/implement/?f=function_s_gi.html) d’[!DNL AppMeasurement].

**Utilisation courante**

L’API du service [!DNL Experience Cloud] ID gère la liste de toutes les instances créées pour chaque [!DNL Adobe Experience Cloud] ID d’organisation. Si l’application qui utilise le service d’ID API ne transmet pas de référence à l’instance, elle peut la trouver en appelant `getInstance` au lieu d’en créer une autre. Cela permet également la prise en charge de plusieurs instances pour différentes organisations dans la même page/application Web.

Cela s’avère utile pour les applications qui n’ont pas une `init` phase claire, mais qui doivent invoquer l’API du service d’ID en plusieurs endroits. Vous pouvez appeler `getInstance` à tous ces emplacements et le premier à s’exécuter crée l’instance. L’instance existante est renvoyée par les appels qui suivent.
