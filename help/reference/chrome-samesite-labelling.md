---
title: Modifications de l’étiquetage Google Chrome SameSite
seo-title: Modifications de l’étiquetage Google Chrome SameSite
description: Documentation pour la bibliothèque Adobe ECID (Service d’ID).
seo-description: Documentation pour la bibliothèque Adobe ECID (Service d’ID).
translation-type: tm+mt
source-git-commit: 592ca6ca6a72e57b728e286d0b730c5bd93c0c7b
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 4%

---


# Modifications de l’étiquetage Google Chrome SameSite {#google-chrome-samesite-labelling-changes}

L’attribut Même site indique aux navigateurs quand et comment déclencher des cookies dans les scénarios propriétaires et tiers. L&#39;attribut MêmeSite peut avoir l&#39;une des trois valeurs suivantes : `strict`, `lax`ou `none`. Chrome, Firefox, Edge, Safari et Opera sont pris en charge `strict` et `lax` depuis novembre 2017, alors qu’ `none` il a été introduit en 2018. Cependant, certains navigateurs plus anciens ne prennent pas en charge ce paramètre.

En février 2020, Google a publié Chrome 80 et modifié le paramètre par défaut `none` pour le remplacer par `lax` un cookie sans valeur d’attribut SameSite spécifiée. Ce paramètre empêche l’utilisation d’un cookie dans un contexte tiers, également appelé &quot;cross-site&quot;. Tout cookie tiers qui en résulte doit être défini sur `SameSite=none` et étiqueté comme sécurisé.

Les cookies sans valeur d’attribut SameSite spécifiée sont définis par défaut sur `lax`.

Consultez le document [standard des](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) cookies pour plus d’informations sur les attributs SameSite.

## Valeurs d’attribut SameSite

| Valeur de l’attribut SameSite | Descriptions |
| ------ | ------------ |
| `strict` | Les cookies dotés de ce paramètre ne sont envoyés que lorsque la page de référence et le landing page font tous deux partie du même domaine que le cookie. |
| `lax` | Les cookies dotés de ce paramètre ne sont envoyés que lorsque le domaine affiché dans l’URL du navigateur correspond au domaine du cookie. Il s’agit de la nouvelle valeur par défaut pour les cookies dans Chrome. |
| `none` | Les cookies dotés de ce paramètre sont disponibles pour un accès externe ou tiers, tel que &quot;cross-site&quot;. Avant cette modification, `none` le paramètre Siteidentique était par défaut pour les cookies. L’utilisation de ce paramètre permet donc à un cookie de se comporter de la même manière qu’il fonctionnait traditionnellement. Cependant, Google exige que tout cookie avec ce paramètre spécifie désormais l’indicateur sécurisé, ce qui signifie que le cookie sera créé et envoyé uniquement avec des requêtes via HTTPS. Tous les cookies intersites sans indicateur sécurisé seront rejetés par Google. |

## Ce que vous devez savoir en tant que client Adobe Experience Cloud

**Aucune mise à jour JavaScript n’est requise**

Les produits d’Adobe ont déjà publié des mises à jour côté serveur pour définir des cookies tiers avec les attributs appropriés. Aucune mise à jour de la bibliothèque JavaScript n’est nécessaire pour nos clients.

**Vérifier que les points de terminaison tiers utilisent HTTPS**

Tous les clients doivent confirmer que leur configuration JavaScript utilise HTTPS pour leurs appels aux services d’Adobe. Cible, Audience Manager et ECID (Experience Cloud Identity Service) redirigent les appels HTTP tiers vers leurs points de terminaison HTTPS respectifs, ce qui peut augmenter la latence. Cela signifie que vous n’êtes pas tenu de modifier votre configuration. Les clients Analytics doivent mettre à jour leurs implémentations pour utiliser exclusivement HTTPS, car les redirections spécifiques à Analytics peuvent entraîner une perte de données.

**Les cookies correctement étiquetés doivent collecter les données comme prévu**

Tant que les cookies sont correctement étiquetés, les navigateurs ne prennent aucune mesure pour les bloquer. Les consommateurs auront la possibilité de bloquer certains types de cookies, mais il s’agit actuellement d’un paramètre d’inclusion uniquement.

**Les cookies tiers existants sans les étiquettes mises à jour seront ignorés.**

Les cookies tiers créés avant que Chrome 80 ne commence à appliquer les paramètres Siteidentique=`none` et les indicateurs sécurisés seront ignorés par Chrome 80 si ces indicateurs ne sont pas présents.

La plupart des cookies tiers d’Adobe existants n’ont pas ces indicateurs et devront être mis à jour par les serveurs Edge avant que les utilisateurs ne procèdent à la mise à niveau vers Chrome 80, sans quoi ces cookies seront perdus. La mise à jour des serveurs Edge se produit automatiquement lorsque les utilisateurs visitent n’importe quel site Web où le cookie est utilisé.

