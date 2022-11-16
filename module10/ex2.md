---
title: Adobe Journey Optimizer - Configure a batch-based journey
description: In this section you will configure a batch email journey to send a newsletter
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 761da5b4-682f-430b-951c-278302fc4c54
---
# 10.2 Configure a batch-based newsletter journey 

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 10.2.1 Create newsletter journey

You'll now create a batch-based journey. Unlike the event-based journey of the previous exercise which relies on incoming experience events or segment entries or exits to trigger a journey for 1 specific customer, batch-based journeys target a whole segment once with unique content like newsletters, one-off promotions, or generic information or periodically with similar content sent on a regular basis like for instance birthday campaigns and reminders. 

In the menu, go to **Journeys** and click **Create Journey**.

![Journey Optimizer](./images/oc43.png)

On the right-hand side you will see a form where you need to specify the journey name and description. Enter the following values:

- **Name**: `--demoProfileLdap-- - Newsletter Journey`. For instance: **vangeluw - Newsletter Journey**.
- **Description**: Monthly Newsletter

Click **Ok**. 

![Journey Optimizer](./images/batchj2.png)

Under **Orchestration**, drag and drop **Read Segment** onto the canvas. This means that, once published, the journey will start by retrieving the whole segment audience, which then becomes the target audience of the journey and message. Click **Select a segment**.

![Journey Optimizer](./images/batchj3.png)

In the **Choose a segment** popup, search for your ldap and select the segment you created in [Module 6 - Real-time CDP - Build a segment and take action](../module6/README.md) named `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`. for example: vangeluw - Interest in PROTEUS FITNESS JACKSHIRT. Click **Save**.

![Journey Optimizer](./images/batchj5.png)

Click **Ok**.

![Journey Optimizer](./images/batchj6.png)

In the left menu, find the **Actions** section and drag and drop an **Email** action onto the canvas.

![Journey Optimizer](./images/batchj7.png)

Set the **Category** to **Marketing** and select an email surface that enables you to send email. In this case, the email surface to select is **Email**. Ensure that the checkboxes for **Clicks on email** and **email opens** are both enabled.

![ACOP](./images/journeyactions1eee.png)

The next step is to create your message. To do that, click **Edit content**.

![ACOP](./images/journeyactions2.png)

You now see this. Click the **Subject line** text field.

![Journey Optimizer](./images/batch4.png)

Enter this text for the subject line: `Luma Newsletter - your monthly update has arrived.`. Click **Save**.

![Journey Optimizer](./images/batch5.png)

You'll then be back here. Click **Email Designer** to start creating the email content. 

![Journey Optimizer](./images/batch6.png)

You'll then see this. Click **Import HTML**.

![Journey Optimizer](./images/batch7.png)

In the pop-up screen, you'll need to drag and drop the HTML file of the email. You can find the HTML template [here](../assets/html/ajo-newsletter.html.zip). Download the zip-file with the HTML template to your local machine and unzip in onto your desktop.

![Journey Optimizer](./images/html1.png)

Drag and drop the file **ajo-newsletter.html** to upload it in Journey Optimizer. Click **Import**.

![Journey Optimizer](./images/batch8.png)

This email content is ready to go since it has all the expected personalization, imagery and text. Only the offer placeholder is left empty. 

You might get an error message: **Error when trying to fetch assets**. This is linked to the image in the email.

![Journey Optimizer](./images/errorfetch.png)

If you get this error, select the image and click the **Edit image** button.

![Journey Optimizer](./images/errorfetch1.png)

Click **Assets Essentials** to go back to your AEM Assets Essentials library.

![Journey Optimizer](./images/errorfetch2.png)

You'll then see this popup. Navigate to the folder **enablement-assets** and select the image **luma-newsletterContent.png**. Click **Select**.

![Journey Optimizer](./images/errorfetch3.png)

Your basic newsletter email is now ready. Click **Save**.

![Journey Optimizer](./images/ready.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/batch9.png)

Click the arrow in the top left corner to go back to your journey.

![Journey Optimizer](./images/oc79aeee.png)

Click **Ok** to close your email action.

![Journey Optimizer](./images/oc79beee.png)

Your newsletter journey is now ready to be published. Before you do so, notice the **Schedule** section where you can switch this journey from being a one-off to a recurring campaign. Click the **Schedule** button.

![Journey Optimizer](./images/batchj12.png)

You'll then see this. Select **Once**.

![Journey Optimizer](./images/sch1.png)

Select a date and time within the next hour so you can test your journey. Click **Ok**.


{% hint style="info" %}
Message send date and time must be within more than one hour.
{% endhint %}

Click **Publish**.

![Journey Optimizer](./images/batchj13.png)

Click **Publish** again.

![Journey Optimizer](./images/batchj14.png)

Your basic newsletter journey is now published. Your newsletter email message will be sent as you defined it in your schedule, and your journey will stop as soon as the last email has been sent.

![Journey Optimizer](./images/batchj14eee.png)

You have finished this exercise.
