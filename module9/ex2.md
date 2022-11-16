---
title: Offer Decisioning - Configure your Offers and Decision ID
description: Offer Decisioning - Configure your Offers and Decision ID
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 4b2c2753-8b7e-496e-9fb5-3ccb9f6a10ef
---
# 9.2 Configure your offers and decision

## 9.2.1 Create your personalized offers

In this exercise, you'll create four **Personalized Offers**. Here are the details to take into account when creating those offers:

|Name | Date Range | Image Link for Email | Image Link for Web | Text | Priority | Eligibility  | Language| 
|-----|------------|----------------------|--------------------|------|:--------:|--------------|:-------:|
|`--demoProfileLdap-- - Nadia Elements Shell` | today - 1 month later | https://bit.ly/3nPiwdZ | https://bit.ly/2INwXjt |`{{ profile.person.name.firstName }}, 10% discount on Nadia Elements Shell`| 25 | all - Female Customers   | English (United States) | 
|`--demoProfileLdap-- - Radiant Tee` | today - 1 month later  | https://bit.ly/2HfA17v |https://bit.ly/3pEIdzn|`{{ profile.person.name.firstName }}, 5% discount on Radiant Tee`| 15 | all - Female Customers   | English (United States) |
|`--demoProfileLdap-- - Zeppelin Yoga Pant` | today - 1 month later | https://bit.ly/2IOaItW | https://bit.ly/2INZHZd|`{{ profile.person.name.firstName }}, 10% discount on Zeppelin Yoga Pant`| 25 | all - Male Customers | English (United States) |
|`--demoProfileLdap-- - Proteus Fitness Jackshirt` | today - 1 month later | https://bit.ly/330a43n |https://bit.ly/36USaQW| `{{ profile.person.name.firstName }}, 5% discount on Proteus Fitness Jackshirt`| 15 | all - Male Customers  | English (United States) |


Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

In the left menu, click **Offers** and then go to **Offers**. Click **+ Create Offer**.

![Decision Rule](./images/offers1.png)

You'll then see this popup. Select **Personalized offer** and click **Next**.

![Decision Rule](./images/offers2.png)

You're now on the **Details** view. 

![Decision Rule](./images/offers3.png)

In this case, you need to configure the offer `--demoProfileLdap-- - Nadia Elements Shell`. Use the information in the table above to fill out the fields. In this example, the name of the Personalized Offer is **vangeluw - Nadia Elements Shell**. Also, set the **Start date and time** to yesterday, and set the **End date and time** to a date in a month from now.

Once done, you should have this. Click **Next**.

![Decision Rule](./images/offers4.png)

You now need to create **Representations**. Representations are a combination of a **Placement** and a real asset.

For **Representation 1**, select:

- Channel: Web
- Placement: Web - Image
- Content: URL
- Public location: copy the URL from the column **Image Link for Web** in the above table

![Decision Rule](./images/addcontent1.png)

Alternatively, you can select **Asset library** for the content and then click **Browse**.

![Decision Rule](./images/addcontent2.png)

You'll then see a popup of the Assets Library, go to the folder **enablement-assets** and select the image file **nadia-web.png**. Then, click **Select**.

![Decision Rule](./images/addcontent3.png)

You'll then see this:

![Decision Rule](./images/addcontentrep20.png)

Click **+ Add Representation**.

![Decision Rule](./images/addrep.png)

For **Representation 2**, select:

- Channel: Email
- Placement: Email - Image
- Content: URL
- Public location: copy the URL from the column **Image Link for Email** in the above table

![Decision Rule](./images/addcontentrep21.png)

Alternatively, you can select **Asset library** for the content and then click **Browse**.

![Decision Rule](./images/addcontent2b.png)

You'll then see a popup of the Assets Library, go to the folder **enablement-assets** and select the image file **nadia-email.png**. Then, click **Select**.

![Decision Rule](./images/addcontent3b.png)

You'll then see this:

![Decision Rule](./images/addcontentrep20b.png)