La plupart des produits d’Adobe disposent déjà des indicateurs appropriés pour les cookies. Les implémentations d’Analytics qui utilisent la collecte de données tierces et qui n’utilisent pas l’ECID font exception. Les clients peuvent connaître une légère augmentation temporaire du nombre de nouveaux visiteurs qui, autrement, auraient été des visiteurs de retour.

**Diminution possible de la correspondance des cookies pour les partenaires de destination et de marché (Audience Manager uniquement)**

Bien que l’Adobe ait le contrôle de la mise à jour de ses cookies, l’Adobe ne peut pas forcer les partenaires à apporter les modifications nécessaires. La correspondance des cookies peut diminuer pour les clients d’Audience Manager qui utilisent des partenaires de destination ou des partenaires du marché qui n’ont pas effectué ces mises à jour.

**Cookies tiers compatibles avec Analytics (`s_vi`cookies Analytics uniquement)**

Certaines implémentations d’Analytics utilisent un alias CNAME Analytics pour activer la création du `s_vi` cookie dans le domaine de ce CNAME. Si le CNAME se trouve dans le même domaine que votre site Web, il sera désigné comme cookie propriétaire. Cependant, si vous possédez plusieurs domaines et utilisez le même CNAME pour la collecte de données sur tous vos domaines, il sera désigné comme cookie tiers sur ces autres domaines.

En `lax` devenant le nouveau paramètre Site identique par défaut dans Chrome, le CNAME n’est plus visible sur les autres domaines.

Pour tenir compte de la modification, Analytics définit désormais explicitement la valeur MêmeSite du `s_vi` cookie sur `lax`. Pour utiliser ce cookie dans un contexte tiers convivial, définissez la valeur MêmeSite sur `none`, ce qui signifie également que vous devez toujours utiliser HTTPS. Contactez le service à la clientèle pour que la valeur du même site soit modifiée pour vos CNAME sécurisés.

>[!IMPORTANT]
>
>Cette action n’est pas requise pour les clients Analytics utilisant l’ECID, les clients utilisant un CNAME distinct pour chacun de leurs domaines ou les clients utilisant uniquement la collecte de données Analytics tierces.

## Cookies Visiteurs standard Adobe

Seuls les cookies standard du visiteur commun sont répertoriés dans le tableau ci-dessous. Pour obtenir des configurations de cookies supplémentaires, consultez la documentation spécifique au produit ou contactez votre représentant d’Adobe.

### ECID

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Propriétaire direct côté client | Sans valeur ajoutée *Chrome est défini par défaut comme `lax` paramètre | Configurable |
| AMCVS_###@AdobeOrg | Propriétaire direct côté client | Sans valeur ajoutée *Chrome est défini par défaut comme `lax` paramètre | Configurable |
| s_ecid | Propriétaire côté serveur | SameSite==`lax` | Non défini |

### Audience Manager

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Troisième niveau | `none` | Défini sur sécurisé |
| Dextp | Troisième niveau | `none` | Défini sur sécurisé |

### Analytics

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Propriétaire côté serveur en cas d’utilisation `CNAME` </li> <li>Tiers si vous utilisez 2o7.net ou omtrdc.net</li></ul> | <ul><li>`lax` if first-party</li> <li>`none` si tiers</li></ul> *Les clients peuvent modifier le paramètre par le biais du ticket du service d’assistance clientèle pour les domaines propriétaires* | Défini, en cas d’utilisation `none` et de demande HTTPS |
| s_fid | Propriétaire direct côté client | Aucune valeur ajoutée *Chrome est défini par défaut comme `lax` paramètre | Non défini |

### Target

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Premier niveau | Sans valeur ajoutée *Chrome est défini par défaut comme `lax` paramètre | Non défini |

### ad cloud

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Troisième niveau | `none` *Uniquement sur les navigateurs Google Chrome et Chrome* | Défini, en cas d’utilisation `none` et de demande HTTPS |
| data_adcloud | Premier niveau | Sans valeur ajoutée *Chrome est défini par défaut comme `lax` paramètre | Non défini |
| ev_tm | Troisième niveau | `none` *Uniquement sur les navigateurs Google Chrome et Chrome* | Défini, en cas d’utilisation `none` et de demande HTTPS |

### Bizible

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Troisième niveau | `none` | Sécurisé |

### Marketo Munchkin

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Propriétaire direct côté client | Sans valeur ajoutée *Chrome est défini par défaut comme `lax` paramètre | Configurable pour les pages externes |

> !![IMPORTANT] Les cookies tiers Adobes sont définis côté serveur.

Pour plus d’informations, voir le document sur les stratégies [](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html)Google Chrome SameSite de la Cible.