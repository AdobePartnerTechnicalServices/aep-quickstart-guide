---
title: Adobe Journey Optimizer - Setup and use push notifications for iOS
description: Setup and use push notifications for iOS
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 14a2306a-eb2f-47ee-ad3c-1169412811ca
---
# 10.4 Setup and use push notifications for iOS

In order to use push notifications with Adobe Journey Optimizer, there are a number of settings to check and know about.

Here are all the settings to verify:

- Datasets and schemas in Adobe Experience Platform
- Datastream for mobile
- Data collection property for mobile
- App surface for push certificates
- Test your push setup using AEP Assurance

Let's review these one by one.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 10.4.1 Push datasets

Adobe Journey Optimizer uses datasets to store things like the push tokens from mobile devices or interactions with push messages (such as: message sent, message opened, etc) in a dataset in Adobe Journey Optimizer.

You can find these datasets by going to **[Datasets]** in the menu on the left side of your screen. To show system datasets, click the filter icon.

![Data Ingestion](./images/menudsjo.png)

Enable the option **Show system datasets** and search for **AJO**. You'll then see the datasets used for push notifications.

![Data Ingestion](./images/menudsjo1.png)

## 10.4.2 Datastream for Mobile

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). 

In the left menu, go to **[Datastream]** and search for your datastream that you created in [Exercise 0.2](./../getting-started/ex2.md), which is named `--demoProfileLdap-- - Demo System Datastream (Mobile)`. Click to open it.

![Click Datastream icon in the left navigation](./images/edgeconfig1a.png)

Click **Edit** on the **Adobe Experience Platform** service.

![Click Datastream icon in the left navigation](./images/edgeconfig1.png)

You'll then see the datastream settings that were defined, and into which datasets events and profile attributes will be stored.

![Name the Datastream and save](./images/edgeconfig2.png)

No changes are needed, your datastream is now ready to be used in your Data Collection Client property for Mobile.

## 10.4.3 Review your Data Collection property for Mobile

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). As part of [Exercise 0.1](./../getting-started/ex1.md), 2 Data Collection properties were created. 
You've been using these Data Collection Client properties already as part of previous modules. 

Click to open the Data Collection property for mobile.

![DSN](./images/launchprop.png)

In your Data Collection property, go to **Extensions**. You'll then see the various extensions that are needed for the mobile app. Click to open the extension **Adobe Experience Platform Edge Network**.

![Adobe Experience Platform Data Collection](./images/launchprop1.png)

You'll then see that your datastream for mobile is linked here. Next, click **Cancel** to go back to your extensions overview.

![Adobe Experience Platform Data Collection](./images/launchprop2.png)

You'll then be back back here. You'll see the extension for **AEP Assurance**. AEP Assurance helps you inspect, proof, simulate, and validate how you collect data or serve experiences in your mobile app. You can read more about AEP Assurance and Project Griffon here [https://aep-sdks.gitbook.io/docs/beta/project-griffon](https://aep-sdks.gitbook.io/docs/beta/project-griffon).

![Adobe Experience Platform Data Collection](./images/launchprop8.png)

Next, click **Configure** to open the extension **Adobe Journey Optimizer**.

![Adobe Experience Platform Data Collection](./images/launchprop9.png)

You'll then see that this is where the dataset for tracking push events is linked.

![Adobe Experience Platform Data Collection](./images/launchprop10.png)

There's no need to make any changes to your Data Collection property.

## 10.4.4 Review your App Surface setup

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/). In the left menu, go to **App Surfaces** and ope, the App Surface for **DX Demo App APNS**.

![Adobe Experience Platform Data Collection](./images/appsf.png)

You'll then see the configured App Surface for iOS and Android.

![Adobe Experience Platform Data Collection](./images/appsf1.png)

## 10.4.5 Test push notification setup using AEP Assurance.

Once the app is installed, you'll find it on your device's home screen. Click the icon to open the app.

![DSN](../images/mobileappn1.png)

When you're using the app the first time, you'll be requested to log in using your Adobe ID. Complete the login process.

![DSN](../images/mobileappn2.png)

After logging in, you'll see a notification requesting your permission to send notifications. We'll send notifications as part of the tutorial, so click **Allow**.

