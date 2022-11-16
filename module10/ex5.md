---
title: Adobe Journey Optimizer - Business Events
description: This section explains how to use the business events capability in order to perform an "item back in stock" use case
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: cc06d847-a405-4223-836c-c22ad6c9caca
---
# 10.5 Create a business event journey

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 10.5.1 Create a business event

In the left menu, click **Configurations**. Click on the **Manage** button inside the **Events** card.

![Journey Optimizer](./images/be1.png)

Business events are a new type of event you can create inside Journey Optimizer. Unlike the **Unitary** events that you have created in previous modules, the business events are not triggered by the customer but by the organization. You'll now create your business event. 

Click **Create Event**.

![Journey Optimizer](./images/be2.png)

Enter the following values in the Event creation form:

- **Name**: `--demoProfileLdap--ItemBackInStock`. For instance: **vangeluwItemBackInStock**
- **Description**: This event is triggered when a product is back in stock
- **Type**: select **Business** in the drop down

![Journey Optimizer](./images/evde.png)

For the Schema, select **Demo System - Event Schema for JO Business Events (Global v1.1) v.1**. You now need to select the fields in the schema that you require for our use case. 

![Journey Optimizer](./images/evdes.png)

Follow these steps:

Click the **pencil** icon on the field where it says **1 field selected**.

![Journey Optimizer](./images/23.8-4.png)

Select all available fields in the schema, then click **OK**.

![Journey Optimizer](./images/23.8-5.png)

For the condition: you need to specify which records in this schema will be triggering the business event. 
  
Follow these steps:

Click the **pencil** icon on the field where it says **Add a condition**.

![Journey Optimizer](./images/23.8-6.png)

On the left-hand side, expand the `--aepTenantId--` object, expand the object **joBusinessEvents** and drag and drop the field **eventName** onto the canvas.

![Journey Optimizer](./images/23.8-7.png)

For the field **eventName**, enter the following value: `--demoProfileLdap--ItemBackInStock`. For instance: vangeluwItemBackInStock.
Click **OK**.

![Journey Optimizer](./images/23.8-8.png)

Click **OK**.

![Journey Optimizer](./images/23.8-9.png)

Finally your event creation form should look like this. Click **Save** to save your business event.

![Journey Optimizer](./images/23.8-10.png)

## 10.5.2 Create a business event journey

You can now leverage this business event and the message inside a journey. Go to **Journeys**. Click **Create Journey**.

![Journey Optimizer](./images/bej10.png)

On the right-hand side you will see a form where you need to specify the journey name and description. Enter the following values:

- **Name**: `--demoProfileLdap-- - Item back in stock journey`. For instance: vangeluw - Item back in stock journey
- **Description**: This journey sends an SMS when an item is back in stock to visitor who have shown an interest.

Click **OK**. 

![Journey Optimizer](./images/bej11.png)

In the left menu, under **Events**, search for your ldap. You'll find the previously created business event `--demoProfileLdap--ItemBackInStock`. Drag and drop this event onto the canvas as this will be the starting point of the journey. 

![Journey Optimizer](./images/bej12.png)

As you can see, a **Read Segment** activity has automatically been added to the canvas. This is because the business events only send a trigger for the journey to read a specific segment, which will then retrieve the list of profiles for that journey.

Click the **Read Segment** activity.
The **Read Segment** configuration expects you to select the segment that you want to notify of the business event that just happened. Click the **Select a segment** field.

![Journey Optimizer](./images/bej13.png)

In the **Choose a segment** popup, search for your ldap and select the segment you created in [Module 6 - Real-time CDP - Build a segment and take action](../module6/README.md) named `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`. for example: vangeluw - Interest in PROTEUS FITNESS JACKSHIRT. Click **Save**.

![Journey Optimizer](./images/bej14.png)

Next, click **Ok**. 

![Journey Optimizer](./images/bej15.png)

The next step is to drag and drop the action that we want to perform in this journey. Select the action **SMS**, then drag and drop it after the condition you just added. 

![Demo](./images/jop9.png)

Set the **Category** to **Marketing** and select a sms surface that enables you to send sms. In this case, the email surface to select is **SMS**. 

