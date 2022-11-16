---
title: Customer Journey Analytics - Connect Adobe Experience Platform Datasets in Customer Journey Analytics
description: Customer Journey Analytics - Connect Adobe Experience Platform Datasets in Customer Journey Analytics
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 3b1ffdda-6b9f-4463-8a50-a8a85c3aaf76
---
# 11.2 Connect Adobe Experience Platform Datasets in Customer Journey Analytics

## Objectives

- Understand the Data Connection UI
- Bring Adobe Experience Platform data into CJA
- Understand Person ID and data stitching
- Learn the concept of data streaming in Customer Journey Analytics

## 11.2.1 Connection

Go to [analytics.adobe.com](https://analytics.adobe.com) to access Customer Journey Analytics.

On the Customer Journey Analytics-homepage, go to **Connections**. 

![demo](./images/cja2.png)

Here you can see all the different connections made between CJA and Platform. These connections have the same goal as report suites in Adobe Analytics. However, the collection of the data is totally different. All data is coming from Adobe Experience Platform datasets. 

Let's create your first connection. Click **Create new connection**.

![demo](./images/cja4.png)

You'll then see the **Create Connection** UI.

![demo](./images/cja5.png)

You can now give a name to your connection. 

Please use this naming convention: `--demoProfileLdap-- – Omnichannel Data Connection`. 

Example: `vangeluw - Omnichannel Data Connection`

You also need to select the correct sandbox to use. In the sandbox menu, select your sandbox, which should be `Bootcamp`. In this example, the sandbox to use is **Bootcamp**. And you also need to set the **Average number of daily events** to **less than 1 million**.

![demo](./images/cjasb.png)

After selecting your sandbox, the available datasets will be updated.

![demo](./images/cjasb1.png)

## 11.2.2 Select Adobe Experience Platform datasets

Search for the dataset `Demo System - Event Dataset for Website (Global v1.1)`. Click **+** to add the dataset to this connection.

![demo](./images/cja7.png)

Now search and check the checkboxes for `Demo System - Event Dataset for Voice Assistants (Global v1.1)` and `Demo System - Event Dataset for Call Center (Global v1.1)`. 

You'll then have this. Click **Next**.

![demo](./images/cja9.png)

## 11.2.3 Person ID and Data Stitching

### Person ID

The goal now is to join these datasets. For every dataset you selected, you’ll see a field called **Person ID**. Each dataset has its own Person ID field. 

![demo](./images/cja11.png)

As you can see, most of them have the Person ID selected automatically. This is because a Primary Identifier is selected in every schema in Adobe Experience Platform. As an example, here's the schema for `Demo System - Event Schema for Call Center (Global v1.1)`, where you can see that the Primary Identifier is set to `phoneNumber`.

![demo](./images/cja13.png)

However, you can still influence which identifier will be used to stitch datasets together for your connection. You can use any identifier that is configured in the schema linked to your dataset. Click on the dropdown to explore the IDs available on each dataset.

![demo](./images/cja14.png)

As mentioned, you can set different Person IDs for each dataset. This allows you to bring different datasets from multiple origins together in CJA. Imagine bringing in NPS or survey data which would be very interesting and helpful to understand the context and why something has happened.

The name of the Person ID field isn't important, as long as the value in the Person ID fields correspond. Let say we have `email` in one dataset and `emailAddress` in another dataset defined as Person ID. If `delaigle@adobe.com` is the same value for the Person ID-field on both datasets, CJA will be able to stitch the data.

{% hint style="info" %}
Currently there are some other limitations such us stitching the anonymous behavior to known. Please review the FAQs here: [FAQ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-faq.html). 
{% endhint %}

### Stitching the data using the Person ID

Now that you understand the concept of stitching datasets using the Person ID, let's choose `email` as your Person ID for each dataset. 

![demo](./images/cja15.png)

Go to each dataset to update the Person ID. 

![demo](./images/cja12a.png)

Now fill the field Person ID choosing the `email` on the dropdown list.

![demo](./images/cja17.png)

Once you have stitched the three datasets, we are ready to continue. 

|  dataset       | Person ID | 
| ----------------- |-------------| 
| Demo System - Event Dataset for Website (Global v1.1) | email         | 
| Demo System - Event Dataset for Voice Assistants (Global v1.1) | email          | 
| Demo System - Event Dataset for Call Center (Global v1.1) | email         | 

You also need to ensure that for every dataset, these options are enabled:

- Import all new data
- Backfill all existing data

Click **Add datasets**.

![demo](./images/cja16.png)

Click **Save** and go to the next exercise. 
After having created your **Connection** it may take a few hours before your data is available in CJA.

![demo](./images/cja20.png)
