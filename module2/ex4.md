---
title: Foundation - Data Ingestion - Data Ingestion from Offline Sources
description: Foundation - Data Ingestion - Data Ingestion from Offline Sources
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 0d79f013-042a-4d2e-a031-c81319a8955d
---
# 2.4 Data Ingestion from Offline Sources

In this exercise, the goal is to onboard external data like CRM Data in Platform.

## Learning Objectives

- Learn how to generate test data
- Learn how to ingest CSV
- Learn how to use the web UI for data ingestion through Workflows
- Understand the data governance features of Experience Platform

## Resources

- Mockaroo UI: [https://www.mockaroo.com/](https://www.mockaroo.com/)
- Experience Platform UI: [https://experience.adobe.com/platform/](https://experience.adobe.com/platform/)

## Tasks

- Create a CSV file with demo date. Ingest the CSV file in Adobe Experience Platform by making use of the available workflows.
- Understand data governance options in Adobe Experience Platform

## 2.4.1 Create your CRM Dataset through a data generator tool

For this you need 1000 sample lines of CRM Data.

Open the Mockaroo Template by going to [https://www.mockaroo.com/12674210](https://www.mockaroo.com/12674210).

![Data Ingestion](./images/mockaroo.png)

On the template, you'll notice the following fields:

- id
- first_name
- last_name
- email
- gender
- birthDate
- home_latitude
- home_longitude
- country_code
- city
- country

All these fields have been defined to produce data that is compatible with Platform. 

To generate your CSV-file, click the **Download Data** button which will give you a CSV-file with 1000 lines of demo-data. 

![Data Ingestion](./images/dd.png)

Open your CSV-file in Microsoft Excel to visualize its contents.

![Data Ingestion](./images/excel.png)

With your CSV-file ready, you can proceed with mapping it against XDM.

### 2.4.2 Verify the CRM Onboarding Dataset in Adobe Experience Platform

Open [Adobe Experience Platform](https://experience.adobe.com/platform) and go to **Datasets**. 

Before you continue, you need to select a **sandbox**. The sandbox to select is named ``--module2sandbox--``. You can do this by clicking the text **Production Prod** in the blue line on top of your screen. After selecting the appropriate sandbox, you'll see the screen change and now you're in your dedicated sandbox.

![Data Ingestion](./images/sb1.png)

In Adobe Experience Platform, click on **Datasets** in the menu on the left side of your screen.

![Data Ingestion](./images/menudatasetssb.png)

You're going to use a shared dataset based in this enablement. The shared dataset has been created already and is called **Demo System - Profile Dataset for CRM (Global v1.1)**. 

![Data Ingestion](./images/emeacrm.png)

Open the dataset **Demo System - Profile Dataset for CRM (Global v1.1)**.

![Data Ingestion](./images/emeacrmoverview.png)

On the overview screen, you can see 3 main pieces of information.

![Data Ingestion](./images/dashboard.png)

First of all, the Dataset Activity dashboard shows the total number of CRM records in the dataset and the ingested batches and their status

![Data Ingestion](./images/batchids.png)

Second, by scrolling down on the page you can check when batches of data were ingested, how many records were onboarded and also, whether or not the batch was successfully onboarded. The **Batch ID** is the identifier for a specific batch job, and the **Batch ID** is important as it can be used for troubleshooting why a specific batch was not successfully onboarded. 

![Data Ingestion](./images/datasetsettings.png)

Lastly, the Dataset Info tab shows important information like the Dataset ID (again, important from a troubleshooting perspective), the Dataset's Name and whether the dataset was enabled for Profile. 

![Data Ingestion](./images/ds_ups_link.png)

The most important setting here is the link between the dataset and the Schema. The Schema defines what data can be ingested and how that data should look like. 

In this case, we're using the **Demo System - Profile Schema for CRM (Global v1.1)**, which is mapped against the class of **Profile** and has implemented extensions, also called field groups. 

![Data Ingestion](./images/ds_schemalink.png)

By clicking on the name of the schema, you're taken to the Schema overview were you can see all the fields that have been activated for this schema.

![Data Ingestion](./images/schemads.png)

Every schema needs to have a custom, primary descriptor defined. In the case of our CRM dataset, the schema has defined that the field **crmId** should be the primary identifier. If you want to create a schema and link it to the Real-time Customer Profile, you need to define a custom Field Group that refers to your primary descriptor.

![Data Ingestion](./images/schema_descriptor.png)

In the above screenshot, you can see that our descriptor is located in `--aepTenantId--.identification.core.crmId`, which is set as the Primary Identifier, linked to the namespace of **Demo System - CRMID**.

Every schema and as such, every dataset that should be used in the Real-time Customer Profile should have one Primary identifier. This Primary identifier is the identifier user by the brand for a customer in that dataset. In the case of a CRM dataset it might be the email-address or the CRM ID, in the case of a Call Center dataset it might be the mobile number of a customer.

It is best practice to create a separate, specific schema for every dataset and to set the descriptor for every dataset specifically to match how the current solutions used by the brand operate.

### 2.4.3 Using a workflow to map a CSV file to an XDM Schema

The goal of this is to onboard CRM data in Platform. All the data that is ingested in Platform should be mapped against the specific XDM Schema. What you currently have is a CSV dataset with 1000 lines on the one side, and a dataset that is linked to a schema on the other side. To load that CSV file in that dataset, a mapping needs to take place. To facilitate this mapping exercise, we have **Workflows** available in Adobe Experience Platform.

![Data Ingestion](./images/workflows.png)

The workflow that we'll use here, is the workflow named **Map CSV to XDM Schema** in the Data Ingestion menu.

Click the **Map CSV to XDM Schema** button. Click **Launch** to start the process.

![Data Ingestion](./images/mapcsvxdm.png)

On the next screen, you need to select a dataset to ingest your file in. You have the choice between selecting an already existing dataset or creating a new one. For this exercise, we'll reuse an existing one: please select **Demo System - Profile Dataset for CRM (Global v1.1)** as indicated below and leave the other settings set to default.

![Data Ingestion](./images/datasetselection.png)

Click **Next** to go to the next step.

![Data Ingestion](./images/next.png)

Drag & Drop your CSV-file or click **Browse** and navigate on your computer to your desktop and select your CSV-file.

![Data Ingestion](./images/dragdrop.png)

After selecting your CSV-file it will upload immediately and you will see a preview of your file within seconds.

![Data Ingestion](./images/previewcsv.png)

Click **Next** to go to the next step. It can take a few seconds while the file is processed completely.

![Data Ingestion](./images/next.png)

You now need to map your CSV Column Headers with an XDM-property in your **Demo System - Profile Dataset for CRM**.

Adobe Experience Platform has already made some proposals for you, by trying to link the Source Attributes with the Target Schema Fields.

![Data Ingestion](./images/mapschema.png)

For the Schema Mappings, Adobe Experience Platform has tried to link fields together already. However, not all proposals of mapping are correct. You now need to **Accept target fields** one-by-one.

#### birthDate

The Source Schema field **birthDate** should be linked to the target field **person.birthDate**. 

![Data Ingestion](./images/tfbd.png)

#### city

The Source Schema field **city** should be linked to the target field **homeAddress.city**. 

![Data Ingestion](./images/tfcity.png)

#### country

The Source Schema field **country** should be linked to the target field **homeAddress.country**. 

![Data Ingestion](./images/tfcountry.png)

#### country_code

The Source Schema field **country_code** should be linked to the target field **homeAddress.countryCode**.  

![Data Ingestion](./images/tfcountrycode.png)

#### email

The Source Schema field **email** should be linked to the target field **personalEmail.address**. 

![Data Ingestion](./images/tfemail.png)

#### crmid

The Source Schema field ** crmid** should be linked to the target field **`--aepTenantId--`.identification.core.crmId**. 

![Data Ingestion](./images/tfemail1.png)

#### first_name

The Source Schema field **first_name** should be linked to the target field **person.name.firstName**. 

![Data Ingestion](./images/tffname.png)

#### gender

The Source Schema field **gender** should be linked to the target field **person.gender**. 

![Data Ingestion](./images/tfgender.png)

#### home_latitude

The Source Schema field **home_latitude** should be linked to the target field **homeAddress._schema.latitude**. 

![Data Ingestion](./images/tflat.png)

#### home_longitude

The Source Schema field **home_longitude** should be linked to the target field **homeAddress._schema.longitude**.  

![Data Ingestion](./images/tflon.png)

#### id

The Source Schema field **id** should be linked to the target field **_id**. 

![Data Ingestion](./images/tfid1.png)

#### last_name

The Source Schema field **last_name** should be linked to the target field **person.name.lastName**. 

![Data Ingestion](./images/tflname.png)

You should now have this:

![Data Ingestion](./images/overview.png)

Click the **Finish** button to finish the workflow.

![Data Ingestion](./images/finish.png)

After clicking **Finish**, you'll then see the **Dataflow** overview, and after a couple of minutes you can refresh your screen to see if your workflow completed successfully. Click your **Target dataset name**. 

![Data Ingestion](./images/dfsuccess.png)

You'll then see the dataset where your ingestion has processed.

![Data Ingestion](./images/ingestdataset.png)

On the dataset, you'll see a Batch ID that has been ingested just now, with 1000 records ingested and a status of **Success**.

![Data Ingestion](./images/batchsuccess1.png)

Click on the **Preview Dataset**- button to get a quick view of a small sample of the dataset to ensure that the loaded data is correct.

![Data Ingestion](./images/preview.png)

![Data Ingestion](./images/previewdata.png)

Once data is loaded, you can define the correct data governance approach for our dataset.
   
### 2.5.4 Adding data governance to your dataset 

Now that your customer data is ingested, you need to make sure that this dataset is properly governed for usage and export control. Click on the **Data Governance** tab and observe that you can set three types of restrictions: Contractual, Identity, and Sensitive Data.

You can find more info on the different labels and how they will be enforced in the future through the policy framework on this link: [https://www.adobe.io/apis/experienceplatform/home/dule/duleservices.html](https://www.adobe.io/apis/experienceplatform/home/dule/duleservices.html) 
 
![Data Ingestion](./images/dsgovernance.png)

Let's restrict identity data for the entire dataset. Hover over your dataset name, and click the Pencil icon to edit the settings. 

![Data Ingestion](./images/pencil.png)

Go to **Identity Data** and you'll see that the **I2** option is checked - this will assume that all pieces of information in this dataset are at least indirectly identifiable to the person.

![Data Ingestion](./images/identity.png)

Click **Save Changes** and observe that **I2** is now set for all data fields in the dataset. 

You can also set these flags for individual data fields - for example, the **firstName** field is likely to be classified as an **I1** level for directly identifiable information.

Select the field **firstName** by checking the checkbox and click on **Edit Governance Labels** in the upper right corner of your screen.

![Data Ingestion](./images/editfirstname.png)

Go to **Identity Data** and you'll see that the **I2** option is already checked (inherited from the dataset). The field firstName also has a field-specific configuration and is set as **I1 - Directly Identifiable Data**.

![Data Ingestion](./images/fndii.png)

With this, you've now successfully ingested and classified CRM Data in Adobe Experience Platform.