Next, click **+ Add representation**.

![Decision Rule](./images/addrep.png)

For **Representation 3**, select:

- Channel: Non-digital
- Placement: Non-digital - Text

Next, you need to add content. In this case that means adding the text to be used as a call to action.

Click **Add Content**.

![Decision Rule](./images/addcontentrep31.png)

You'll then see this popup.

![Decision Rule](./images/addcontent3text.png)

Select **Custom text** and fill out these fields:

Look at the **Text** field from the above table and enter that text here, in this case: `{{ profile.person.name.firstName }}, 10% discount on Nadia Elements Shell`.

You'll also notice that you can select any profile attribute and include it as a dynamic field in the offer text. In this example, the field `{{ profile.person.name.firstName }}` will ensure that the first name of the customer that will receive this offer will be included in the offer text.

You'll then see this. Click **Save**.

![Decision Rule](./images/addcontentrep3text.png)

You now have this. Click **Next**.

![Decision Rule](./images/addcontentrep3textdone.png)

You'll then see this:

![Decision Rule](./images/constraints.png)

Select **By defined decision rule** and click the **+** icon to add the rule **all - Female Customers**.

![Decision Rule](./images/constraints1.png)

You'll then see this. Fill out the **Priority** as indicated in the above table. Click **Next**.

![Decision Rule](./images/constraints2.png)

You'll then see an overview of your new **Personalized Offer**.

![Decision Rule](./images/offeroverview.png)

Finally, click **Save and approve**.

![Decision Rule](./images/saveapprove.png)

You'll then see your newly created Personalized Offer become available in the Offers Overview:

![Decision Rule](./images/offeroverview1.png)

You should now repeat the above steps to create the three other Personalized Offers for the products Radiant Tee, Zeppelin Yoga Pant and Proteus Fitness Jackshirt.

When done, your **Offer Overviews** screen for **Personalized Offers** should show all your offers.

![Final Offers](./images/finaloffers.png)

## 9.2.2 Create your fallback offer

After having created four Personalized Offers, you should now configure a **Fallback Offer**.

Make sure you're in the **Offers** view:

![Final Offers](./images/finaloffers.png)

Click **+ Create Offer**.

![Decision Rule](./images/createoffer.png)

You'll then see this popup. Select **Fallback offer** and click **Next**.

![Decision Rule](./images/foffers2.png)

You'll then see this:

![Decision Rule](./images/foffers3.png)

Enter this name for your fallback offer: `--demoProfileLdap-- - Luma Fallback Offer`. Click **Next**.

![Decision Rule](./images/foffers4.png)

You now need to create **Representations**. Representations are a combination of a **Placement** and a real asset.

For **Representation 1**, select:

- Channel: Web
- Placement: Web - Image
- Content: URL
- Public location: `https://bit.ly/3nBOt9h`

![Decision Rule](./images/addcontent1fb.png)

Alternatively, you can select **Asset library** for the content and then click **Browse**.

![Decision Rule](./images/addcontent2fb.png)

You'll then see a popup of the Assets Library, go to the folder **enablement-assets** and select the image file **spriteyogastraps-web.png**. Then, click **Select**.

![Decision Rule](./images/addcontent3fb.png)

You'll then see this:

![Decision Rule](./images/addcontentrep20fb.png)

For **Representation 2**, select:

- Channel: Email
- Placement: Email - Image
- Content: URL
- Public location: `https://bit.ly/3nF4qvE`

![Decision Rule](./images/addcontentrep21fb.png)

Alternatively, you can select **Asset library** for the content and then click **Browse**.

![Decision Rule](./images/addcontent2bfb.png)

You'll then see a popup of the Assets Library, go to the folder **enablement-assets** and select the image file **spriteyogastraps-email.png**. Then, click **Select**.

![Decision Rule](./images/addcontent3bfb.png)

You'll then see this:

![Decision Rule](./images/addcontentrep20bfb.png)

Next, click **+ Add representation**.

