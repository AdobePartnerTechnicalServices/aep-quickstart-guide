---
title: Journey Optimizer Create your journey and email message
description: Journey Optimizer Create your email message
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 2b7333c3-5b6a-41c5-a7a7-b048d1579ddd
---
# 7.2 Create your journey and email message

In this exercise, you'll configure the journey and the message that needs to be triggered when someone creates an account on the demo website.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](./images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](./images/acoptriglp.png)

## 7.2.1 Create your journey

In the left menu, click **Journeys**. Next, click **Create Journey** to create a new journey.

![ACOP](./images/createjourney.png)

You'll then see an empty journey screen.

![ACOP](./images/journeyempty.png)

In the previous exercise, you created a new **Event**. You named it like this `ldapAccountCreationEvent` and replaced `ldap` with your ldap. This was the result of the Event creation:

![ACOP](./images/eventdone.png)

You now need to take this event as the start of this Journey. You can do this by going to the left side of your screen and searching for your event in the list of events.

![ACOP](./images/eventlist.png)

Select your event, drag and drop it on the Journey canvas. Your Journey now looks like this:

![ACOP](./images/journeyevent.png)

As the second step in the journey, you need to add a short **Wait** step. Go to the left side of your screen to the **Orchestration** section to find this. You'll be using profile attributes and need to make sure they are populated into the Real-time Customer Profile.

![ACOP](./images/journeywait.png)

Your journey now looks like this. On the right side of the screen you need to configure the wait time. Set it to 1 minute. This will give plenty of time for the profile attributes to be available after the event fires.

![ACOP](./images/journeywait1.png)

Click **Ok** to save your changes.

As the third step in the journey, you need to add an **Email** action. Go to the left side of your screen to **Actions**, select the **Email** action, then drag and drop it on the second node in your journey. You now see this.

![ACOP](./images/journeyactions.png)

Set the **Category** to **Marketing** and select an email surface that enables you to send email. In this case, the email surface to select is **Email**. Ensure that the checkboxes for **Clicks on email** and **email opens** are both enabled.

![ACOP](./images/journeyactions1.png)

The next step is to create your message. To do that, click **Edit content**.

![ACOP](./images/journeyactions2.png)

## 7.2.2 Create your message

To create your message, click **Edit content**.

![ACOP](./images/journeyactions2.png)

You now see this.

![ACOP](./images/journeyactions3.png)

Click the **Subject line** text field.

![Journey Optimizer](./images/msg5.png)

In the text area start writing **Hi**

![Journey Optimizer](./images/msg6.png)

The subject line is not done yet. Next you need to bring in the personalization token for the field **First name** which is stored under `profile.person.name.firstName`. In the left menu, scroll down to find the **Person** element and click on the arrow to go a level deeper.

![Journey Optimizer](./images/msg7.png)

Now find the **Full name** element and click on the arrow to go a level deeper.

![Journey Optimizer](./images/msg8.png)

Finally, find the **First name** field and click on the **+** sign next to it. You'll then see the personalization token appear in the text field.

![Journey Optimizer](./images/msg9.png)

Next, add the text **, thank you for signing up!**. Click **Save**.

![Journey Optimizer](./images/msg10.png)

You'll then be back here. Click **Email Designer** to create the email's content. 

![Journey Optimizer](./images/msg11.png)

In the next screen you will be prompted with 3 different methods to provide the email's content:

- **Design from scratch**: Start with a blank canvas and use the WYSIWYG-editor to drag and drop structure and content components to visually build up the email's content.
- **Code your own**: Create your own email template by coding it using HTML
- **Import HTML**: Import an existing HTML template, which you'll be able to edit.

Click **Design from scratch**.

![Journey Optimizer](./images/msg12.png)

In the left menu, you'll find the structure components that you can use to define the structure of the email (rows and columns).

![Journey Optimizer](./images/msg13.png)

Drag and drop a **1:2 column Left** from the menu into the canvas. This will be the placeholder for the logo image.

![Journey Optimizer](./images/msg14.png)

Drag and drop a **1:1 column** underneath the previous component. This will be the banner block.

![Journey Optimizer](./images/msg15.png)

Drag and drop a **1:2 column Left** underneath the previous component. This will be the actual content with an image on the left side and text on the right side.

