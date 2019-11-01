---
description: Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation du service d’ID.
keywords: Service d’identification
seo-description: Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation du service d’ID.
seo-title: FAQ sur le service d’ID
title: FAQ sur le service d’ID
uuid: e8d8f819-3d73-4fa2-864c-4867071c14ee
translation-type: tm+mt
source-git-commit: c4c0b791230422f17292b72fd45ba5689a60adae

---


# FAQ sur le service d’ID{#id-service-faqs}

Questions fréquemment posées sur les fonctionnalités et problèmes liés à l’utilisation du service d’ID.

## Fonction {#section-659e89f8b9a74cb8afff35587dc96836}

**Quel type de fonctions ou de fonctionnalités le service d’ID fournit-il ?**

Voir [Aperçu](../introduction/overview.md).

**Pourquoi le service d’ID n’effectue-t-il pas d’appel pour récupérer l’Experience Cloud ID ?**

Ce problème peut être difficile à diagnostiquer. Vous pouvez néanmoins vérifier les en-têtes de stratégie de sécurité du contenu de votre site. Si votre stratégie de sécurité est stricte, ces paramètres peuvent bloquer les appels tiers effectués par le service d’ID. Voir [Stratégies de sécurité du contenu et service Experience Cloud Identity](../reference/csp.md#concept-968c423a7392479db0a0d821ae9783e3)

**Stockage du fichier VisitorAPI.js**

Vous pouvez rencontrer des problèmes si vous hébergez le fichier VisitorAPI.js comme fichier local dans des applications mobiles. Nous vous recommandons d’héberger le fichier sur un serveur web.

## Temps de chargement des pages et latence {#section-c78e148d8dbe4c77a436ef0f2af5434b}

**Comment le placement de la bibliothèque VisitorAPI.js du service d’ID affecte-t-il le temps de chargement des pages ?**

Placez la bibliothèque VisitorAPI.js dans la partie supérieure de la page, dans la `<head>` section d’en-tête du code. Vous pouvez ainsi vous assurer que l’appel d’un ID disparaît avant que le corps de la page ne commence à se charger. Cela maximise les chances de réussite d’un renvoi d’ID.

L’appel du service d’ID est asynchrone et est le seul appel au [domaine demdex.net](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html). L’appel du service d’ID ne bloque pas le chargement d’autres éléments sur la page.

Pour les [!DNL Target] clients, le placement du code du service d’ID dans le corps `<body>` de la page peut augmenter les risques qu’il puisse bloquer un appel [!DNL Target]. Si vous devez placer le code du service d’ID dans le corps de votre page, il doit être placé après la balise `<body>` ouverte.

**Le service d’ID effectue-t-il un appel au serveur à chaque chargement de page ?**

Non, cet appel n’a lieu que la première fois que la page est affichée et une fois tous les 7 jours par la suite. Pendant ce temps, les appels au serveur ne sont pas requis. Le service d’ID fonctionne en mode côté client et n’a pas besoin d’effectuer un appel au serveur pour renvoyer un ID.

Voir [Aperçu](../introduction/overview.md).

**Lorsque vous utilisez le service d’ID, qu’est-ce qui peut ralentir le chargement des pages ou affecter l’expérience de l’utilisateur ?**

Il est difficile de recenser toutes les causes possibles. Des milliards de clients se connectent à nos services et la grande diversité en termes d’emplacement et de mode de connexion affecte les performances. Par exemple :

* Les vitesses varient considérablement sur les réseaux mobiles. Ces réseaux souffrent également de pertes de signaux et de données ou de paquets vocaux.
* La connectivité est instable sur les appareils se connectant au Wi-Fi dans diverses conditions. Par exemple, les problèmes de perte de paquets et de vitesse sont courants dans les lieux publics comme les cafés ou dans d’autres environnements tels que les avions où les paquets doivent rebondir à travers un satellite avant d’atteindre les réseaux terrestres.
* Des réseaux locaux mal configurés peuvent avoir un impact négatif sur la connectivité et la vitesse.
* Les appareils des clients peuvent avoir leurs propres problèmes, tels qu’une mémoire insuffisante, un basculement excessif du disque ou une puissance limitée du processeur par rapport aux charges de travail actuelles.
* Les navigateurs mettent en file d’attente et exécutent des appels au serveur à distance et traitent même les réponses avec des règles différentes, selon le fabricant et la version du navigateur. Ce comportement affecte la vitesse et les performances.

**Pouvez-vous citer quelques améliorations apportées permettant de raccourcir le temps de chargement des pages ?**

Par exemple, la production de threads. Nous avons introduit la production de threads en cas de plusieurs requêtes de synchronisation des identifiants. Nous avons observé à partir de rapports de laboratoire que, pour les clients effectuant plusieurs synchronisations des identifiants, l’interface utilisateur serait bloquée en raison des nombreux calculs en continu utilisant le processeur. Par conséquent, nous avons introduit la production de threads pour séparer les requêtes de synchronisation des identifiants de 100 ms chacune.

Il en résultera de meilleures performances pour les utilisateurs se servant de Visitor version 2.3.0 et ultérieure et de DIL version 6.10 et ultérieure. Les améliorations du temps de chargement des pages sont indiquées dans la figure ci-dessous :

![](assets/id_sync_improvements_copy.png)

**Les requêtes de navigateur utilisant CORS à la place de JSONP affectent-elles les performances des pages ?**

Les requêtes de ressources utilisant la norme CORS sont généralement préférables à celles utilisant JSONP. Avec JSONP, certains navigateurs mettent en file d’attente et annulent la priorité des requêtes relatives à d’autres appels synchrones et asynchrones sur la page. La norme CORS permet de s’assurer que ces requêtes sont traitées avec une priorité plus élevée dans la pile d’appels du navigateur.

Voir [Prise en charge de la norme CORS dans le service Experience Cloud Identity](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

## Sécurité {#section-b176b8492fbe4acfb79ebb30ec902f98}

**Le service d’ID prend-il en charge la norme CORS ?**

Oui. Voir [Prise en charge de la norme CORS dans le service Experience Cloud Identity](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Qu’est-ce que la norme CORS ?**

*`Cross-Origin Resource Sharing`*(Cross-Origin Resource Sharing) ou CORS est une méthode que les navigateurs utilisent pour demander des ressources. Le service d’ID continue de demander des ressources au moyen de la norme CORS dans les navigateurs qui la prennent en charge. Le service d’ID demande des ressources au moyen de JSONP dans les anciens navigateurs qui ne prennent pas en charge la norme CORS. Voir [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758).

**Que faire si mes exigences en matière de sécurité sont si strictes que je ne souhaite jamais utiliser JSONP ?**

Si vos exigences en matière de sécurité sont strictes, définissez la configuration de l’API du service d’ID sur `useCORSOnly: true`. Il est recommandé de n’activer ce mode que si vous pensez que vos visiteurs utilisent des navigateurs qui prennent en charge la norme CORS.

Voir [Experience Cloud](../reference/cors.md#concept-6c280446990d46d88ba9da15d2dcc758) et [useCORSOnly](../library/function-vars/use-cors-only.md#reference-8a9a143d838b48d6b23329b84b13e1fa).

>[!MORELIKETHIS]
>
>* [Assistance clientèle](https://helpx.adobe.com/marketing-cloud/contact-support.html)

