---
title: Segment Activation to Microsoft Azure Event Hub - Activate Segment
description: Segment Activation to Microsoft Azure Event Hub - Activate Segment
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 250f8536-b6bd-4c64-a552-80d5c6fb6358
---
# 13.4 Activate Segment

## 13.4.1 Add Segment to Azure Event Hub Destination

In this exercise you will add your segment `--demoProfileLdap-- - Interest in Equipment` to your `--demoProfileLdap---aep-enablement` Azure Event Hub destination.

Log in to Adobe Experience Platform by going to this URL: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](../module2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[Production Prod]** in the blue line on top of your screen. After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](../module2/images/sb1.png)

Go to **Destinations**, then click **Browse**. You'll then see all available destinations. Locate your destination and click the **+** icon as indicated below.

![5-01-select-destination.png](./images/5-01-select-destination.png)

You'll then see this. Search for your segment using your ldap and select `--demoProfileLdap-- - Interest in Equipment` from the list of segments.

Click **Next**.

![5-04-select-segment.png](./images/5-04-select-segment.png)

Adobe Experience Platform Real-time CDP can deliver a payload to two types of destinations, segment destinations and profile destinations.

Segment destinations will receive a predefined segment qualification payload that will be discussed later. Such a payload contains **all** the segment qualifications for a specific profile. Even for segments that are not in de destination's activation list. An example of such a segment destination are **Azure Event Hubs** and **AWS Kinesis**.

Profile based destinations let you pick any attribute (firstName, lastName, ...) from the XDM Profile Union Schema and include it in the activation payload. An example of such destination is the **Email Marketing**.

Because your Azure Event Hub destination is a **segment** destination, select for example the field `--aepTenantId--.identification.core.ecid`. 

Click **Add new field**, click browse schema and select the field `--aepTenantId--identification.core.ecid` (delete any other field that would be displayed automatically).

Click **Next**.

![5-05-select-attributes.png](./images/5-05-select-attributes.png)

Click **Finish**.

![5-06-destination-finish.png](./images/5-06-destination-finish.png)

Your segment is now activated towards your Microsoft Event Hub destination.

![5-07-destination-segment-added.png](./images/5-07-destination-segment-added.png)
