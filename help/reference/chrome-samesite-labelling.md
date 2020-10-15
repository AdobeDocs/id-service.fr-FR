---
title: Modifications de l’étiquetage SameSite de Google Chrome
seo-title: Modifications de l’étiquetage SameSite de Google Chrome
description: Documentation pour la bibliothèque Adobe ECID (Service d’ID).
seo-description: Documentation pour la bibliothèque Adobe ECID (Service d’ID).
translation-type: ht
source-git-commit: 592ca6ca6a72e57b728e286d0b730c5bd93c0c7b
workflow-type: ht
source-wordcount: '1079'
ht-degree: 100%

---


# Modifications de l’étiquetage SameSite de Google Chrome {#google-chrome-samesite-labelling-changes}

L’attribut SameSite indique aux navigateurs à quel moment et de quelle manière déclencher des cookies dans les scénarios propriétaires et tiers. L’attribut SameSite peut avoir l’une des trois valeurs suivantes : `strict`, `lax` ou `none`. Chrome, Firefox, Edge, Safari et Opera prennent en charge `strict` et `lax` depuis novembre 2017, tandis que `none` a été introduit en 2018. Cependant, certains navigateurs plus anciens ne prennent pas en charge ce paramètre.

En février 2020, Google a lancé Chrome 80 et remplacé le paramètre par défaut `none` par `lax` lorsqu’un cookie n’a pas de valeur d’attribut SameSite spécifiée. Ce paramètre empêche l’utilisation d’un cookie sur un site tiers, également connu sous l’appellation « intersite ». Tout cookie tiers qui en résulte doit être défini sur `SameSite=none` et étiqueté comme étant sécurisé.

Les cookies sans valeur d’attribut SameSite spécifiée sont définis par défaut sur `lax`.

Consultez le [document portant sur les normes des cookies](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1) pour plus d’informations sur les attributs SameSite.

## Valeurs d’attribut SameSite

| Valeur d’attribut SameSite | Descriptions |
| ------ | ------------ |
| `strict` | Les cookies comprenant ce paramètre sont uniquement envoyés lorsque la page de référence et la page de destination font toutes deux partie du même domaine que le cookie. |
| `lax` | Les cookies comprenant ce paramètre sont uniquement envoyés lorsque le domaine affiché dans l’URL du navigateur correspond au domaine du cookie. Cela constitue le nouveau réglage par défaut des cookies dans Chrome. |
| `none` | Les cookies comprenant ce paramètre sont disponibles pour un accès externe ou tiers, tel que les accès « intersites ». Avant cette modification, le paramètre SameSite par défaut pour les cookies était `none`. L’utilisation de ce paramètre permet donc de conserver l’ancien comportement d’un cookie presque à l’identique. Cependant, Google exige que tout cookie comprenant ce paramètre affiche désormais l’indicateur « sécurisé ». Cela signifie que le cookie sera uniquement créé et envoyé avec des requêtes par HTTPS. Tous les cookies intersites ne présentant pas l’indicateur « sécurisé » seront rejetés par Google. |

## Ce que vous devez savoir en tant que client Adobe Experience Cloud

**Aucune mise à jour JavaScript requise**

Les produits Adobe ont déjà publié des mises à jour côté serveur pour définir les cookies tiers avec les attributs appropriés. Nos clients n’ont pas besoin d’effectuer une mise à jour de la bibliothèque JavaScript.

**S’assurer que les points d’entrée tiers utilisent HTTPS**

Tous les clients doivent confirmer que leur configuration JavaScript utilise HTTPS pour leurs appels aux services Adobe. Target, Audience Manager et le service d’identités Experience Cloud (ECID) redirigent les appels HTTP tiers vers leurs points d’entrée HTTPS respectifs, ce qui peut augmenter la latence. Cela signifie que vous n’êtes pas contraint de modifier votre configuration. Les clients Analytics doivent mettre à jour leurs implémentations pour utiliser exclusivement HTTPS, car les redirections spécifiques à Analytics peuvent entraîner une perte de données.

**Les cookies correctement étiquetés devraient collecter les données comme prévu**

Tant que les cookies sont correctement étiquetés, les navigateurs ne prennent aucune mesure pour les bloquer. Les clients auront la possibilité de bloquer certains types de cookies, mais il semblerait qu’il s’agisse pour le moment uniquement d’une option devant être sélectionnée manuellement.

**Les cookies tiers existants sans étiquettes à jour seront ignorés.**

Les cookies tiers créés avant que Chrome 80 ne commence à appliquer les paramètres SameSite=`none` et les indicateurs « sécurisé » seront ignorés par Chrome 80 si ces indicateurs sont absents.

La plupart des cookies tiers d’Adobe existants ne possèdent pas ces indicateurs et devront être mis à jour par les serveurs Edge avant que les utilisateurs ne procèdent à la mise à niveau vers Chrome 80, sans quoi ces cookies seront perdus. La mise à jour des serveurs Edge est automatique lorsque les utilisateurs visitent n’importe quel site web où le cookie est utilisé.

