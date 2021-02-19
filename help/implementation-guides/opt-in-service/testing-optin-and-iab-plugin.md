---
description: Une fois le service Opt-in activé sur votre site web, utilisez les différentes méthodes de validation afin de vérifier que celui-ci fonctionne correctement, à l’aide des outils de développement de votre navigateur.
seo-description: Une fois le service Opt-in activé sur votre site web, utilisez les différentes méthodes de validation afin de vérifier que celui-ci fonctionne correctement, à l’aide des outils de développement de votre navigateur.
seo-title: Validation du service Opt-in
title: Validation du service Opt-in
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 38%

---


# Validation du service Opt-in{#validating-opt-in-service}

Une fois le service Opt-in activé sur votre site web, utilisez les différentes méthodes de validation afin de vérifier que celui-ci fonctionne correctement, à l’aide des outils de développement de votre navigateur.

## Cas d’utilisation 1 : Activation d’Opt-in {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

Avant de charger la page, videz votre cache et vos cookies.

Dans Chrome, cliquez sur la page web avec le bouton droit de la souris, puis cliquez sur Inspecter. Comme dans la capture d’écran ci-dessus, sélectionnez l’onglet *Réseau* pour vue les requêtes effectuées à partir du navigateur.

Dans l’exemple ci-dessus, les balises JS d’Adobe suivantes sont installées sur la page : ECID, AAM, Analytics et Cible.

**Comment voir si Opt-in fonctionne comme prévu ?**

Aucune requête ne doit s’afficher pour les serveurs d’Adobe :

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>Vous devez voir un appel vers `http://dpm.demdex.net/optOutStatus`, un point de terminaison en LECTURE SEULE utilisé pour récupérer l’état de désinscription du visiteur. Ce point de terminaison n’entraîne la création d’aucun cookie tiers et ne collecte aucune information de la page.

Les cookies créés par les balises d’Adobe ne doivent pas s’afficher : (AMCV_{{YOUR_ORG_ID}}, mbox, demdex, s_cc, s_sq, everest_g_v2, everest_session_v2)

Dans Chrome, accédez à l’onglet *Application*, développez la section *Cookies* sous *Enregistrement*, puis sélectionnez le nom de domaine de votre site Web :

![](assets/use_case_1_2.png)

## Cas d’utilisation 2 : Activation d’Opt-in et du stockage  {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

La seule différence avec le cas d’utilisation 2, c’est la présence d’*un nouveau cookie* contenant les autorisations d’Opt-in fournies par votre visiteur : **adobeujs-optin**.

## Cas d’utilisation 3 : Activation d’Opt-in et approbation préalable d’Adobe Analytics   {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

Etant donné que Adobe Analytics est prérenseigné, les demandes de votre serveur de suivi sont affichées dans l’onglet Réseau :

![](assets/use_case_3_1.png)

et vous verrez les cookies Analytics dans l’onglet Application :

![](assets/use_case_3_2.png)

## Cas d’utilisation 4 : Activation d’Opt-in et de l’IAB   {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**Comment vue de votre consentement IAB actuel sur la page :**

Ouvrez les outils de développement et sélectionnez l&#39;onglet *Console*. Collez le fragment de code suivant et appuyez sur Entrée :

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

Voici un exemple de sortie lorsque les fins 1, 2 et 5 sont approuvées et que l’identifiant du fournisseur d’Audience Manager est approuvé :

* demdex.net/id : La présence de cet appel prouve que l&#39;ECID a demandé un identifiant à demdex.net
* demdex.net/event : La présence de cet appel prouve que l&#39;appel de collecte de données du DIL fonctionne comme prévu.
* demdex.net/dest5.html : La présence de cet appel prouve que les synchronisations d’ID sont déclenchées.

![](assets/use_case_4_1.png)

Si l’un des éléments suivants n’est pas valide, aucune requête n’est présentée aux serveurs d’Adobe et aucun cookie d’Adobe n’est affiché :

* Les buts 1, 2 OU 5 ne sont pas approuvés.
* L&#39;ID du fournisseur d&#39;Audience Manager n&#39;est pas approuvé.