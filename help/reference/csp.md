---
description: Une stratégie de sécurité du contenu (Content Security Policy, CSP) est un en-tête HTTP et une fonction de sécurité qui permet aux navigateurs de contrôler le type de ressources chargées sur une page web. Passez en revue cette section si vous utilisez le service d’ID ainsi que des stratégies de sécurité du contenu strictes utilisant des listes blanches pour accepter des ressources provenant de domaines de confiance. Vous devez ajouter les domaines Adobe répertoriés dans cette section à vos listes blanches de stratégie de sécurité du contenu.
keywords: ID Service
seo-description: Une stratégie de sécurité du contenu (Content Security Policy, CSP) est un en-tête HTTP et une fonction de sécurité qui permet aux navigateurs de contrôler le type de ressources chargées sur une page web. Passez en revue cette section si vous utilisez le service d’ID ainsi que des stratégies de sécurité du contenu strictes utilisant des listes blanches pour accepter des ressources provenant de domaines de confiance. Vous devez ajouter les domaines Adobe répertoriés dans cette section à vos listes blanches de stratégie de sécurité du contenu.
seo-title: Stratégies de sécurité du contenu et service Experience Cloud Identity
title: Stratégies de sécurité du contenu et service Experience Cloud Identity
uuid: 7399edf3-01c1-4730-834e-e2dd2c5791ff
translation-type: ht
source-git-commit: 7255228470a59a537251c3a3eec686f52a2b76ec

---


# Stratégies de sécurité du contenu et service Experience Cloud Identity {#content-security-policies-and-the-experience-cloud-id-service}

Une stratégie de sécurité du contenu (Content Security Policy, CSP) est un en-tête HTTP et une fonction de sécurité qui permet aux navigateurs de contrôler le type de ressources chargées sur une page web. Passez en revue cette section si vous utilisez le service d’ID ainsi que des stratégies de sécurité du contenu strictes utilisant des listes blanches pour accepter des ressources provenant de domaines de confiance. Vous devez ajouter les domaines Adobe répertoriés dans cette section à vos listes blanches de stratégie de sécurité du contenu.

## Présentation des stratégies de sécurité du contenu {#section-5fde5c00a678455c914b8307a8caab82}

Les stratégies de sécurité du contenu utilisent l’en-tête HTTP `Content-Security-Policy` pour contrôler le type de ressources qu’un navigateur accepte ou charge sur une page. L’application d’une stratégie de sécurité du contenu peut vous aider à éviter :

* le chargement de fichiers JavaScript si la source est inconnue ou non incluse dans la liste blanche ;
* les attaques de type cross-site scripting (XXS) ;
* les attaques par injection de données ;
* les attaques de dégradation de site ;
* la diffusion de logiciels malveillants.

L’utilisation des stratégies de sécurité du contenu est courante et bien comprise. Cette documentation n’a pas pour objectif d’expliquer les stratégies de sécurité du contenu en détail (voir les liens d’information connexes ci-dessous pour plus d’informations). L’important est de connaître les noms de domaine Adobe que vous devez ajouter à une stratégie de sécurité du contenu si vous utilisez ces stratégies et que vous disposez de règles de sécurité strictes. L’ajout de ces domaines permet aux navigateurs des visiteurs accédant à votre site d’effectuer ces appels importants vers les ressources d’Experience Cloud que vous utilisez.

## Domaines Experience Cloud en liste blanche {#section-30693e9a96834edfbf04de9e698cf2aa}

Ajoutez les noms de domaine ou URL suivants à votre stratégie de sécurité du contenu pour chaque solution ou service Experience Cloud que vous utilisez.

<table id="table_EC9FC999A62D4B7A830CE73B0AB9EF3C"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Solution ou service Experience Cloud </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>AppMeasurement</b> </p> </td> 
   <td colname="col2"> <p>Modifiez votre stratégie de sécurité du contenu afin d’inclure les éléments suivants : </p> <p> 
     <ul id="ul_7522AE83A03A4115A84DF5B32D6DD79B"> 
      <li id="li_AB1EC161FB154BEDA1BEFE76C8A38A90"> <span class="codeph"> *.2o7.net</span> </li> 
      <li id="li_4B12A283716746949201528CD6AF529E"> <span class="codeph"> *.omtrdc.net</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Target</b> </p> </td> 
   <td colname="col2"> <p>Modifiez votre stratégie de sécurité du contenu afin d’inclure <span class="codeph">*.tt.omtrdc.net</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Service Experience Cloud ID et Audience Manager</b> </p> </td> 
   <td colname="col2"> <p>Modifiez votre stratégie de sécurité du contenu afin d’inclure les domaines ci-dessous :</p> 
   <p><ul>
   <li>connect-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>img-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>script-src 'self' <code>https://*.demdex.net https://cm.everesttech.net https://assets.adobedtm.com;</code></li>
   <li>frame-src 'self' <code>https://*.demdex.net;</code></li>
   <li>Si vous utilisez Adobe Launch pour déployer des balises, vous devez également ajouter <code>https://assets.adobedtm.com</code> à la liste des domaines.</li></ul></p> <p>Les appels au domaine <span class="codeph"> demdex.net</span> sont utilisés pour générer les <a href="../introduction/cookies.md" format="dita" scope="local"> cookies et le service Experience Cloud Identity</a>, ainsi que pour les synchronisations des identifiants. Voir également <a href="https://docs.adobe.com/content/help/fr-FR/audience-manager/user-guide/reference/demdex-calls.translate.html" format="https" scope="external"> Signification des appels vers le domaine Demdex</a>. </p> </td> </tr> 
 <tr>
 <td colname="col1"> <p> <b>Module externe Activity Map</b> </p> </td> 
 <td colname="col2"> <p>Modifiez votre stratégie de sécurité du contenu afin d’inclure *.adobe.com. **Remarque** : si Activity Map était déjà installé avant janvier 2020, votre navigateur verra toujours une requête initiale vers *.omniture.com, mais il sera redirigé vers *.adobe.com. </p></td> 
 </tr>
 </tbody> 
</table>

>[!MORELIKETHIS]
>* [Référence des stratégies de sécurité du contenu](https://content-security-policy.com/)
>* [MDN : Stratégie de sécurité du contenu](https://developer.mozilla.org/fr/docs/Web/HTTP/CSP)
>* [Wikipédia : Stratégie de sécurité du contenu](https://fr.wikipedia.org/wiki/Content_Security_Policy)

