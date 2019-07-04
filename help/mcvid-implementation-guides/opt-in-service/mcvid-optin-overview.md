---
description: Le service Opt-in vous permet de configurer des protocoles permettant aux visiteurs de vous donner ou pas l’autorisation d’installer des cookies sur leurs appareils ou sur leurs navigateurs lorsqu’ils visitent votre site.
seo-description: Le service Opt-in vous permet de configurer des protocoles permettant aux visiteurs de vous donner ou pas l’autorisation d’installer des cookies sur leurs appareils ou sur leurs navigateurs lorsqu’ils visitent votre site.
seo-title: Service Opt-in
title: Service Opt-in
uuid: aebd72ad-4118-471b-9755-d08a72caa0fd
translation-type: ht
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Service Opt-in{#opt-in-service}

Le service Opt-in vous permet de configurer des protocoles permettant aux visiteurs de vous donner ou pas l’autorisation d’installer des cookies sur leurs appareils ou sur leurs navigateurs lorsqu’ils visitent votre site.

Le service Opt-in est une extension du service [Experience Cloud ID (ECID)](https://marketing.adobe.com/resources/help/fr_FR/mcvid/), conçu pour vous permettre de contrôler la création de cookies par les solutions Experience Cloud sur les pages web pour les visiteurs avant d’avoir eu l’accord de l’utilisateur (ainsi que de désigner les solutions concernées). Le service Opt-in vous laisse également en charge de la configuration des protocoles et de l’intégration à votre plate-forme de gestion de contenu (CMP) et aux systèmes existants, faisant partie d’un ensemble plus vaste.

L’utilisation du service Opt-in vous permet de définir si un visiteur peut donner son consentement pour toutes les solutions Adobe à la fois ou pour les solutions actuelles l’une après l’autre. Une fois le processus d’approbation terminé et enregistré par le client, vous pouvez récupérer les approbations visiteur de la CMP de l’ensemble des solutions Adobe.

Le service Opt-in est mis en œuvre et configuré facilement à l’aide [d’Adobe Launch](https://docs.adobelaunch.com/) avec [l’extension Opt-in](../../mcvid-implementation-guides/opt-in-service/launch.md). Vous pouvez également le mettre en œuvre et le configurer à l’aide de [DTM](../../mcvid-implementation-guides/opt-in-service/optin-dtm.md).

Pour commencer, reportez-vous à la section [Configuration du service Opt-in](../../mcvid-implementation-guides/opt-in-service/getting-started.md) pour commencer.

>[!NOTE]
>
>Le service Opt-in vous permet de configurer un système d’approbation ou de refus du téléchargement des cookies Adobe uniquement. Celui-ci ne perrmet pas de rassembler les préférences utilisateur en matière de consentement, ni ne constitue un référentiel de préférences.

>[!IMPORTANT]
>
>Le contenu de ce document ne constitue pas un avis juridique et ne vise pas à remplacer un avis juridique. Adressez-vous au service juridique de votre société pour obtenir des conseils en ce qui concerne le consentement et les pratiques quant à la configuration de la mise en œuvre de l’opt-in.

## Opt-in et les diverses solutions Experience Cloud {#section-053e6224505542cf961896f0ca869e52}

Le service Opt-in est un outil vous permettant de construire le workflow correspondant à vos besoins pour l’obtention du consentement. Il vous permet de concevoir un workflow pour agir (déclencher des balises) avant et après avoir reçu l’autorisation de l’utilisateur ou de votre responsable des consentements.

Le service Opt-in vous permet de configurer les pratiques de gestion du consentement des solutions Adobe pour :

* Indiquer si les conditions de collecte des consentements s’appliquent de manière générale à un utilisateur.
* Indiquer, parmi les solutions, lesquelles sont autorisées à générer des cookies.
* Appliquer les préférences par défaut pour chacune des solutions dont l’utilisateur n’a pas explicitement consenti ou refusé la catégorie.
* Déclencher une réponse personnalisée basée sur les modifications apportées aux paramètres de consentement de l’utilisateur, vous permettant de conserver ou de mettre à jour les paramètres dudit utilisateur.

L’utilisation des services Opt-in vous permet de configurer votre site de façon à autoriser le chargement de certains cookies avec consentement préalable avant que l’utilisateur ait fait son choix. Vous pouvez configurer les services Opt-in de sorte que les nouveaux clients autorisent le chargement de cookies après l’affichage de l’accord utilisateur ou après qu’un choix a été proposé à l’utilisateur. Vous pouvez également stocker et récupérer les consentements sur votre plate-forme de gestion de contenu, ou simplement stocker les autorisations d’opt-in dans un cookie.

![](assets/Opt-in-approval.png)

Les solutions Adobe peuvent alors vérifier que la balise est approuvée, s’abonner aux modifications, puis récupérer l’ensemble des clients opt-in. Le service Opt-in vous permet de récupérer les autorisations directement via les bibliothèques JavaScript de la solution ou via ECID lorsque celui-ci a été mis en œuvre.
