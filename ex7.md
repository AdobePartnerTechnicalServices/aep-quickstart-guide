---
title: 0.7 Visualize your own Real-time Customer Profile - UI
description: Foundation - Real-time Customer Profile - Visualize your own Real-time Customer Profile - UI
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: ed13e37f-48eb-4668-b828-6c58340a7cc1
---
# 0.7 Visualize your own Real-time Customer Profile - UI

In this exercise, you'll login to Adobe Experience Platform and view your own Real-time Customer Profile in the UI.
 
## Story

In the Real-time Customer Profile, all profile data is shown alongside event data, as well as existing segment memberships. The data shown can come from anywhere, from Adobe applications and external solutions. This is the most powerful view in Adobe Experience Platform, the true experience system of record.

## 3.2.1 Use the Customer Profile View in Adobe Experience Platform

Go to [Adobe Experience Platform](https://experience.adobe.com/platform). After logging in, you'll land on the homepage of Adobe Experience Platform.

![Data Ingestion](.images/home.png)

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--aepSandboxId--``. You can do this by clicking the text **Production Prod** in the blue line on top of your screen. After selecting the appropriate [!UICONTROL sandbox], you'll see the screen change and now you're in your dedicated [!UICONTROL sandbox].

![Data Ingestion](./images/sb1.png)

In the left menu, go to **Profiles** and to **Browse**.

![Customer Profile](./images/homemenu.png)

On the Profile Viewer panel on your website, you can find multiple identities. Every Identity is linked to a namespace. 

![Customer Profile](./images/identities.png)

On the Profile Viewer panel, you can see these combinations of IDs and Namespaces:

| Identity     | Namespace       |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID)          | 12507560687324495704459439363261812234 |
| Email ID          | woutervangeluwe+06022022-01@gmail.com|
| Mobile Number ID          | +32473622044+06022022-01|

With Adobe Experience Platform, all IDs are equally important. Previously, the ECID was the most important ID in the Adobe context and all other IDs were linked to the ECID in a hierarchical relation. With Adobe Experience Platform this is no longer the case, and every ID can be considered a primary identifier. 

{% hint style="info" %}
Typically, the primary identifier depends on the context. If you ask your Call Center, **What is the most important ID?** they will probably answer, **the phone number!** But if you ask your CRM team, they will answer, **The email address!**  Adobe Experience Platform understands this complexity and manages it for you. Every application, whether an Adobe application or non-Adobe application, will speak with Adobe Experience Platform by referring to the ID they consider primary. And it simply works.
{% endhint %}

For the field **Identity namespace**, select **Email** and for the field **Identity Value** enter the email address you used to register in the previous exercise. Click **View**. You'll then see your profile in the list. Click the **Profile ID** to open your profile.

![Customer Profile](./images/popupecid.png)

You now see an overview of a couple of important **Profile Attributes** of your customer profile.

![Customer Profile](./images/profile.png)

If you'd like to see all available Profile Attributes for your profile, go to **Attributes**.

![Customer Profile](./images/profilattr.png)

Go to **Events**, where you can see entries for every experience event that is linked to your Profile.    

![Customer Profile](./images/profileee.png)

Finally, go to the menu option **Segment membership**. You'll now see all segments that qualify for this profile.

![Customer Profile](./images/profileseg.png)

Now that you've learned how to view any customer's real-time profile by making use of Adobe Experience Platform's User Interface, let's do the same thing through the APIs by making use of Postman and Adobe I/O to query against Adobe Experience Platform's APIs.

Next Step: [0.8 See your Real-time Customer Profile in action in the Call Center](./ex8.md)

[Go Back to Getting Started](getting-started.md)

[Go Back to All Modules](./)
