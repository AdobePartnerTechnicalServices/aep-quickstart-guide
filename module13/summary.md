---
title: Segment Activation to Microsoft Azure Event Hub - Summary & benefits
description: Segment Activation to Microsoft Azure Event Hub - Summary & benefits
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 2174ac52-b5dd-4bc8-ab5f-4d84ae9ef19b
---
# Summary & benefits

Congratulations and thank you for investing your time in learning about Microsoft Azure Event Hub and Adobe Experience Platform! 
In this module, you learnt how to set up an Azure Event Hub instance and how to connect that to Adobe Experience Platform.

## Benefits

Let's highlight the benefits of integrating Adobe Experience Platform with Microsoft Azure Event Hub:

- Microsoft Azure Event Hubs as an Adobe Experience Platform Destination lets you capture segment qualification in realtime and process them using an Azure Event Hub function. With such an Azure Event Hub function you can build any kind of custom segment activation handler and as such integrate any kind of third party destination.

- Although destinations are triggered only by specified segments, the activation payload will include all segments for which given profile qualifies.

- A segment only triggers an activation when its status changes. For example a profile that qualifies four times for a segment in a period of three months, only the first two will be activated. The first one is a status change from to **realized**, the second one is triggered by a status change from **realized** to **existing**.

- When activating segments for known profiles, a full identity map is included into the activation payload. Your Azure function can use any of the available identities to map the segments to a profile managed in a third party application, while using the application's customer identifier.

- In this module, the event hub function was deployed locally (debug mode in Visual Studio Code), offering you lots of troubleshooting and debug options.

## Check this out

- N/A
