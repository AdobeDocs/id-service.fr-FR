---
description: getInstance renvoie un objet d’identifiant visiteur pour l’ID d’organisation IMS spécifié. Cela est nécessaire pour initialiser l’objet ID de visiteur fourni à AppMeasurement via s.visitor.
keywords: Service d’identification des visiteurs
title: getInstance
exl-id: 4941cf51-a8d0-4796-a102-4cd13cd5574d
TQID: https://experienceleague.adobe.com/XtjVkeuXAke6g-K8DNmq5kT6aUszrj6W0k9UM2NBBIA
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 230
ht-degree: 55%

---

# getInstance{#getinstance}

getInstance renvoie un objet d’identifiant visiteur pour l’ID d’organisation IMS spécifié. Cela est nécessaire pour initialiser l’objet ID de visiteur fourni à AppMeasurement via s.visitor.

**Syntaxe**

**JavaScript &#x200B;**

```js
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
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
>*N’instanciez pas* la fonction Visitor avec `var visitor = new Visitor`. Vous devez utiliser l’appel de fonction approprié indiqué ici. S’applique à la `VisitorAPI.js` bibliothèque de code version 3.0 ou ultérieure.

**ActionScript/Flash**

```js
import com.adobe.mc.Visitor; 
... 
var visitor = Visitor.getInstance("INSERT-IMS-ORG-ID-HERE", { 
     trackingServer: "INSERT-TRACKING-SERVER-HERE", // same as s.trackingServer 
     trackingServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE", // same as s.trackingServerSecure 
 
     // To enable CNAME support, add the following configuration variables 
     // If you are not using CNAME, DO NOT include these variables 
     marketingCloudServer: "INSERT-TRACKING-SERVER-HERE", 
     marketingCloudServerSecure: "INSERT-SECURE-TRACKING-SERVER-HERE" // same as s.trackingServerSecure 
});
```

Si `getInstance` ne trouve pas d’instance existante, une instance est créée et renvoyée. Ceci est similaire à la fonction [&#128279;](https://experienceleague.adobe.com/docs/analytics/implementation/vars/functions/s-gi.html?lang=fr) dans AppMeasurement.`s_gi()`

**Utilisation courante**

L’API du service d’identification des visiteurs conserve une liste de toutes les instances créées pour chaque ID d’organisation IMS. Si l’application qui utilise l’API du service d’identification des visiteurs ne transmet pas de référence à l’instance, elle peut trouver cette instance en appelant `getInstance` au lieu d’en créer une nouvelle. Cela permet également la prise en charge de plusieurs instances pour différentes organisations dans la même page/application Web.

Cela s’avère utile pour les applications qui n’ont pas de phase de `init` claire, mais qui doivent appeler l’API du service d’identification des visiteurs à plusieurs endroits. Vous pouvez appeler `getInstance` à tous ces emplacements et le premier à s’exécuter crée l’instance. L’instance existante est renvoyée par les appels qui suivent.

