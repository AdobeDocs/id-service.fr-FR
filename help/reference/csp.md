---
description: Une politique de sécurité de contenu (CSP) est une fonction d’en-tête et de sécurité HTTP qui permet aux navigateurs de contrôler le type de ressources chargées sur une page Web. Consultez cette section si vous utilisez le service d’ID et disposez de CSP strictes qui utilisent des places sur la liste autorisée pour accepter des ressources provenant de domaines de confiance. Vous devez ajouter les domaines Adobe répertoriés ici à vos places sur la liste autorisée CSP.
keywords: Service d’ID
title: Politiques de sécurité du contenu et service d’identités d’Experience Cloud
exl-id: e35c6809-764e-4c3e-9139-88bb92e82338
source-git-commit: c56bbaa6a3639e421c11a8231e14afb58a4fa305
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Politiques de sécurité du contenu et service Experience Cloud Identity {#content-security-policies-and-the-experience-cloud-id-service}

Une politique de sécurité de contenu (CSP) est une fonction d’en-tête et de sécurité HTTP qui permet aux navigateurs de contrôler le type de ressources chargées sur une page Web. Consultez cette section si vous utilisez le service d’ID et disposez de CSP strictes qui utilisent des places sur la liste autorisée pour accepter des ressources provenant de domaines de confiance. Vous devez ajouter les domaines Adobe répertoriés ici à vos places sur la liste autorisée CSP.

## Présentation des stratégies de sécurité du contenu {#section-5fde5c00a678455c914b8307a8caab82}

Les stratégies de sécurité du contenu utilisent l’en-tête HTTP `Content-Security-Policy` pour contrôler le type de ressources qu’un navigateur accepte ou charge sur une page. L’application d’un fichier CSP peut vous aider à empêcher :

* Les fichiers JavaScript ne se chargent pas si la source est inconnue ou n’est pas incluse dans une liste autorisée.
* Les attaques de type Cross-site scripting (XXS).
* Les attaques d’injection de données.
* Les attaques de défacement de site.
* La distribution de programmes malveillants.

L’utilisation des CSP est courante et bien comprise. La présente documentation n’a pas pour but d’expliquer en détail les CSP (voir les liens d’information connexes ci-dessous pour plus d’informations). Il est important de comprendre les noms de domaine Adobe que vous devez ajouter à un fichier CSP si vous les utilisez et si vous disposez de politiques de sécurité rigoureuses. L’ajout de ces domaines permet aux navigateurs visiteurs qui accèdent à votre site d’effectuer ces appels importants vers les ressources Experience Cloud que vous utilisez.

## Domaines Experience Cloud pour la Liste autorisée {#section-30693e9a96834edfbf04de9e698cf2aa}

Ajoutez ces noms de domaine ou URL à votre fournisseur de services de messagerie instantanée pour chaque solution ou service Experience Cloud de liste que vous utilisez.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C">
 <thead>
  <tr>
   <th colname="col1" class="entry">Solution ou service Experience Cloud</th>
   <th colname="col2" class="entry">Description</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1">
    <p><b>AppMeasurement</b></p>
   </td>
   <td colname="col2">
    <p>Modifiez votre CSP afin d’inclure les domaines ci-dessous :</p>
    <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B">
     <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"><span class="codeph">*.2o7.net</span></li>
     <li id="li_4B12A283716746949201528CD6AF529E"><span class="codeph">*.omtrdc.net</span></li>
    </ul>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Cible</b></p>
   </td>
   <td colname="col2">
    <p>Modifiez votre CSP afin d’inclure <span class="codeph">*.tt.omtrdc.net</span>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Experience Cloud ID_Service et Audience Manager</b></p>
   </td>
   <td colname="col2">
    <p>Modifiez votre stratégie de sécurité du contenu afin d’inclure les domaines ci-dessous :</p>
    <ul>
     <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
     <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
     <li>Si vous utilisez Adobe Launch pour déployer des balises, vous devez également ajouter <code>https://assets.adobedtm.com</code> à la liste des domaines.</li>
    </ul>
    <p>Les appels au domaine <span class="codeph">demdex.net</span> sont utilisés pour générer les <a href="../introduction/cookies.md" format="dita" scope="local">cookies et Experience Cloud ID_Service</a> et pour les synchronisations d’ID. Voir également la section <a href="https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=fr" format="https" scope="external">Comprendre les appels vers le domaine Demdex</a>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Plug-in Activity Map</b></p>
   </td>
   <td colname="col2">
    <p>Modifiez votre stratégie de sécurité du contenu afin d’inclure *.adobe.com. **Remarque** : si Activity Map était déjà installé avant janvier 2020, votre navigateur verra toujours une requête initiale vers *.omniture.com, mais il sera redirigé vers *.adobe.com.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Advertising Analytics</b></p>
   </td>
   <td colname="col2">
    <p>Si vous restreignez les paramètres de chaîne de requête, puis placez sur la liste autorisée les paramètres suivants :</p>
    <ul>
     <li><code>s_kwcid</code> (qui utilise <code>!</code>)</li>
     <li><code>ef_id</code> (qui utilise <code>:</code>)</li>
    </ul>
    <p>Si vous bloquez le caractère <code>!</code> dans les URL, alors vous pouvez également le placer sur la liste autorisée.</p>
    <p>Advertising Analytics utilise uniquement <code>s_kwcid</code>, mais Advertising Search, Social et Commerce et Advertising DSP utilisent également <code>ef_id</code>.</p>
   </td>
  </tr>
  <tr>
   <td colname="col1">
    <p><b>Adobe Advertising</b></p>
   </td>
   <td colname="col2">
    <p>Modifiez votre CSP afin d’inclure les domaines suivants :</p>
    <ul>
     <li><code>.everestjs.net</code></li>
     <li><code>.everesttech.net</code></li>
    </ul>
   </td>
  </tr>
 </tbody>
</table>

>[!MORELIKETHIS]
>
>* [Référence des politiques de sécurité du contenu](https://content-security-policy.com/)
>* [MDN : Politique de sécurité du contenu](https://developer.mozilla.org/fr/docs/Web/HTTP/CSP)
>* [Wikipédia : Politique de sécurité du contenu](https://fr.wikipedia.org/wiki/Content_Security_Policy)
