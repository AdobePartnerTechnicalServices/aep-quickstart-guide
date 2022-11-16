---
title: Offer Decisioning - Test your Decision using the demo website
description: Test your Decision using the demo website
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: cdb2ba7d-bfc3-43ce-b9a1-1f0866322589
---
# 9.4 Combine Adobe Target and Offer Decisioning

## 9.4.1 Collect your demo project's shareable link

In order to load the demo website project in Adobe Target, you first need to collect a special link that will allow Adobe Target to load your demo website project.

To do that, go to [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). After logging in with your Adobe ID, you'll see this. Click your website project to open it.

![RTCDP](./images/builder1.png)

You'll now see this. Click **Share**. 

![RTCDP](./images/builder2.png)

Click **Generate Link** and then copy the link to your clipboard.

![RTCDP](./images/builder3.png)

Go to [https://bitly.com](https://bitly.com), paste the link you copied and click **Shorten**. You'll now get a shortened link, which looks like this: `https://bit.ly/3JxN7aG`. You'll need that link in the next exercise.

![RTCDP](./images/builder4.png)

## 9.4.2 Collect

Now go to the Adobe Experience Cloud homepage by going to [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Click **Target**.

![RTCDP](../module6/images/excl.png)

On the **Adobe Target** homepage, you'll see all existing Activities.

![RTCDP](../module6/images/exclatov.png)

Click **+ Create Activity** to create a new Activity.

![RTCDP](../module6/images/exclatcr.png)

Select **Experience Targeting**.

![RTCDP](./images/exclatcrxt.png)

Now select **Visual** and paste your shortened link in the field **Enter Activity URL**. Click **Next**.

![RTCDP](./images/exclatcrxt1.png)

You'll then see your demo website project being loaded in the Visuel Experience Composer.

![RTCDP](./images/vec1.png)

Go to **Browse** mode to click **Allow all** on the cookie consent popup.

![RTCDP](./images/vec2.png)

Click the area which contains the text **Featured Categories**. Click **Insert Before** and then select **Offer Decision**.

![RTCDP](./images/vec3.png)

You'll then see this popup. Select your sandbox `--aepSandboxId--` and then select the placement **Web - Image**.

![RTCDP](./images/vec4.png)

Next, select your decision `--demoProfileLdap-- - Luma Decision`. Click **Save**.

![RTCDP](./images/vec5.png)

You'll then see this. Make sure the add an additional template rule **URL** **contains** **your-project-name**. CLick **Save**.

![RTCDP](./images/vec6.png)

You'll then see this. Click **Next**.

![RTCDP](./images/vec7.png)

Enter a name for your offer, use this name: `--demoProfileLdap-- - XT with Offers (VEC)`. Click **Next**.

![RTCDP](./images/vec8.png)

You'll then see this. Define your **Goal Metric** as indicated. Click **Save & Close**.

![RTCDP](./images/vec9.png)

Your offer is now created and is being published.

![RTCDP](./images/vec10.png)

Once your offer is published, you can enable it.
