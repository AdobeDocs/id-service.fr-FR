---
description: Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation du service d’ID.
keywords: Service d’ID
title: FAQ sur le service d’ID
exl-id: 4dd2220c-8a9d-4e27-838b-be5ad357cb3e
source-git-commit: cb89ac70e37f35d5e4e2b971f2df9645304522f8
workflow-type: ht
source-wordcount: '787'
ht-degree: 100%

---

# FAQ sur le service d’ID {#id-service-faqs}

Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation du service d’ID.

## Fonction {#section-659e89f8b9a74cb8afff35587dc96836}

**Quel type de fonctions ou de fonctionnalités le service d’ID fournit-il ?**

Voir [Aperçu](../introduction/overview.md).

**Pourquoi le service d’ID ne lance-t-il pas d’appel pour récupérer l’Experience Cloud ID ?**

Cela peut être difficile à diagnostiquer. Vous pouvez notamment vérifier les en-têtes de stratégie de sécurité de contenu de votre site. Si vous avez une stratégie de sécurité stricte, ces paramètres peuvent bloquer les appels tiers effectués par le service d’ID. Voir la section [Stratégies de sécurité du contenu et service Experience Cloud Identity](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3)

**Enregistrement de fichier VisitorAPI.js**

Vous pouvez rencontrer des problèmes si vous hébergez le fichier VisitorAPI.js comme fichier local dans des applications mobiles. Nous vous recommandons d’héberger le fichier sur un serveur Web.

## Temps de chargement des pages et latence {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Comment le placement de la bibliothèque VisitorAPI.js du service d’ID affecte-t-il le temps de chargement des pages ?**

Placez la bibliothèque VisitorAPI.js dans la partie supérieure de la page, dans la `<head>` section d’en-tête du code. Vous pouvez ainsi vous assurer que l’appel d’un ID disparaît avant que le corps de la page ne commence à se charger. Cela maximise les chances de réussite d’un renvoi d’ID.

L’appel du service d’ID est asynchrone et est le seul appel au [domaine demdex.net](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=fr). L’appel du service d’ID ne bloque pas le chargement d’autres éléments sur la page.

Pour les [!DNL Target] clients, le placement du code du service d’ID dans le corps `<body>` de la page peut augmenter les risques qu’il puisse bloquer un appel [!DNL Target]. Si vous devez placer le code du service d’ID dans le corps de votre page, il doit être placé après la balise `<body>` ouverte.

**Le service d’ID lance-t-il un appel serveur à chaque chargement de page ?**

Non, cet appel ne se produit que lors du premier rendu de la page et une fois tous les 7 jours par la suite. En attendant, les appels au serveur ne sont pas requis. Le service d’ID fonctionne en mode côté client et n’a pas besoin d’effectuer un appel serveur pour renvoyer un identifiant.

Voir [Aperçu](../introduction/overview.md).

**Lors de l’utilisation du service d’ID, qu’est-ce qui peut ralentir le chargement des pages ou affecter l’expérience de l’utilisateur ?**

Il est difficile de cataloguer toutes les conditions possibles. Des milliards de clients finaux se connectent à nos services et la grande variété d’endroits et de méthodes utilisés pour ces connexions affecte les performances. Par exemple :

* Les vitesses varient considérablement sur les réseaux mobiles. Ces réseaux souffrent également de pertes de signal et de données ou de paquets vocaux.
* La connectivité souffre sur les appareils connectés par WiFi dans diverses conditions. Par exemple, les problèmes de perte de paquets et de vitesse sont fréquents dans les lieux publics comme les cafés ou dans d’autres environnements comme les avions où les paquets doivent rebondir par satellite avant d’atteindre les réseaux terrestres.
* Les réseaux locaux mal configurés peuvent avoir un impact négatif sur la connectivité et la vitesse.
* Les périphériques clients peuvent rencontrer leurs propres problèmes, tels qu’une faible mémoire, un échange de disque excessif ou une puissance CPU limitée par rapport aux charges de travail actuelles.
* Les navigateurs mettent en file d’attente et exécutent les appels de serveur distant et traitent même les réponses avec des règles différentes, selon le fabricant et la version du navigateur. Ce comportement affecte la vitesse et les performances.

**Pouvez-vous nommer certaines améliorations apportées pour raccourcir les temps de chargement de page ?**

Par exemple, la méthode dite du thread yielding. Nous avons introduit le thread yielding des résultats en cas de plusieurs demandes de synchronisation d’ID. Nous avons observé dans des rapports de laboratoire que pour les clients qui effectuent plusieurs synchronisations d’identifiants, l’interface utilisateur avait tendance à se bloquer en raison des nombreux calculs incessants effectués par le processeur. En conséquence, nous avons introduit le thread yielding permettant de séparer les requêtes de synchronisation des identifiants de 100 msec chacune.

Cette modification améliore les performances des clients utilisant Visitor 2.3.0+ et DIL 6.10+. Les améliorations des temps de chargement des pages sont illustrées dans la figure ci-dessous :

![](assets/id_sync_improvements_copy.png)

**Les requêtes de navigateur utilisant CORS ou JSON-P affectent-elles les performances des pages ?**

Les demandes de ressources avec CORS sont généralement préférables à celles effectuées avec JSONP. Avec JSONP, certains navigateurs mettent en file d’attente et dépriorisent les requêtes par rapport à d’autres appels synchrones et asynchrones sur la page. CORS permet de s’assurer que ces requêtes sont traitées avec une priorité plus élevée dans la pile d’appels du navigateur.

Voir [Prise en charge de la norme CORS dans le service Experience Cloud Identity](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Sécurité {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Le service d’ID prend-il en charge CORS ?**

Oui. Voir [Prise en charge de la norme CORS dans le service Experience Cloud Identity](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Qu’est-ce que la norme CORS ?**

*`Cross-Origin Resource Sharing`*(Cross-Origin Resource Sharing) ou CORS est une méthode que les navigateurs utilisent pour demander des ressources. Le service d’ID demande toujours des ressources à l’aide de CORS dans les navigateurs qui les prennent en charge. Le service d’ID demande des ressources avec JSON-P dans les navigateurs plus anciens qui ne prennent pas en charge CORS. Voir [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Que faire si mes exigences en matière de sécurité sont si strictes que je ne souhaite jamais utiliser JSONP ?**

Si vos exigences en matière de sécurité sont strictes, définissez la configuration de l’API du service d’ID sur `useCORSOnly: true`. Vous ne devez activer ce mode que si vous êtes certain que les visiteurs de votre site utilisent des navigateurs qui prennent en charge CORS.

Voir les sections [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) et [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Assistance clientèle](https://helpx.adobe.com/fr/marketing-cloud/contact-support.html)

