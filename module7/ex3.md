---
title: Module 7 Update your Configuration ID and Test your Journey
description: Update your Configuration ID and Test your Journey
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: d3ceb676-d7f5-4f52-85a4-deaa5ef24034
---
# 7.3 Update your Data Collection property and test your journey

## 7.3.1 Update your Data Collection property

Go to [Adobe Experience Platform Data Collection](https://experience.adobe.com/launch/) and select **Tags**.

This is the Adobe Experience Platform Data Collection Properties page you saw before.

![Properties page](../module1/images/launch1.png) 

In module 0, Demo System created two Client properties for you: one for the website and one for the mobile app. Find them by searching for `--demoProfileLdap--` in the **[!UICONTROL Search]** box. Click to open the **Web** property.

![Search box](../module1/images/property6.png)

You'll then see this.

![Launch Setup](./images/rule1.png)

In the left menu, go to **Rules** and search for the rule **Register profile**. Click the rule **Register profile** to open it.

![Launch Setup](./images/rule2.png)

You'll then see the details of this rule. Click to open the action **Send "Registration Event" to AEP - trigger JO**.

![Launch Setup](./images/rule3.png)

You'll then see that when this action is triggered, a specific data element is used to define the XDM data structure. You need to update that data element, and you need to define the **Event ID** of the event that you configured in [Exercise 7.1](./ex1.md).

![Launch Setup](./images/rule4.png)

You now need to go update the data element **XDM - Registration Event**. To do so, go to **Data Elements**. Search for **XDM - Registration Event** and click to open that data element.

![Launch Setup](./images/rule5.png)

You'll then see this:

![Launch Setup](./images/rule6.png)

Navigate to the field `_experience.campaign.orchestration.eventID`. Remove the current value, and paste your eventID there.

As a reminder, the Event ID can be found in Adobe Journey Optimizer under **Configurations > Events** and you'll find the event ID in the sample payload of your even, which looks like this: `"eventID": "227402c540eb8f8855c6b2333adf6d54d7153d9d7d56fa475a6866081c574736"`.

![ACOP](./images/payloadeventID.png)

After pasting your eventID, your screen should look like this. Next, click **Save** or **Save to Library**.

![Launch Setup](./images/rule7.png)

Finally, you need to publish your changes. Go to **Publishing Flow** in the left menu.

![Launch Setup](./images/rule8.png)

Click **Add All Changed Resources** and then click **Save & Build to Development**.

![Launch Setup](./images/rule9.png)

Your library will then be updated and after 1-2 minutes you can then go ahead and test your configuration.

## 7.3.2 Test your Journey

Go to [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). After logging in with your Adobe ID, you'll see this. Click your website project to open it.

![DSN](../images/web8.png)

On the **Screens** page, click **Run**. 

![DSN](../module1/images/web2.png)

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

Click the Adobe logo icon in the top left corner of your screen to open the Profile Viewer.
  
![Demo](../module2/images/pv1.png)

Have a look at the Profile Viewer panel and the Real-time Customer Profile with the **Experience Cloud ID** as the primary identifier for thi currently unknown customer.
      
![Demo](../module2/images/pv2.png)

Go to the Register/Login page. Click **CREATE AN ACCOUNT**.
  
![Demo](../module2/images/pv9.png)
  
Fill out your details and click **Register** after which you'll be redirected to the previous page. 

![Demo](../module2/images/pv10.png)

Open the Profile Viewer panel and go to Real-time Customer Profile. On the Profile Viewer panel, you should see all of your personal data displayed, like your newly added email and phone identifiers.
  
![Demo](../module2/images/pv11.png)
  
1 minute after having created your account, you'll receive your account creation email from Adobe Journey Optimizer.

![Launch Setup](./images/email.png)
