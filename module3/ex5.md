---
title: Foundation - Real-time Customer Profile - Create a segment - API
description: Foundation - Real-time Customer Profile - Create a segment - API
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 3f537efd-7281-4c0c-b809-97f266a2a337
---
# 3.5 Create a segment - API

In this exercise, you'll use Postman and Adobe I/O to create a segment and store the results of that segment as a dataset, by making use of Adobe Experience Platform's APIs.

## Story

In the Real-time Customer Profile, all profile data is shown alongside event data and existing segment memberships. The data that is shown  can come from anywhere, from Adobe applications and external solutions. This is the most powerful view in Adobe Experience Platform, the experience system of record.

## Exercise 3.5.1 - Create a segment through the Platform API

Go to Postman.

Locate the collection: **_Adobe Experience Platform Enablement**. In this collection, you'll see a folder **2. Segmentation**. We'll be using these requests in this exercise.

![Segmentation](./images/pmdtl.png)

What we'll do next is follow all the required steps to create a segment through the API. We're going to build a simple segment: "**ldap** - All Female Customers".

### Step 1 - Create a Segment Definition

Click on the request named **Step 1 - Profile: Create A Segment Definition**.

![Segmentation](./images/s1_call.png)

Go the the **Body** section of this request.

![Segmentation](./images/s1_body.png)

In the **Body** of this request, you'll see the following:

![Segmentation](./images/s1_bodydtl.png)

The language used for this request is called Profile Query Language, or **PQL**.

You can find more info and documentation about PQL [here](https://experienceleague.adobe.com/docs/experience-platform/segmentation/pql/overview.html?lang=en). 


Attention: please update the variable **name** in the below request by replacing **ldap** with your specific **ldap**.

```json
{
    "name" : "ldap - API - All Female Customer",
    "expression" : {"type":"PQL", "format":"pql/json", "value":"{\"nodeType\":\"fnApply\",\"fnName\":\"in\",\"params\":[{\"nodeType\":\"fieldLookup\",\"fieldName\":\"gender\",\"object\":{\"nodeType\":\"fieldLookup\",\"fieldName\":\"person\",\"object\":{\"nodeType\":\"literal\",\"literalType\":\"XDMObject\",\"value\":\"profile\"}}},{\"literalType\":\"List\",\"nodeType\":\"literal\",\"value\":[\"female\"]}]}"},
    "createdBy": "ldap",
    "schema" : { "name" : "_xdm.context.profile"},
    "ttlInDays" : 90
}
```

After adding your specific **ldap**, the Body should look similar to this:

```json
{
    "name" : "vangeluw - API - All Female Customer",
    "expression" : {"type":"PQL", "format":"pql/json", "value":"{\"nodeType\":\"fnApply\",\"fnName\":\"in\",\"params\":[{\"nodeType\":\"fieldLookup\",\"fieldName\":\"gender\",\"object\":{\"nodeType\":\"fieldLookup\",\"fieldName\":\"person\",\"object\":{\"nodeType\":\"literal\",\"literalType\":\"XDMObject\",\"value\":\"profile\"}}},{\"literalType\":\"List\",\"nodeType\":\"literal\",\"value\":[\"female\"]}]}"},
    "createdBy": "vangeluw",
    "schema" : { "name" : "_xdm.context.profile"},
    "ttlInDays" : 90
}
```

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/s1_h.png)

| Key            | Value              |
| -------------- | ------------------ |
| x-sandbox-name | `--aepSandboxId--` |

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. Your x-sandbox-name should be `--aepSandboxId--`.

Now, click the blue **Send** button to create the segment and view the results of that.

![Segmentation](./images/s1_bodydtl_results.png)

After this step, you can view your segment definition in the Platform UI. To check this, log in to Adobe Experience Platform and go to **Segments**. 

![Segmentation](./images/s1_segmentdef.png)

### Step 2 - Create a Segment POST Job

In the previous exercise, you created a _streaming_ segment. A streaming segment continuously evaluates qualifications in real-time. What you're doing here, is creating a _batch_ segment. Batch segment gives you a preview of what the segment could look like in terms of qualifications, but _that don't mean that the segment has actually run_. Currently, _nobody qualifies for this segment_. To make people qualify, the batch segment needs to run, which is exactly what we'll do here.

Let's now POST a Segment Job.

Go to Postman.

![Segmentation](./images/pmdtl.png)

In your Postman collection, click on the request named **Step 2 - POST Segment Job** to open it.

![Segmentation](./images/s2_call.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/s2headers.png)

| Key            | Value              |
| -------------- | ------------------ |
| x-sandbox-name | `--aepSandboxId--` |

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. Your x-sandbox-name should be `--aepSandboxId--`.

Click on the blue **Send** button.

You should see a similar result:

![Segmentation](./images/s2_call_response.png)

This Segment Job is now running, and this may take some time. In Step 3, you'll be able to check the status of this job.


### Step 3 - GET Segment Job status

Go to Postman.

![Segmentation](./images/pmdtl.png)

In your Postman collection, click on the request named **Step 3 - GET Segment Job status**.

![Segmentation](./images/s3_call.png)

You should also verify the **Header** - fields of your request. Go to **Headers**. You'll then see this:

![Postman](./images/s3headers.png)

| Key            | Value              |
| -------------- | ------------------ |
| x-sandbox-name | `--aepSandboxId--` |

>[!NOTE]
>
>You need to specify the name of the Adobe Experience Platform sandbox you're using. Your x-sandbox-name should be `--aepSandboxId--`.

Click on the blue **Send** button.

You should see a similar result:

![Segmentation](./images/s3_status.png)

In this example, the **status** of the job is set to **QUEUED**.

Repeat this request by clicking the blue **Send** button every couple of minutes until the **status** is set to **SUCCEEDED**.

![Segmentation](./images/s3_status_succeeded.png)

Once the status is **SUCCEEDED**, your segment job has run and customers are now qualifying for the segment.

Congrats, you've successfully completed the Segmentation exercise. Let's now have a look how the Real-time Customer Profile can be activated across the enterprise.
s