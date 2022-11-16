---
title: Offer Decisioning - Test your Decision using the API
description: Test your Decision using the API
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 0091c31f-0b54-4d40-a82b-3bf688db8a1f
---
# 9.6 Test your decision using the API

## 9.6.1 Work with the Offer Decisioning API using Postman

Download [this Postman Collection for Offer Decisioning](../assets/postman/postman_offer-decisioning.zip) to your desktop and unzip it. You'll then have this:

![OD API](./images/unzip.png)

You now have this file on your desktop:

- [_Module 14- Decisioning Service.postman_collection.json]

In [Exercise 3.3.3 - Postman authentication to Adobe I/O](./../module3/ex3.md) you installed Postman. You'll need to use Postman again for this exercise.

Open Postman. Click **[Import]**.

![Adobe I/O New Integration](./images/postmanui.png)

Click on **[Upload files]**.

![Adobe I/O New Integration](./images/pm1.png)

Select the file **[_Module 14- Decisioning Service.postman_collection.json]** and click **[Open]**.

![Adobe I/O New Integration](./images/pm2.png)

You'll then have this collection available in Postman.

![Adobe I/O New Integration](./images/pm3.png)

You now have everything you need in Postman to start interacting with Adobe Experience Platform through the APIs.

### 9.6.1.1 List Containers

Click to open the request **[GET - List Containers]**. 

Under **[Params]**, you'll see this: 

- property: `_instance.parentName==aepenablementfy22`

In that parameter, **[aepenablementfy22]** is the name of the sandbox that is used in Adobe Experience Platform. The sandbox you should use is `--aepSandboxId--`. Replace the text **[aepenablementfy22]** by `--aepSandboxId--`.

After replacing the sandbox name, click **[Send]**.

![OD API](./images/api2.png)

This is the response, which shows the offer container for the sandbox that you specified. Please copy the **[container instanceId]** as indicated below and write it down in a text file on your computer. You'll need to use this **[container instanceId]** for the next exercise!

![OD API](./images/api3.png)

### 9.6.1.2 List Placements

Click to open the request **[GET - List Placements]**. Click **[Send]**.

![OD API](./images/api4.png)

You're now seeing all available placements in your offer container. The placements you're seeing were defined in the Adobe Experience Platform UI, as you could see in [Exercise 9.1.3](./ex1.md).

![OD API](./images/api5.png)

### 9.6.1.3 List Decision Rules

Click to open the request **[GET - List Decision Rules]**. Click **[Send]**.

![OD API](./images/api6.png)

In the response, you'll see the Decision Rules that you defined in the Adobe Experience Platform UI, as you could see in [Exercise 9.1.4](./ex1.md).

![OD API](./images/api7.png)

### 9.6.1.4 List Personalized Offers

Click to open the request **[GET - List Personalized Offers]**. Click **[Send]**.

![OD API](./images/api8.png)

In the response, you'll see the Personalized Offers that you defined in the Adobe Experience Platform UI in [Exercise 9.2.1](./ex2.md).

![OD API](./images/api9.png)

### 9.6.1.5 List Fallback Offers

Click to open the request **[GET - List Fallback Offers]**. Click **[Send]**.

![OD API](./images/api10.png)

In the response, you'll see the Fallback Offer that you defined in the Adobe Experience Platform UI in [Exercise 9.2.2](./ex2.md).

![OD API](./images/api11.png)

### 9.6.1.6 List Collections

Click to open the request **[GET - List Collections]**.

![OD API](./images/api12.png)

In the response, you'll see the Collection that you defined in the Adobe Experience Platform UI in [Exercise 9.2.3](./ex2.md).

![OD API](./images/api13.png)

### 9.6.1.7 Get Detailed Offers for Customer Profile

Click to open the request **[POST - Get Detailed Offers for Customer Profile]**. This request is similar to the previous one, but will actually return details like image URLs, text etc.

![OD API](./images/api23.png)

For this request, similar to the previous exercise which has similar requirements, you need to provide the values for **[xdm:placementId]** and **[xdm:activityId]** to retrieve the specific offer details for a customer.

The field **[xdm:activityId]** needs to be filled out. You can retrieve that in the Adobe Experience Platform UI, as indicated below.

![OD API](./images/activityid.png)

The field **[xdm:placementId]** needs to be filled out. You can retrieve that in the Adobe Experience Platform UI, as indicated below. In the below example, you can see the placementId for the placement **[Web - Image]**.

![OD API](./images/placementid.png)

Go to **[Body]** and enter the email address of the customer for whom you'd like to request an offer. Click **[Send]**.

![OD API](./images/api24.png)

Finally, you'll then see the result of what kind of personalized offer and what assets need to be displayed to this customer.

![OD API](./images/api25.png)

You've now completed this exercise.