![DSN](../images/mobileappn3.png)

You'll then see the app's homepage. Go to **Settings**.

![DSN](../images/mobileappn4.png)

In settings, you'll see that currently a **Public Project** is loaded in the app. Click **Custom Project**.

![DSN](../images/mobileappn5.png)

You can now load a custom project. Click the QR code to easily load your project.

![DSN](../images/mobileappn6.png)

After exercise 0.1, you had this result. Click to open the **Mobile Retail project** that was created for you.

![DSN](../images/dsn5b.png)

In case you had accidentally closed your browser window, or for future demo or enablement sessions, you can also access your website project by going to [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). After logging in with your Adobe ID, you'll see this. Click your mobile app project to open it.

![DSN](../images/web8a.png)

You'll then see this. Click **Integrations**.

![DSN](../images/web8aa.png)

You need to select the Data Collection property for mobile that was created in exercise 0.1. Next, click **Run**.

![DSN](../images/web8b.png)

You'll then see this popup, which contains a QR code. Scan this QR-code from within the mobile app.

![DSN](../images/web8c.png)

You'll then see your project ID show in the app, after which you can click **Save**.

![DSN](../images/mobileappn7.png)

Now, go back to **Home** in the app. Your app is now ready to be used.

![DSN](../images/mobileappn8.png)

You now need to scan a QR code to connect your mobile device to your AEP Assurance session. 

