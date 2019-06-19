---
description: Cette section présente comment le service d'identité de Platform Platform fonctionne avec l'Analytics ID hérité.
keywords: Service d’identification
seo-description: Cette section présente comment le service d'identité de Platform Platform fonctionne avec l'Analytics ID hérité.
seo-title: Requêtes d’Analytics ID et d’Experience Cloud ID
title: Requêtes d’Analytics ID et d’Experience Cloud ID
uuid: 28 beed 16-7 ef 9-4824-8 e 82-853930756 eca
translation-type: tm+mt
source-git-commit: 50a5b4d3a27fd8b21437f02bd9390565f23ac7e6

---


# Requêtes d’Analytics ID et d’Experience Cloud ID{#analytics-and-experience-cloud-id-requests}

Cette section présente comment le service d&#39;identité de Platform Platform fonctionne avec l&#39;Analytics ID hérité.

## Résumé {#section-64d8523ff7634cb987d0c6480f587dd3}

Historiquement, le service d&#39;identité de Platform Platform a été étroitement intégré à Adobe Analytics. Aujourd’hui, il reste un composant intégral d’Analytics mais exerce aussi des fonctions importantes pour d’autres solutions et fonctionnalités [!DNL Experience Cloud]. En raison de cet héritage hérité, la vérification ou l&#39;écriture d&#39;un Analytics ID fonctionne légèrement différemment qu&#39;avec le processus générique décrit dans [la section Demande et définition d&#39;identifiants du service d&#39;identité de Platform Platform….](../../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a) Pour plus d&#39;informations sur l&#39;ordre des opérations pour la vérification des ID, voir [Définition des identifiants Analytics et Experience Cloud ID](../../reference/analytics-reference/analytics-ids.md#concept-f381dd18ee184c6c8e48286937a161d6).

## Le cookie AMCV n’est pas défini dans le navigateur {#section-cccf10cd775e4a95a7e98d3c3c0ff9a9}

Si le cookie [!DNL Experience Cloud] (AMCV) n’est pas présent, un appel du service d’ID à [!DNL Adobe] permet de générer une réponse qui varie selon la présence ou l’absence d’un Analytics ID hérité. L’[!DNL Analytics] ID hérité est stocké dans le [cookie s_vi](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html). Le tableau ci-dessous décrit comment les ID sont écrits dans le cookie AMCV en fonction de l’état du cookie s_vi.

<table id="table_DC85FECE26DD424E841BA1059AF1E57F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> État du cookie s_vi </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b> Le cookie s_vi n’est pas défini</b> </p> </td> 
   <td colname="col2"> <p>Le service d’ID affecte aux visiteurs un <span class="keyword">Experience Cloud</span> ID (MID). Le MID identifie les visiteurs dans <span class="keyword">Analytics</span> et d’autres solutions <span class="keyword">Experience Cloud</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Le cookie s_vi est défini</b> </p> </td> 
   <td colname="col2"> <p>Lorsqu'un visiteur de site avec un cookie s_ vi rencontre pour la première fois le service d'identité Experience Platform, ce service : </p> 
    <ul id="ul_BE584810280D4874AF802A9247011787"> 
     <li id="li_AA395B09A3174AF78F3EC10053E2E4F5">Écrit dans le cookie AMCV l’<span class="keyword">Analytics</span> ID stocké dans le cookie s_vi. Il est écrit en tant qu’<span class="keyword">Analytics</span> ID (AID). Cette action <i>n’a aucune</i> incidence sur les décomptes des visiteurs. <span class="keyword"> Analytics</span> continue à identifier les utilisateurs à l’aide de leur ID hérité. </li> 
     <li id="li_8735DE21FEA542BA8024109B8FE1E2ED">Écrit le MID dans le cookie AMCV. Le MID identifie les utilisateurs dans différentes solutions. </li> 
    </ul> <p> <p>Remarque : Avec une période <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> de grâce</a>, la réponse du centre de données comprend toujours un ID hérité stocké dans le cookie s_ vi. Pendant la période de grâce, l’ID hérité est écrit dans le cookie AMCV en tant que valeur AID. </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Les utilisateurs identifiés par le cookie s_ fid ne souhaitent pas migrer la valeur FID héritée vers le cookie AMCV. Avec un cookie s_fid, les utilisateurs seront migrés comme si aucun cookie s_vi n’était présent (voir ci-dessus) et apparaîtront comme de nouveaux visiteurs de votre site. Pour plus d’informations, voir [Cookies Analytics](https://marketing.adobe.com/resources/help/en_US/whitepapers/cookies/?f=cookies_analytics.html).

## Le cookie AMCV est défini dans le navigateur. {#section-01c088fc565c4b24ba1722c7cc240310}

Si le cookie AMCV est présent,  utilisera le MID en tant qu’identifiant [!DNL Analytics] si aucune valeur d’[!DNL Analytics]Analytics ID hérité ne figure dans le cookie.
