---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more
description: Adobe Journey Optimizer - External Weather API, SMS Action & more
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 7f3d6dcb-845d-4ff1-97c3-8e93b8d2c624
---
# 8. Adobe Journey Optimizer: External data sources and custom actions

**Author: [Wouter Van Geluwe](https://www.linkedin.com/in/woutervangeluwe/)**

In this module, you'll use Adobe Journey Optimizer to listen to customer behavior, both online and offline, and respond to it in an intelligent, contextual and real-time way. You've already had an initial hands-on experience with Adobe Journey Optimizer in Module 6. In this exercise, you'll go a bit deeper and explore a more advanced use case whereby external data sources are used as part of a journey.

## Learning Objectives

- Learn how to create events, external data sources and journeys in Adobe Journey Optimizer
- Learn how to consume weather information from the Open Weather API
- Learn how to use custom action destinations like Twilio and Slack from Adobe Journey Optimizer

## Prerequisites

- Access to Adobe Experience Platform: [https://experience.adobe.com/platform](https://experience.adobe.com/platform)
- Access to Adobe Journey Optimizer
- Access to the Open Weather API

{% hint style="warning" %}
This tutorial was created to facilitate a particular workshop format. It uses specific systems and accounts to which you might not have access. Even without access, we think you can still learn a lot by reading through this very detailed content. If you're a participant in one of the workshops and need your access credentials, please contact **<spphelp@adobe.com>**, who will provide you with the required information.
{% endhint %}

## Architecture Overview

Have a look at the below architecture, which highlights the components that will be discussed and used in this module.

![Architecture Overview](../assets/images/architecturem12.png)

## Business Context

As a brand, you've invested heavily in personalizing online experiences. Now, you want to be as contextual and relevant for offline experiences.
In this module, you'll use a customer's presence in an offline store to then deliver a personalized experience inside the store by showcasing relevant content to that customer on our in-store screens and at the same time, we want to deliver a personalized Push or SMS Message to that same customer, all in real-time.
As a brand, you also understand that context greatly impacts a customer's interest, so you want to bring in the current weather information of that customer's location, to decide what content or promotion to display.

## Sandbox to use

{% hint style="info" %}
Kindly refer to [Exercise 0.0](../getting-started/ex0.md) for instructions on how to find your Sandbox ID and other identifying values.
{% endhint %}

## Exercises

[8.1 Define an event](./ex1.md)

Learn how to define a custom event using Adobe Journey Optimizer.

[8.2 Define an external data source](./ex2.md)

Learn how to configure an external data source using Adobe Journey Optimizer.

[8.3 Define a custom action](./ex3.md)

Learn how to define an external action using Adobe Journey Optimizer.

[8.4 Create your journey and messages](./ex4.md)

Combine events, data sources and actions into an intelligent and contextual journey.

[8.5 Trigger your journey](./ex5.md)

Trigger your specific journey.

[Summary and benefits](./summary.md)

Summary of this module and overview of the benefits.

{% hint style="info" %}
Thank you for investing your time in learning all there is to know about Adobe Experience Platform. If you have questions, want to share general feedback of have suggestions on future content, please contact the Solution Partner Portal, by sending an email to **spphelp@adobe.com**.
{% endhint %}
