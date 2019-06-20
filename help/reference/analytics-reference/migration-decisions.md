---
description: Avant de déployer le service Experience Cloud ID, vous devez comprendre comment ce service affecte le suivi des visiteurs sur plusieurs domaines et les problèmes potentiels si vous collectez des données avec des méthodes différentes ou via des fichiers JavaScript.
keywords: Service d’identification
seo-description: Avant de déployer le service Experience Cloud ID, vous devez comprendre comment ce service affecte le suivi des visiteurs sur plusieurs domaines et les problèmes potentiels si vous collectez des données avec des méthodes différentes ou via des fichiers JavaScript.
seo-title: Points de prise de décision concernant la migration vers le service Experience Cloud ID
title: Points de prise de décision concernant la migration vers le service Experience Cloud ID
uuid: ee 56 b 5 de-fcf 3-4 cfb -9 e 53-762 af 7 c 4 d 2 ff
translation-type: tm+mt
source-git-commit: 3e7b49564938527e1b6bca3a5fbaf9eb141d2e06

---


# Points de prise de décision concernant la migration vers le service Experience Cloud ID

Avant de déployer le service Experience Cloud ID, vous devez comprendre comment ce service affecte le suivi des visiteurs sur plusieurs domaines et les problèmes potentiels si vous collectez des données avec des méthodes différentes ou via des fichiers JavaScript.

Répondez aux questions de cette section pour déterminer quelles autres étapes de migration vous devez suivre.

## Avez-vous un CNAME de collecte de données ?

Nombre de clients peuvent procéder à la migration hors d’un CNAME de collecte de données dans le cadre de la migration du service d’ID.

<table id="table_13F7C1E3D64D4F86B0149C9D3B54AADD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Méthode de collecte de données </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Avec un CNAME </p> </td> 
   <td colname="col2"> <p>Reportez-vous à la question suivante pour décider si vous devez effectuer la migration hors d’un CNAME de collecte de données. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Sans CNAME </p> </td> 
   <td colname="col2"> <p>Passez à la question <a href="../../reference/analytics-reference/migration-decisions.md#section-34dabde7780e4a339f134c0ca7768961" format="dita" scope="local">Si vous n’avez pas de CNAME de collecte de données, votre serveur de collecte de données est-il *.2o7.net ou *.sc.omtrdc.net ?</a> </p> </td> 
  </tr> 
 </tbody> 
</table>

## Si vous avez un CNAME de collecte de données, avez-vous plusieurs domaines ?

Si plusieurs domaines envoient des données vers la *même suite de rapports*, il est recommandé d’utiliser un CNAME de collecte de données pour effectuer le suivi des visiteurs sur les domaines. Si vous collectez des données sur un seul domaine, il n’y a aucun avantage à préserver un CNAME de collecte de données.

<table id="table_D132BCA243E54657AEC930559343FDD3"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Collecte des données sur </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>Plusieurs domaines </p> </td> 
   <td colname="col2"> <p>Si vous effectuez le suivi des visiteurs sur plusieurs domaines et que vous avez également un site d’accès principal où les clients peuvent être identifiés avant qu’ils ne visitent d’autres domaines, continuez à utiliser votre CNAME de collecte de données. Voir <a href="../../reference/analytics-reference/cname.md#concept-4df91f8a30ad4ec7a01eb943d579cc9d" format="dita" scope="local">CNAME de collecte de données et suivi inter-domaines</a> pour obtenir une explication détaillée. </p> <p>Notez que vous devez définir deux paramètres supplémentaires pour le serveur de suivi, <span class="codeph">visitor.marketingCloudServer</span> et <span class="codeph">visitor.marketingCloudServerSecure</span>, pour configurer un CNAME avec le service d’ID. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Un seul domaine </p> </td> 
   <td colname="col2"> <p>Lorsque vous utilisez un seul domaine, vous pouvez effectuer la migration hors d’un CNAME de collecte de données si vous ne souhaitez plus le gérer. Si le CNAME fonctionne, il n’y a toutefois aucune raison de le modifier. </p> <p>Si toutefois vous le supprimez : </p> 
    <ul id="ul_12CDECEFC7BB41A18895B507CAA42315"> 
     <li id="li_32E2CD3E58454E20A642BADE507AE86E">Vérifiez que le nouveau serveur de suivi est <a href="https://marketing.adobe.com/resources/help/en_US/whitepapers/rdc/" format="https" scope="external">compatible avec RDC</a>. </li> 
     <li id="li_865BB6DAA3594EBBAB688E73C8343762">Passez du CNAME à un serveur de suivi RDC quelques mois avant la migration vers le service <span class="keyword">Experience Cloud</span> ID. </li> 
     <li id="li_284A015177554C848C8648DC5BBAA365"> <i>N’utilisez pas</i> de serveur de suivi <span class="codeph">*.2o7.net</span>. </li> 
     <li id="li_B1ABF03DC46C42059F61542CDE0FE5A1">Contactez le <a href="https://helpx.adobe.com/marketing-cloud/contact-support.html" format="https" scope="external">service à la clientèle</a> pour configurer la migration des visiteurs. Cela permet d’assurer des décomptes cohérents des visiteurs. </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Disposez-vous de plusieurs fichiers JavaScript Analytics ou effectuez-vous le suivi d’applications ou vidéos Flash ?