La plupart des produits Adobe ont déjà attribué les indicateurs appropriés aux cookies. Les implémentations d’Analytics qui emploient la collecte de données tierces et n’utilisent pas ECID constituent les seules exceptions. Il se peut que les clients connaissent une légère augmentation temporaire du nombre de nouveaux visiteurs qui auraient été autrement des visiteurs récurrents.

**Diminution possible de la correspondance des cookies pour les partenaires de Destination et de Marketplace (Audience Manager uniquement)**

Bien qu’Adobe décide de la mise à jour de ses cookies, Adobe ne peut pas obliger les partenaires à apporter les modifications nécessaires. La correspondance des cookies peut diminuer pour les clients Audience Manager qui utilisent des partenaires de Destination ou des partenaires de Marketplace qui n’ont pas effectué ces mises à jour.

**Cookies tiers compatibles avec Analytics (cookies `s_vi` Analytics uniquement)**

Certaines implémentations d’Analytics utilisent un pseudonyme CNAME Analytics pour activer la création du cookie `s_vi` dans le domaine de ce CNAME. Si le CNAME se trouve dans le même domaine que votre site web, il sera désigné comme cookie propriétaire. Cependant, si vous possédez plusieurs domaines et utilisez le même CNAME pour la collecte de données sur tous vos domaines, il sera désigné comme un cookie tiers sur ces autres domaines.

Lorsque `lax` devient le nouveau paramètre SameSite par défaut dans Chrome, le CNAME n’est plus visible sur les autres domaines.

Pour tenir compte du changement, Analytics définit désormais explicitement la valeur SameSite du cookie `s_vi` sur `lax`. Pour utiliser ce cookie dans un contexte tiers compatible, définissez la valeur SameSite sur `none` : cela signifie également que vous devez toujours utiliser HTTPS. Contactez l’assistance clientèle pour que la valeur SameSite soit modifiée pour vos CNAME sécurisés.

>[!IMPORTANT]
>
>Cette action n’est pas requise pour les clients Analytics utilisant l’ECID, les clients utilisant un CNAME distinct pour chacun de leurs domaines ou les clients utilisant uniquement la collecte de données Analytics tierce.

## Cookies standards des visiteurs Adobe

Seuls les cookies standards du visiteur communs sont répertoriés dans le tableau ci-dessous. Pour obtenir des configurations de cookies supplémentaires, consultez la documentation spécifique au produit ou prenez contact avec votre représentant Adobe.

### ECID

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| AMCV_###@AdobeOrg | Propriétaire côté client | Aucune valeur ajoutée *Chrome opte par défaut pour le paramètre `lax` | Configurable |
| AMCVS_###@AdobeOrg | Propriétaire côté client | Aucune valeur ajoutée *Chrome opte par défaut pour le paramètre `lax` | Configurable |
| s_ecid | Propriétaire côté serveur | SameSite==`lax` | Non défini |

### Audience Manager

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| Demdex | Troisième niveau | `none` | Défini sur sécurisé |
| Dextp | Troisième niveau | `none` | Défini sur sécurisé |

### Analytics

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| s_vi | <ul><li> Propriétaire côté serveur en cas d’utilisation de `CNAME` </li> <li>Tiers en cas d’utilisation de 2o7.net ou omtrdc.net</li></ul> | <ul><li>`lax` si propriétaire</li> <li>`none` si tiers</li></ul> *Les clients peuvent modifier le paramètre à l’aide d’un ticket provenant de l’assistance clientèle pour les domaines propriétaires* | Défini, en cas d’utilisation de `none` et d’une demande HTTPS |
| s_fid | Propriétaire côté client | Aucune valeur ajoutée *Chrome opte par défaut pour le paramètre `lax` | Non défini |

### Target

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| mbox | Premier niveau | Aucune valeur ajoutée *Chrome opte par défaut pour le paramètre `lax` | Non défini |

### Ad Cloud

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| everest_g_v2 | Troisième niveau | `none` *Uniquement sur les navigateurs Google Chrome et Chromium* | Défini, en cas d’utilisation de `none` et d’une demande HTTPS |
| data_adcloud | Premier niveau | Aucune valeur ajoutée *Chrome opte par défaut pour le paramètre `lax` | Non défini |
| ev_tm | Troisième niveau | `none` *Uniquement sur les navigateurs Google Chrome et Chromium* | Défini, en cas d’utilisation de `none` et d’une demande HTTPS |

### Bizible

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| _buid | Troisième niveau | `none` | Sécurisé |

### Marketo Munchkin

| Cookie | Type | Attribut SameSite | Attribut sécurisé |
| ------ | ---- | ------------------ | ---------------- |
| _mkto_trk | Propriétaire côté client | Aucune valeur ajoutée *Chrome opte par défaut pour le paramètre `lax` | Configurable pour les pages externes |

> !![IMPORTANT] Les cookies tiers Adobes sont définis côté serveur.

Pour plus d’informations, voir le document concernant les [stratégies de Google Chrome concernant SameSite pour Target](https://docs.adobe.com/content/help/fr-FR/target/using/implement-target/before-implement/privacy/google-chrome-samesite-cookie-policies.html).