To start an AEP Assurance session, go to [https://experience.adobe.com/#/@experienceplatform/griffon](https://experience.adobe.com/#/@experienceplatform/griffon). Click **Create Session**.

![Adobe Experience Platform Data Collection](./images/griffon3.png)

Click **Start**.

![Adobe Experience Platform Data Collection](./images/griffon5.png)

Fill out the values:

- Session Name: use `--demoProfileLdap-- - push debugging` and replace ldap by your ldap
- Base URL: use **dxdemo://default**

Click **Next**.

![Adobe Experience Platform Data Collection](./images/griffon4.png)

You'll then see a QR code on your screen, which you should scan with your iOS device.

![Adobe Experience Platform Data Collection](./images/griffon6.png)

On your mobile device, open the camera app and scan the QR code that is displayed by AEP Assurance.

![Adobe Experience Platform Data Collection](./images/ipadPushTest8a.png)

You'll then see a popup screen, asking you to enter the PIN-code. Copy the PIN-code from your AEP Assurance screen and click **Connect**.

![Adobe Experience Platform Data Collection](./images/ipadPushTest9.png)

You'll then see this.

![Adobe Experience Platform Data Collection](./images/ipadPushTest11.png)

In AEP Assurance, you'll now see that a devicer is to the AEP Assurance session.

![Adobe Experience Platform Data Collection](./images/griffon7.png)

Go to **Push Debug**. You'll see something like this.

![Adobe Experience Platform Data Collection](./images/griffon10.png)

Some explanation:

- The first column, **Client**, shows the available identifiers on your iOS device. You'll see an ECID and a Push Token.
- The second column shows **Profile** information, with additional info on what platform the Push Token lives in (APNS or APNSSandbox). If you click the **Inspect Profile** button, you'll be taken to Adobe Experience Platform and you'll see the full Real-time Customer Profile.
- The 3rd column shows the **App Configuration**, which was set up as part of exercise **10.5.4 Create App Configuration in Launch**

To test your Push configuration setup, click the **Send Push Notification** button. 

![Adobe Experience Platform Data Collection](./images/griffon11.png)

You need to make sure that the **DX Demo** app isn't open at the time of clicking the **Send Push Notification** button. If the app is open, the Push Notification might be received in the background and wouldn't be visible.

You'll then see a push notification like this one appear on your mobile device.

![Adobe Experience Platform Data Collection](./images/ipadPush2.png)

If you've received the push notification, that means that your setup is correct and working fine.

## 10.4.6 Create a new event

In the menu, go to **Journey Administration** and click **Manage** under **Events**.

![ACOP](./images/acopmenu.png)

On the **Events** screen, you'll see a view similar to this. Click **Create Event**.

![ACOP](./images/add.png)

You'll then see an empty event configuration.

![ACOP](./images/emptyevent.png)

First of all, give your Event a Name like this: `--demoProfileLdap--StoreEntryEvent` and set description to `Store Entry Event`.

![ACOP](./images/eventname.png)

Next is the **Event Type** selection. Select **Unitary**.

![ACOP](./images/eventidtype1.png)

Next is the **Event ID Type** selection. Select **System Generated**

![ACOP](./images/eventidtype.png)

Next is the Schema selection. A schema was prepared for this exercise. Please use the schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

After selecting the Schema, you'll see a number of fields being selected in the **Payload** section. Your event is now fully configured.

![ACOP](./images/eventpayload.png)

You should then see this. Click **Save**.

![ACOP](./images/eventsave.png)

Your Event is now configured and saved. Click on your event again to open up the **Edit Event** screen again.

![ACOP](./images/eventdone.png)

Hover over the **Payload** field and click on the **View Payload** icon.

![ACOP](./images/hover.png)

You'll now see an example of the expected payload.

![ACOP](./images/fullpayload.png)

Your Event has a unique orchestration eventID, which you can find by scrolling down in that payload until you see `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

The event ID is what needs to be sent to Adobe Experience Platform in order to trigger the Journey that you'll build in the next step. Write down this eventID, as you'll need it in the next step.
`"eventID": "e3a8f0bdc0b609667cd96a72a6b1e5aafa0ddaf6ccf121c574e6a2030860a633"`

Click **Ok**, followed by **Cancel**.

## 10.4.7 Create a journey

In the menu, go to **Journeys** and click **Create Journey**.

![DSN](./images/sjourney1.png)

You'll then see this. Give your journey a name. Use `--demoProfileLdap-- - Store Entry journey`. Click **OK**.

![DSN](./images/sjourney3.png)

First, you need to add your event as the starting point of your journey. Search for your event `--demoProfileLdap--StoreEntryEvent` and drag and drop it onto the canvas. Click **OK**.

![DSN](./images/sjourney4.png)

Next, under **Actions**, search for the **Push** action.
Drag and drop the **Push** action onto the canvas.

![DSN](./images/sjourney5.png)

Set the **Category** to **Marketing** and select a push surface that enables you to send push notifications. In this case, the email surface to select is **Push-iOS-Android**.

![ACOP](./images/journeyactions1push.png)

The next step is to create your message. To do that, click **Edit content**.

![ACOP](./images/journeyactions2push.png)

You'll then see this. Click the **personalization** icon for the **Title** field.

![Push](./images/bp5.png)

You'll then see this. You can now select any Profile attribute from the Real-time Customer Profile directly.

![Push](./images/bp6.png)

Search for the field **First Name**, then click the **+** icon next to the field **First Name**. You'll then see the personalization token for First Name being added: **{{profile.person.name.firstName}}**.

![Push](./images/bp9.png)

Next, add the text **, welcome to our store!** behind **{{profile.person.name.firstName}}**.

Click **Save**.

![Push](./images/bp10.png)

You now have this. Click the **personalization** icon for the **Body** field.

![Push](./images/bp11.png)

Enter this text **Click here to get a 10% discount when you buy today!** and click **Save**.

![Push](./images/bp12.png)

You'll then have this. Click the arrow in the top left corner to go back to your journey.

![Journey Optimizer](./images/bp12a.png)

Click **OK** to close your push action.

![DSN](./images/sjourney8.png)

Click **Publish**.

![DSN](./images/sjourney10.png)

Click **Publish** again.

![DSN](./images/sjourney10a.png)

Your journey is now published.

![DSN](./images/sjourney11.png)

## 10.4.8 Test your journey and push message

In your DX Demo 2.0 mobile application, go to the **Settings** screen. Click the **Store Entry** button.


{% hint style="info" %}
The **Store Entry** button is currently being implemented. You won't yet find it in the app.
{% endhint %}

![DSN](./images/demo1b.png)

Make sure to close the app immediately after clicking the **Store Entry** icon, otherwise the push message won't be shown.

![DSN](./images/demo2.png)

After a couple of seconds, you'll see the message appear.

![DSN](./images/demo3.png)

You have finished this exercise.