![Journey Optimizer](./images/msg16.png)

Next, drag and drop a **1:1 column** underneath the previous component. This will be email's footer. Your canvas should now look like this:

![Journey Optimizer](./images/msg17.png)

Next, let's use Content Components to add content inside these blocks. Click on the **Content Components** menu item

![Journey Optimizer](./images/msg18.png)

Drag and drop an **Image** component in the first cell on the first row. Click **Browse**.

![Journey Optimizer](./images/msg19.png)

You'll then see this. Navigate to the folder **enablement-assets** and select the file **luma-logo.png**. Click **Select**.

![Journey Optimizer](./images/msg21.png)

You're now back here:

![Journey Optimizer](./images/msg25.png)

Go to **Content Components** and drag and drop an **Image** component in the first cell on the first row. Click **Browse**.

![Journey Optimizer](./images/msg26.png)

In the **Assets** pop-up, go to the **enablement-assets** folder. In this folder, you'll find all assets previously prepared and uploaded by the creative team. Select **module23-thankyou-new.png** and click **Select**. 

![Journey Optimizer](./images/msg28.png)

You'll then have this:

![Journey Optimizer](./images/msg30.png)

Select your image and in the right menu, scroll down until you see the **Size** width slider component. Use the slider to change the width to f.i. **60%**.

![Journey Optimizer](./images/msg31.png)

Next, go to **Content Components** and drag and drop a **Text** component in the structure component on the fourth row. 

![Journey Optimizer](./images/msg33.png)

Select the default text **Please type your text here.** as you would do with any text editor. Write **Dear** instead. Notice the text toolbar displayed when you are in text mode.

![Journey Optimizer](./images/msg34.png)

In the toolbar click the **Add personalization** icon.

![Journey Optimizer](./images/msg35.png)

Next, you need to bring the **First name** personalization token which is stored under `profile.person.name.firstName`. In the menu, find the **Person** element, drill down to the **Full Name** element, and then click the **+** icon to add the First Name field onto to expression editor.

Click **Save**.

![Journey Optimizer](./images/msg36.png)

You'll now notice how the personalization field has been added to your text. 

![Journey Optimizer](./images/msg37.png)

In the same text field, hit **Enter** twice to add two lines and write **Thank you for creating your account with Luma!**.

![Journey Optimizer](./images/msg38.png)

The final check to perform to ensure your email is ready is to preview it, click on the **Simulate Content** button.

![Journey Optimizer](./images/msg50.png)

Start by identifying which profile you want to use for the preview. Select the **email** namespace by clicking on the icon next to **Enter identity namespace** field.

In the list of identity namespaces, select the **Email** namespace.

In the **Identity value** field, enter the email address of a previous demo profile that is already stored in the Real-time Customer Profile. For example **woutervangeluwe+06022022-01@gmail.com** and click on the **Find Test Profile** button

![Journey Optimizer](./images/msg53.png)

Once your profile shows up in the table, click on the **Preview** tab to access the preview screen.

When the preview is ready, validate that the personalization is correct in the subject line, the body text as well as the unsubscription link is highlighted as an hyperlink.

Click **Close** to close the preview.

![Journey Optimizer](./images/msg54.png)

Click **Save** to save your message.

![Journey Optimizer](./images/msg55.png)

Go back to the message dashboard by clicking the **arrow** next to the subject line text in the top-left corner.

![Journey Optimizer](./images/msg56.png)

You've now completed creating your registration email. Click the arrow in the top left corner to go back to your journey.

![Journey Optimizer](./images/msg57.png)

Click **Ok**.

![Journey Optimizer](./images/msg57a.png)

## 7.2.3 Publish your journey

You still need to give your journey a Name. You can do that by clicking the **Properties** icon in the top right side of your screen.

![ACOP](./images/journeyname.png)

You can then enter the journey's name here. Please use `--demoProfileLdap-- - Account Creation Journey`. Click **OK** to save your changes.

![ACOP](./images/journeyname1.png)

You can now publish your journey by clicking **Publish**.

![ACOP](./images/publishjourney.png)

Click **Publish** again.

![ACOP](./images/publish1.png)

You'll then see a green confirmation bar saying that your journey is now Published.

![ACOP](./images/published.png)

You've now finished this exercise.