Si vous disposez de plusieurs fichiers JavaScript Analytics ou d’applications ou de vidéos Flash sur votre site qui envoient des données vers la *même suite de rapports*, vous devez configurer une période de grâce afin que les visiteurs continuent à être identifiés par un Analytics ID pendant que vous déployez le service [!DNL Experience Cloud] ID.

<table id="table_8A4EA063AF4345B69BC98537E2E702BA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Collecte des données à l’aide de </th> 
   <th colname="col2" class="entry"> Actions requises </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 
    <ul id="ul_910DD99E074E49C6907F86426EFA5BF2"> 
     <li id="li_4366CC8EB7A54A959568E3761ABBBF23">Plusieurs fichiers JavaScript Analytics </li> 
     <li id="li_B8A8132019EA48088E4F37E36F153D76">Autres méthodes de collecte de données </li> 
    </ul> </td> 
   <td colname="col2"> <p>Vous devez configurer une période de grâce d’identification des visiteurs afin que vous puissiez déployer le service d’identification des visiteurs sur chaque fichier JavaScript et sur les autres bibliothèques de collecte de données. Voir <a href="../../reference/analytics-reference/grace-period.md" format="dita" scope="local"> Période de grâce du service d’ID</a>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Un seul fichier JavaScript Analytics </p> </td> 
   <td colname="col2"> <p>Vous pouvez mettre à jour votre fichier JavaScript unique afin d’utiliser le service d’identification des visiteurs sans période de grâce. </p> </td> 
  </tr> 
 </tbody> 
</table>

## Utilisez-vous des méthodes de collecte de données non prises en charge ?

Vous devrez peut-être mettre à jour la façon dont vous effectuez un suivi sur les liens ou migrer hors de Silverlight.

<table id="table_A72AEB92F48345DD83F136B9989F4EF9"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Méthode de collecte de données </th> 
   <th colname="col2" class="entry"> Actions requises </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p>JavaScript et/ou Flash </p> </td> 
   <td colname="col2"> <p>Aucune. Le service <span class="keyword">Experience Cloud</span> ID prend en charge ces méthodes de collecte de données. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Silverlight </p> </td> 
   <td colname="col2"> <p>Si les visiteurs peuvent accéder au contenu Silverlight et aux autres sections de votre site qui utilisent le service <span class="keyword">Experience Cloud</span> ID, vous devez migrer hors de Silverlight. Silverlight n’est pas pris en charge par le service d’ID. </p> <p> Si vous effectuez le suivi d’un lecteur vidéo Silverlight, le fournisseur fournit généralement des API JavaScript que vous pouvez utiliser à la place. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p>Balises d’image codées de manière irréversible </p> </td> 
   <td colname="col2"> <p>Mettez ces liens à jour pour utiliser JavaScript. </p> </td> 
  </tr> 
 </tbody> 
</table>

