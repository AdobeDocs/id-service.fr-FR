---
description: getInstance renvoie un objet d’identification visiteur pour l’ID d’organisation Experience Cloud spécifié. Cela est requis pour initialiser l’objet d’identification visiteur fourni à AppMeasurement par le biais de s.visitor.
keywords: Service d’identification
seo-description: getInstance renvoie un objet d’identification visiteur pour l’ID d’organisation Experience Cloud spécifié. Cela est requis pour initialiser l’objet d’identification visiteur fourni à AppMeasurement par le biais de s.visitor.
seo-title: getInstance
title: getInstance
uuid: 259 b 88 a 6-e 3 d 0-4 aab-b 935-566099 bdab 98
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

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
>*N&#39;instanciez pas* la fonction Visiteur avec `var visitor = new Visitor`. Vous devez utiliser l’appel de fonction approprié indiqué ici. S’applique à la bibliothèque de code [!DNL VisitorAPI.js] version 3.0 ou ultérieure.

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

Si `getInstance` ne trouve pas d’instance existante, une instance est créée et renvoyée. Cette fonction est similaire à la [`s_gi()` fonction ](https://marketing.adobe.com/resources/help/en_US/sc/implement/?f=function_s_gi.html) in [!DNL AppMeasurement].

**Utilisation courante**

L&#39;API du service [!DNL Experience Cloud] d&#39;ID gère la liste de toutes les instances créées pour chaque [!DNL Adobe Experience Cloud] ID d&#39;organisation. Si l’application qui utilise le service d’ID ne transmet pas de référence à l’instance, elle peut la trouver en appelant `getInstance` au lieu d’en créer une autre. Cela permet également la prise en charge de plusieurs instances pour différentes organisations dans la même page/application Web.

Cela s&#39;avère utile pour les applications qui n&#39;ont pas de phase claire `init` mais qui doivent invoquer l&#39;API du service d&#39;ID à plusieurs emplacements. Vous pouvez appeler `getInstance` à tous ces emplacements et le premier à s’exécuter crée l’instance. L’instance existante est renvoyée par les appels qui suivent.
