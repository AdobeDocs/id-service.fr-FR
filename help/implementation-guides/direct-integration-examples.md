---
description: Les exemples suivants présentent 2 cas d’utilisation courants liés à une intégration directe et à l’Experience Cloud ID (MID). Le MID est un ID unique et persistant pour les visiteurs de votre site.
keywords: Service d’ID
title: Cas d’utilisation de l’intégration directe
exl-id: f2a55b90-8307-4242-b20a-6a3c367a251b
source-git-commit: 06e935a4ba4776baa900d3dc91e294c92b873c0f
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 100%

---

# Cas d’utilisation de l’intégration directe {#direct-integration-use-cases}

Les exemples suivants présentent 2 cas d’utilisation courants liés à une intégration directe et à l’Experience Cloud ID (ECID ou MID). Cet ID est un identifiant unique et persistant pour les visiteurs de votre site.

>[!TIP]
>
>* Consultez et comprenez [les variables et la syntaxe du code](../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9) avant de passer aux cas d’utilisation.
>* Pour plus d’informations sur le MID, voir [Cookies et service Experience Cloud Identity](../introduction/cookies.md).

>



## Cas d’utilisation 1 : je dispose d’un Experience Cloud ID, mais je souhaite transmettre mes identifiants visiteur et définir un état d’authentification {#section-a67d89a343754d1286d03cf08d34b806}

<table id="table_DA8840FCB51541109FE6DF20430E8924"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elément d’exemple d’utilisation </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Conditions</b> </p> </td> 
   <td colname="col2"> <p>Pour ce cas d’utilisation, vous devez : </p> 
    <ul id="ul_F20231F83EE84889B78971A64E758757"> 
     <li id="li_20F3E96493724CD2BAF4B20AEE5CBF23">Posséder un MID pour le visiteur du site. Nommons cet ID 1234. </li> 
     <li id="li_A358C58CC58C4FCBB7250F5ED108AA71">Reconnaître ce visiteur à l’aide de votre propre ID unique. Nommons cet ID 9876. </li> 
     <li id="li_D93CE7182EBE4927A5C7A0BF414C03BC">Vouloir lier le MID (1234) à votre propre ID unique (9876). </li> 
     <li id="li_4611146E56624C2AB647733487A3F046"> <i>(Facultatif)</i> Vouloir définir un statut d’authentification pour ce visiteur. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Actions</b> </p> </td> 
   <td colname="col2"> <p>Dans ces conditions, appelez le service d’ID avec les éléments suivants : </p> 
    <ul id="ul_9ECB1A65266644E89E949C57D202D5A4"> 
     <li id="li_10A6F5A9C54D44A08F4F2E405E6019E2">Le MID (1234). </li> 
     <li id="li_4869572B40E54C54B88A2474DAC475A8">L’ID de votre fournisseur de données. Il s’agit d’un ID unique attribué à votre société. Nommons cet ID 4444. </li> 
     <li id="li_05C8ED47488C4E289D84093127EC7B19">L’ID dont vous disposez pour le visiteur (9876). </li> 
     <li id="li_3D1556AD18C843828A362CC604A9F76B"> <i>(Facultatif)</i> Un ID de statut permettant de définir l’état de l’authentification de ce visiteur. </li> 
    </ul> <p>Si vous disposez d’autres paramètres répertoriés dans le  <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> guide d’intégration directe</a> (par ex. <span class="codeph">d_blob</span> ou <span class="codeph">dcs_region</span>, etc.), vous pouvez également les transmettre. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solution et exemple de code</b> </p> </td> 
   <td colname="col2"> <p>Utilisez le format suivant pour votre appel au service d’ID : </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_mid=1234&amp;d_cid=4444%019876%011&amp;d_ver=2</span> </p> <p>Remarquez que l’exemple d’appel contient : </p> 
    <ul id="ul_0667FBFD8D3C46BDBD027F484691EC97"> 
     <li id="li_FAB1FAE703DB48D1A32EE72684028964">Le MID : <span class="codeph">d_mid=1234</span> </li> 
     <li id="li_C97B74FF444F4BB4B4A5CB1CBBE52249">Le MID associé à votre ID unique pour le visiteur : <span class="codeph">d_mid=1234&amp;d_cid=4444%019876%011</span> </li> 
     <li id="li_D428DBF765234DD78DDF152C5EE8AB69">L’ID d’état d’authentification : <span class="codeph">...d_cid=4444%019876%011</span> (indice : c’est le dernier chiffre) </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Cas d’utilisation 2 : je ne dispose pas d’un MID et dois en générer un {#section-8e81291f8b684de8b88fae4002ae0029}

<table id="table_666A92693F8A413096DF6A64770C1141"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Elément d’exemple d’utilisation </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>Conditions</b> </p> </td> 
   <td colname="col2"> <p>Pour ce cas d’utilisation, vous devez : </p> 
    <ul id="ul_BF3BD821907B46A4B2EFA63146D35722"> 
     <li id="li_E658AE0671D14558B65FDD8992F25996">Ne pas disposer de MID pour le visiteur du site. </li> 
     <li id="li_28A48BB3F71C4E4297F95A2D3E10AD7B">Avoir besoin de demander un MID auprès du service d’ID. </li> 
     <li id="li_E2C306B9308D41E5BFE2F23EF48F5A41">Connaissez votre <a href="../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26" format="dita" scope="local">ID d’organisation</a>. Nommons-le 5555. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Actions</b> </p> </td> 
   <td colname="col2"> <p>Dans ces conditions, appelez le service d’ID avec votre ID d’organisation. </p> <p>Si vous disposez d’autres paramètres répertoriés dans le  <a href="../implementation-guides/direct-integration.md#concept-4cd3206a84bb4687af0b312ae09648b9" format="dita" scope="local"> guide d’intégration directe</a> (par ex. <span class="codeph">d_blob</span> ou <span class="codeph">dcs_region</span>, etc.), vous pouvez également les transmettre. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>Solution et exemple de code</b> </p> </td> 
   <td colname="col2"> <p>Utilisez le format suivant pour votre appel au service d’ID : </p> <p> <span class="codeph">https://dpm.demdex.net/id?d_orgid=5555&amp;d_ver=2</span> </p> <p>Notez de quelle manière l’exemple d’appel contient votre ID d’organisation, <span class="codeph">d_orgid=5555</span>. Il renvoie un <span class="keyword">Experience Cloud</span> ID pour ce visiteur. </p> </td> 
  </tr> 
 </tbody> 
</table>
