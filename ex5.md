---
title: 0.5 Ingest Data to AEP through the Website
description: Ingest Data to AEP through the Website
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 683c7dd9-af69-456e-ab75-2a694588e3b3
---
# 0.5 - Ingest Data to AEP through the Website

## Context

The journey from unknown to known is one of the most important topics amongst brands these days, as is the customer journey from acquisition to retention. 

Adobe Experience Platform plays a huge role in this journey. Platform is the brains for communication, the experience system of record.

Platform is an environment in which the word **customer** is broader than just the **known**-customers. This is a very important thing to mention when speaking to brands: an unknown visitor on the website is also a customer from Platform's perspective and as such, all of the behavior as an unknown visitor is also sent to Platform. Thanks to that approach, when this customer eventually becomes a known customer, a brand can visualize what happened before that moment as well. This helps from an attribution and experience optimization perspective.

## What you are going to do

You will now ingest data into Adobe Experience Platform and that data will be linked to identifiers like ECIDs and email-addresses. The goal of this is to understand the business context of what you're about to do from a configuration perspective. In the next exercise, you'll start configuring everything you need to make all that data ingestion possible in your own sandbox environment.

### Customer Journey flow

Go to [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). After logging in with your Adobe ID, you'll see this. Click your website project to open it.

![DSN](images/web8.png)

On the **Screens** page, click **Run**. 

![DSN](images/web2.png)

You'll then see your demo website open up. Select the URL and copy it to your clipboard.

![DSN](images/web3.png)

Open a new incognito browser window.

![DSN](images/web4.png)

Paste the URL of your demo website, which you copied in the previous step. You'll then be asked to login using your Adobe ID.

![DSN](images/web5.png)

Select your account type and complete the login process.

![DSN](images/web6.png)

You'll then see your website loaded in an incognito browser window. For every demonstration, you'll need to use a fresh, incognito browser window to load your demo website URL.

![DSN](images/web7.png)

Click the Adobe logo icon in the top left corner of your screen to open the Profile Viewer.
  
![Demo](images/pv1.png)

Have a look at the Profile Viewer panel and the Real-time Customer Profile with the **Experience Cloud ID** as the primary identifier for thi currently unknown customer.
      
![Demo](./images/pv2.png)

You can also see all the Experience Events that were collected based on the customer's behaviour. The list is currently empty but that will change soon.

![Demo](images/pv3.png)

Go to the **Men** product category. Next, click on the product **Montana Wind Jacket**.

![Demo](images/pv4.png)

You'll then see the product detail page. An Experience Event of type **Product View** has now been sent to Adobe Experience Platform using the Web SDK implementation that you reviewed in Module 1. 
  
![Demo](images/pv5.png)
  
Open the Provile Viewer panel and have a look at your **Experience Events**.
  
![Demo](images/pv6.png)
  
Go back to the **Women** category page, and click another product. Another Experience Event has been sent to Adobe Experience Platform. 
  
![Demo](images/pv7.png)
  
Open the Profile Viewer panel. You'll now see 2 Experience Events of type **Product View**. While the behavior is anonymous, we're able to track every click and store it in in Adobe Experience Platform. Once the anonymous customer becomes known, we'll be able to merge all anonymous behavior automatically to the know profile.
  
![Demo](images/pv8.png)

Go to the Register/Login page. Click **CREATE AN ACCOUNT**.
  
![Demo](images/pv9.png)
  
Fill out your details and click **Register** after which you'll be redirected to the previous page. 

![Demo](images/pv10.png)

Open the Profile Viewer panel and go to Real-time Customer Profile. On the Profile Viewer panel, you should see all of your personal data displayed, like your newly added email and phone identifiers.
  
![Demo](images/pv11.png)

On the Profile Viewer panel, go to Experience Events. You'll see the 2 products that you viewed before on the Profile Viewer panel. Both of these events are now also connected to your 'known' profile.

![Demo](images/pv12.png)
  
You've now ingested data into Adobe Experience Platform and you've linked that data to identifiers like ECIDs and email-addresses. The goal of this is to understand the business context of what you're about to do. In the next exercise, you'll start configuring everything you need to make all that data ingestion possible.

Next Step: [0.6: Navigate the Mobile App](./ex6.md)

[Go Back to Getting Started](getting-started.md)

[Go Back to All Modules](./)
