---
title: Real-time CDP - Build a segment and take action - Configure an Advertising Destination like Google DV360
description: Real-time CDP - Build a segment and take action - Configure an Advertising Destination like Google DV360
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 40441815-428a-48dc-a12e-91220d4ba307
---
# 6.2 Configure an Advertising Destination like Google DV360


{% hint style="warning" %}
The below content is intended as FYI - You do **NOT** have to configure a new destination for DV360. The destination has already been created and you can use it in the next exercise.
{% endhint %}

Go to [Adobe Experience Platform](https://experience.adobe.com/platform). After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](../module2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](../module2/images/sb1.png)

In the left menu, go to **Destinations**, then go to **Catalog**. You'll then see the **Destinations Catalog**.

![RTCDP](./images/rtcdp.png)

In **Destinations**, click on **Google Display & Video 360** and then click **+ Set Up**.

![RTCDP](./images/rtcdpgoogle.png)

You'll then see this. Click **Connect to destination**.

![RTCDP](./images/rtcdpgooglecreate1.png)

In the next screen, you can configure your destination to Google DV360.

![RTCDP](./images/rtcdpgooglecreatedest.png)

Enter a value in the fields **Name** and **Description**.

The field **Account ID** is the **Advertiser ID** of the DV360 Account. You can find that here:

![RTCDP](./images/rtcdpgoogledv360advid.png)

The **Account Type** should be set to **Invite Advertiser**.

Now you have this. Click **Next**.

![RTCDP](./images/rtcdpgoogldv360new.png)


{% hint style="info" %}
Google needs to allow-list Adobe in order for Adobe Experience Platform to send data to Google DV360. Contact your Google Account Manager to enable this dataflow.
{% endhint %}

After creating the destination, you'll see this. You can optionally select a data governance policy. Next, click **Save & exit**.

![RTCDP](./images/rtcdpcreatedest1.png)

You'll then see a list of available destinations. 
In the next exercise, you'll connect the segment you built in the previous exercise to the Google DV360 destination.
