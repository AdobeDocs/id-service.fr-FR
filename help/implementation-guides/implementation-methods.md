---
description: Méthodes d’implémentation standard ou non standard du service d’identités d’Experience Cloud.
keywords: Service d’ID
title: Méthodes de mise en œuvre
exl-id: 0fe40a3c-bdcd-4290-bcd7-25344ff108d6
TQID: https://experienceleague.adobe.com/VcMKVPqOHJHqwX4CTYHeeQnqrEzwLLJ9xn2-e1vDr-k
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 5c41e39a833b527a329f62e5f0929445f47139de
workflow-type: tm+mt
source-wordcount: 141
ht-degree: 100%

---

# Méthodes de mise en œuvre

Vous pouvez choisir une méthode d’implémentation [!DNL Experience Cloud ID Service] standard avec [!DNL Experience Platform Launch] ou une méthode non standard.

>[!IMPORTANT]
>
>Veillez à lire et à comprendre les conditions [requises pour utiliser le service d’ID](../reference/requirements.md) avant de commencer à utiliser ces procédures.

## Mise en œuvre standard {#section-ea1e5270f2184f85a2e85214a6ac60cb}

Adobe recommande vivement d’utiliser [[!DNL Experience Platform tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=fr) pour implémenter le service d’ID. Cette méthode garantit l’intégration à d’autres solutions [!DNL Experience Cloud], simplifie les processus d’implémentation et assure automatiquement le placement et le séquencement corrects du code.

## Implémentations non standard {#section-2c4f2db1f9704315a7cccab6d2e07113}

Les procédures et exemples de codes de ce guide peuvent vous aider à configurer le service [!DNL Experience Cloud] ID d’une manière manuelle ou non standard. Veuillez noter que ces implémentations sont souvent complexes et difficiles d’un point de vue technique. Elles peuvent nécessiter de votre part des ressources d’ingénierie limitées ou consommer du temps d’assistance contractuel avec votre consultant en Adobe.