![Decision Rule](./images/addrep.png)

For **Representation 3**, select:

- Channel: Non-digital
- Placement: Non-digital - Text

Next, you need to add content. In this case that means adding the Image Link.

Click **Add Content**.

![Decision Rule](./images/addcontentrep21text.png)

You'll then see this popup.

![Decision Rule](./images/addcontent2text.png)

Select **Custom text** and fill out these fields:

Enter the text `{{ profile.person.name.firstName }}, discover our Sprite Yoga Straps!` and click **Save**.

![Decision Rule](./images/faddcontent3text.png)

You'll then see this. Click **Next**.

![Decision Rule](./images/faddcontentrep3.png)

You'll then see an overview of your new **Fallback Offer**. Click **Finish**.

![Decision Rule](./images/fofferoverview.png)

Finally, click **Save and approve**.

![Decision Rule](./images/saveapprovefb.png)

In your **Offer Overviews** screen, you'll now see this:

![Final Offers](./images/ffinaloffers.png)

## 9.2.3 Create your collection

A Collection is used to **filter** out a sub-set of offers from the personalized offer list and use that as part of an Decision in order to speed up the decision process. 

Go to **Collections**. Click **+ Create Collection**.

![Decision Rule](./images/collections.png)

You'l then see this popup. Configure your Collection like this. Click **Next**.

- Collection name: use `--demoProfileLdap-- - Luma Collection`
- Select **Create static collection**.

![Decision Rule](./images/createcollectionpopup1.png)

In the next screen, select the four **Personalized Offers** you created in the previous exercise. Click **Save**.

![Decision Rule](./images/createcollectionpopup2.png)

You'll now see this:

![Decision Rule](./images/colldone.png)

## 9.2.4 Create your decision

A Decision combines Placements, a Collection of Personalized Offers and a Fallback Offer to ultimately be used by the Offer Decisioning engine to find the best offer for a specific profile, based on each of the individual personalized offer characteristics like priority, eligibility constraint and total / user capping.

To configure your **Decision**, go to **Decisions**. Click **+ Create Activity**.

![Decision Rule](./images/activitydd.png)

You'll then see this:

![Decision Rule](./images/activity1.png)

Fill out the fields like this. Click **Next**.

- Name: `--demoProfileLdap-- - Luma Decision`
- Start date and time: yesterday
- End date and time: today + 1 month

![Decision Rule](./images/activity2.png)

In the next screen, you need to add placements into decision scopes. You'll need to create decision scopes for the placements **Web - Image**, **Email - Image** and **Non-digital - Text**.

![Decision Rule](./images/addplacements.png)

First, create the decision scope for **Non-digital - Text** by selecting that placement in the dropdown. Then, click the **Add** button to add evaluation criteria.

![Decision Rule](./images/activity3.png)

Select your collection `--demoProfileLdap-- - Luma Collection` and click **Add**.

![Decision Rule](./images/activity4text.png)

You'll then see this. Click the **-** button to add a new decision scope.

![Decision Rule](./images/activity5text.png)

Select the placement **Web - Image** and add your collection `--demoProfileLdap-- - Luma Collection` under evaluation criteria. Then, click the **+** button again to add a new decision scope.

![Decision Rule](./images/activity6text.png)

Select the placement **Email - Image** and add your collection `--demoProfileLdap-- - Luma Collection` under evaluation criteria. Then, click **Next**.

![Decision Rule](./images/activity4.png)

You now need to select your **Fallback Offer**, which is named `--demoProfileLdap-- - Luma Fallback Offer`. Click **Next**.

![Decision Rule](./images/activity10.png)

Review your decision. Click **Finish**.

![Decision Rule](./images/activity11.png)

In the popup, click **Save and activate**.

![Decision Rule](./images/activity12.png)

And finally, you'll now see your decision in the overview:

![Decision Rule](./images/activity13.png)

You've now successfully configured your decision. Your decision is now live, and can be used to deliver optimized and personalized offers to your customers, in real-time.
