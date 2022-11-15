---
title: Real-time CDP - Build a segment and take action - Build a segment
description: Real-time CDP - Build a segment and take action - Build a segment
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: c0778e81-4282-433d-9e02-37e32bf370ef
---
# 6.1 Create a segment

In this exercise, you'll create a segment by making use of Adobe Experience Platform's segment builder.

## 6.1.1 Context

In today's world, responding to a customer's behavior needs to be real-time. One of the ways of responding to customer behavior in real-time is by using a segment, on the condition that the segment qualifies in real-time. In this exercise, you need to build out a segment, taking into account real activity on the website that we've been using.

## 6.1.2 Identify the behavior you want to react to

Go to [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). After logging in with your Adobe ID, you'll see this. Click your website project to open it.

![DSN](../images/web8.png)

You can now follow the below flow to access the website. Click **Integrations**.

![DSN](../images/web1.png)

On the **Integrations** page, you need to select the Data Collection property that was created in exercise 0.1. 

![DSN](../images/web2.png)

You'll then see your demo website open up. Select the URL and copy it to your clipboard.

![DSN](../images/web3.png)

Open a new incognito browser window.

![DSN](../images/web4.png)

Paste the URL of your demo website, which you copied in the previous step. You'll then be asked to login using your Adobe ID.

![DSN](../images/web5.png)

Select your account type and complete the login process.

![DSN](../images/web6.png)

You'll then see your website loaded in an incognito browser window. For every demonstration, you'll need to use a fresh, incognito browser window to load your demo website URL.

![DSN](../images/web7.png)

In this example, you want to respond to a specific customer viewing a specific product.
From the **Luma** homepage, go to **Men**, and click the product **PROTEUS FITNESS JACKSHIRT**.

![Data Ingestion](./images/homenadia.png)

So when somebody visits the product page for **PROTEUS FITNESS JACKSHIRT**, you want to be able to take action. The first thing to do to take action, is define a segment.

![Data Ingestion](./images/homenadiapp.png)

## 6.1.3 Create the Segment

Go to [Adobe Experience Platform](https://experience.adobe.com/platform). After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](../module2/images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](../module2/images/sb1.png)

In the menu on the left side, go to **Segments** and then go to **Browse** where you can see an overview of all existing segments. Click on the **Create Segment** button to start creating a new segment.

![Segmentation](./images/menuseg.png)

As mentioned above, you need to build a segment out of all customers that have viewed the product **PROTEUS FITNESS JACKSHIRT**.

To build out this segment, you need to add an event. You can find all events by clicking on the **Events** icon in the **Segments** menu bar.

Next, you'll see the top level **XDM ExperienceEvent** node.

To find customers that have visited the **PROTEUS FITNESS JACKSHIRT** product, click on **XDM ExperienceEvent**.

![Segmentation](./images/findee.png)

Scroll down to **Product List Items** and click it.

![Segmentation](./images/see.png)

Select **Name** and drag and drop the **Name** object from the left **Product List Items** menu onto the segment builder canvas into the **Events** section.

![Segmentation](./images/eewebpdtlname1.png)

The comparison parameter should be **equals** and in the input field, enter `PROTEUS FITNESS JACKSHIRT`.

![Segmentation](./images/pv.png)

Your **Event Rules** should now look like this. Every time you add an element to the segment builder, you can click the **Refresh Estimate** button to get a new estimate of the population in your segment.

![Segmentation](./images/ldap4.png)

Finally, let's give your segment a name and save it.

As a naming convention, use:

- `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`

Your segment name should look like this:
`vangeluw - Interest in PROTEUS FITNESS JACKSHIRT`

Next, click the **Save and Close** button to save your segment.

![Segmentation](./images/segmentname.png)

You'll now be taken back to the segment overview page.

![Segmentation](./images/savedsegment.png)