![ACOP](./images/journeyactions1x.png)

The next step is to create your message. To do that, click **Edit content**.

![ACOP](./images/journeyactions2x.png)

You'll now see the message dashboard, where you can configure the text of your SMS. Click the **Compose message** area to create your message.

![Journey Optimizer](./images/sms3.png)

Enter the following text: `Hi {{profile.person.name.firstName}}, the Proteus Fitness Jackshirt is back in stock at Luma.`. Click **Save**.

![Journey Optimizer](./images/sms4.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/oc79xx.png)

You'll now see your completed SMS action. Click **Ok**.

![Journey Optimizer](./images/oc79xxy.png)

Your journey is now ready to be published. Click **Publish**.

![Journey Optimizer](./images/jop13.png)

Click **Publish** again.

![Journey Optimizer](./images/jop14.png)

Your journey is now published, you can now test it!

![Journey Optimizer](./images/jop15.png)

## 10.5.3 Test your business event journey

You'll now simulate the re-stock of a product by ingesting a new event against the **Demo System - Event Schema for JO Business Events (Global v1.1) v.1** using Postman.

In the left menu, click **Sources** and then click on the **Accounts** tab.

![Journey Optimizer](./images/s1.png)

On the **Accounts** tab, you'll find the account named **Journey Optimizer Business Events**. Click it to open it.

![Journey Optimizer](./images/s2.png)

This account only has one dataflow, click on the dataflow name to select it.

![Journey Optimizer](./images/s3.png)

Click **Copy schema payload** in the right menu. This option copies the entire **curl** command to insert a record against the **Demo System - Event Schema for JO Business Events (Global v1.1) v.1** to your clipboard.

![Journey Optimizer](./images/s4.png)

Paste the Curl command inside a text editor

![Journey Optimizer](./images/s5.png)

Let's have a closer look to this request,

- The POST request is sent to the DCS Inlet ID
- The request references the schema, the dataset and the Organization ID.
- Finally it contains the xdmEntity node which represents the data that we want to create inside the dataset. 

You now need to replace the following `xdmEntity` line...

```json
"xdmEntity": {
  "_experienceplatform": {
    "joBusinessEvents": {
      "eventDescription": "string",
      "eventName": "string",
      "stockEventId": "string"
    }
  },
  "_id": "/uri-reference",
  "eventType": "advertising.completes",
  "timestamp": "2018-11-12T20:20:39+00:00"
}
```

...by this line, make sure to verify the field eventName as it should say `--demoProfileLdap--ItemBackInStock`, which represents the condition you have specified in your business event to trigger your journey.

```json
"xdmEntity": {
  "_experienceplatform": {
    "joBusinessEvents": {
      "eventDescription": "Product Proteus Fitness Jackshirt is back in stock",
      "eventName": "--demoProfileLdap--ItemBackInStock",
      "stockEventId": "1"
    }
  },
  "_id": "/uri-reference",
  "eventType": "productBackInStock",
  "timestamp": "2021-04-19T15:25:39+00:00"
}
```

The updated **curl** command should look like this:

![Journey Optimizer](./images/s6.png)

Select all of it and copy it to your clipboard.

Open Postman. On the left-hand side of Postman, click **Import**.

![Journey Optimizer](./images/23.8-46.png)

Select the **Raw text** tab and paste the command previously copied here. Click **Continue**.

![Journey Optimizer](./images/s7.png)

Click **Import**.

![Journey Optimizer](./images/23.8-50.png)

Postman has automatically converted the **curl** command into a REST command ready to be triggered, simply press the **Send** button to request the creation of that record inside the dataset.

![Journey Optimizer](./images/23.8-51.png)

Verify that your request has been successfully received. Look for a **200 OK** status in postman.

![Journey Optimizer](./images/s8.png)

The SMS may take a couple of minutes to arrive on your mobile phone. If it does not, your **Interest in Proteus Fitness Jackshirt** segment may not contain a profile with a correct mobile phone. If so, go on the Luma website, visit the **Proteus Fitness Jackshirt** product and register while making sure you provide the correct mobile phone number.

![Journey Optimizer](./images/s9.png)

You have now finished this exercise.
