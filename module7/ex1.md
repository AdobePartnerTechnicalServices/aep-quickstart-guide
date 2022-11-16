---
title: Journey Optimizer Create your event
description: Journey Optimizer Create your event
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: e35d2357-21f9-4566-b2a1-cc0cf0c64956
---
# 7.1 Create your event

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](./images/acoptriglp.png)

In the left menu, scroll down and click **Configurations**. Next, click the **Manage** button under **Events**.

![ACOP](./images/acopmenu.png)

You'll then see an overview of all available events. Click **Create Event** to start creating your own event.

![ACOP](./images/emptyevent.png)

A new, empty event window will then pop up.

![ACOP](./images/emptyevent1.png)

First of all, give your Event a Name like this: `--demoProfileLdap--AccountCreationEvent`.

![ACOP](./images/eventname.png)

Next, add a description like this `Account Creation Event`.

![ACOP](./images/eventdescription.png)

Next, make sure the **Type** is set to **Unitary**, and for the **Event ID Type** selection, select **System Generated**.

![ACOP](./images/eventidtype.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. You should now hover over the **Payload** section and you'll see 3 icons popup. Click on the **Edit** icon.

![ACOP](./images/eventpayload.png)

You'll see a **Fields** window popup, in which you need to select some of the fields that we need to personalize the email.  We will choose other profile attributes later, using the data already in Adobe Experience Platform.

![ACOP](./images/eventfields.png)

In the object `--aepTenantId--.demoEnvironment`, please make sure to select the fields **brandLogo** and **brandName**.

![ACOP](./images/eventpayloadbr.png)

In the object `--aepTenantId--.identification.core`, please make sure to select the field **email**.

![ACOP](./images/eventpayloadbrid.png)

Click **Ok** to save your changes.

![ACOP](./images/saveok.png)

You should then see this:

![ACOP](./images/eventsave.png)

Click **Save** once more to save your changes.

![ACOP](./images/save1.png)

Your event is now configured and saved.

![ACOP](./images/eventdone.png)

Click your event again to open up the **Edit Event** screen again. Hover over the **Payload** field again to see the 3 icons again. Click on the **View Payload** icon. 

![ACOP](./images/viewevent.png)

You'll now see an example of the expected payload.

![ACOP](./images/fullpayload.png)

Your Event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

The event ID is what needs to be sent to Adobe Experience Platform in order to trigger the Journey that you'll build in Exercise 7.2. Remember this eventID, as you'll need it in Exercise 7.3.
`"eventID": "227402c540eb8f8855c6b2333adf6d54d7153d9d7d56fa475a6866081c574736"`

Click **Ok**, followed by clicking **Cancel**.

You've now finished this exercise.
