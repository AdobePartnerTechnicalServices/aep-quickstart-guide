---
title: Adobe Journey Optimizer - Apply personalization in an email message
description: This exercise explain how to use segment personalization within an email content
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 573ecfba-4f1d-4242-8358-1d33109aaea3
---
# 10.3 Apply personalization in an email message

Login to Adobe Experience Cloud by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Adobe Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home** view in Journey Optimizer. Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepTenantId--``. You can do this by clicking the text **[!UICONTROL Production Prod]** in the blue line on top of your screen.

![ACOP](../module7/images/acoptriglp.png)

## 10.3.1 Segment-based personalization

In this exercise you'll improve your newsletter email message with a personalized text based on segment membership.

Go to **Journeys**. Find the newsletter journey that you have created in the previous exercise. Search for `--demoProfileLdap-- - Newsletter`. Click your journey to open it. 

![Journey Optimizer](./images/sbp1.png)

You'll then see this. Click **Duplicate**. 

![Journey Optimizer](./images/sbp2.png)

Click **Duplicate**.

![Journey Optimizer](./images/sbp3.png)

Select your **Email** action and click **Edit content**.

![Journey Optimizer](./images/sbp3a.png)

Click **Email Designer**.

![Journey Optimizer](./images/sbp4.png)

You'll then see this.

![Journey Optimizer](./images/sbp5.png)

Open **Content Components** and drag a **Text** component below the current newsletter content. 

![Journey Optimizer](./images/sbp6.png)

Select the whole default text and delete it. Then click on the **Add personalization** button in the toolbar.

![Journey Optimizer](./images/sbp7.png)

You'll then see this:

![Journey Optimizer](./images/seg1.png)

In the left menu, click **Segment Memberships**.

![Journey Optimizer](./images/seg2.png)


{% hint style="info" %}
If you can't find your segment in this list, scroll down a bit to find instructions on how to retrieve the segment ID manually.
{% endhint %}

Select the segment `Luma - Women's Category Interest` and click the **+** icon, which should look like this:

![Journey Optimizer](./images/seg3.png)

You should then leave the first line as it is, and replace line 2 and 3 by this code:

``
    Psssst... a private sale in the women category will launch soon, we will keep you posted
{%else%}
    Thanks for taking the time to read our newsletter. Here is a 10% promo code to use on the website: READER10
{%/if%}
``

You'll then have this:

![Journey Optimizer](./images/seg4.png)

Click **Validate** to make sure the code is correct. Click **Save**.

![Journey Optimizer](./images/sbp8.png)

You can now save this message by clicking the **Save** button in the top-right corner. Then, click **Simulate Content**.

![Journey Optimizer](./images/sbp9.png)

Select one of the profiles you created as part of this tutorial and click **Preview**. You'll then see the result of your configuration. 

![Journey Optimizer](./images/sbp10.png)

You'll then see this. Then, click **Close**.

![Journey Optimizer](./images/sbp10fff.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/sbp11.png)

Click the arrow in the top left corner to go back to your journey.

![Journey Optimizer](./images/oc79afff.png)

Click **Ok** to close your email action.

![Journey Optimizer](./images/oc79bfff.png)

Change your **Schedule** to **Once** and define a **Date/Time**. Click **Ok**.


{% hint style="info" %}
Message send date and time must be within more than one hour.
{% endhint %}

![Journey Optimizer](./images/sbp18.png)

Click on the **Publish** button in the journey.

![Journey Optimizer](./images/sbp19.png)

In the pop-up window, click **Publish** again.

![Journey Optimizer](./images/sbp20.png)

Your basic newsletter journey is now published. Your newsletter email message will be sent based on your schedule and your journey will stop as soon as the last email has been sent.

![Journey Optimizer](./images/sbp20fff.png)

You have finished this exercise.
