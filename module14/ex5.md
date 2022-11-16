---
title: Data Collection & Event Forwarding - Forward events towards the AWS ecosystem
description: Forward events towards the AWS ecosystem
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 3d24e533-6eb4-40a7-a242-ba7f40839665
---
# 14.5 Forward events towards the AWS ecosystem


{% hint style="warning" %}
Completion of this exercise is **optional** and a cost is involved to use AWS Kinesis. While AWS provides a free tier account which lets you test and configure many services without a cost, AWS Kinesis isn't part of that free tier account. So in order to implement and test this exercise, a cost will be involved to use AWS Kinesis.
{% endhint %}

## Good to know

Adobe Experience Platform supports various Amazon services as destination. 
Kinesis and  S3 are both [profile export destinations](https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=en) and can be used as part of Adobe Experience Platform's Real-Time CDP.
You can easily feed high-value segment events and associated profile attributes into your systems of choice.

In this note, you’ll learn how to setup your own Amazon Kinesis stream to stream event data coming from the Adobe Experience Platform Edge ecosystem to a cloud storage destination, such as Amazon S3. This is useful in case you'd like to collect experience events from web and mobile properties and push them into your datalake for analysis and operational reporting. Datalakes generally ingest data in a batch fashion with large daily file imports, they do not expose public http endpoint which could be used in conjunction with event forwarding.

Supporting the above use cases imply that streamed data need to be buffered or placed in a queue before being written to a file. Care has to be taken to not open file for write access across multiple process. Delegating this task to dedicated system is ideal to scale nicely while ensuring a great level of service, this is where Kinesis comes to the rescue.

Amazon Kinesis Data Streams focuses on ingesting and storing data streams. Kinesis Data Firehose focuses on delivering data streams to select destinations, such as S3 buckets. 

As part of this exercise, you'll...

- Perform a basic setup of a Kinesis data stream
- Create a Firehose delivery stream and use S3 bucket as destination
- Configure Amazon API gateway as a rest api endpoint to receive your event data
- Forward raw event data from Adobe's Edge to your Kinesis stream

## 14.5.1 Configure your AWS S3 bucket

Go to [https://console.aws.amazon.com](https://console.aws.amazon.com) and sign in with the Amazon-account you previously created.

![ETL](../module6/images/awshome.png)

After logging in, you'll be redirected to the **AWS Management Console**.

![ETL](../module6/images/awsconsole.png)

In the **Find Services** menu, search for **s3**. Click the first search result: **S3 - Scalable Storage in the Cloud**.

![ETL](../module6/images/awsconsoles3.png)

You'll then see the **Amazon S3** homepage. Click **Create Bucket**.

![ETL](../module6/images/s3home.png)

In the **Create Bucket** screen, you need to configure two things:
  
- Name: use the name `eventforwarding---demoProfileLdap--`. As an example, in this exercise the bucket name is **aepmodulertcdpvangeluw**
- Region: use the region **EU (Frankfurt) eu-central-1**

![ETL](./images/bucketname.png)

Leave all the other default settings as they are. Scroll down and click **Create bucket**.

![ETL](./images/createbucket.png)

You'll then see your bucket being created and will be redirected to the Amazon S3 homepage.

![ETL](./images/S3homeb.png)

## 14.5.2 Configure your AWS Kinesis Data Stream

In the **Find Services** menu, search for **kinesis**. Click the first search result: **Kinesis - Work with Real-Time Streaming Data**.

![ETL](./images/kinesis1.png)

Select **Kinesis Data Streams**. Click **Create data stream**.

![ETL](./images/kinesis2.png)

For the **Data stream name**, use `--demoProfileLdap---datastream`.

![ETL](./images/kinesis3.png)

There's no need to change any of the other settings. Scroll down and click **Create data stream**.

![ETL](./images/kinesis4.png)

You'll then see this. Once your data stream is succesfully created, you can move forward to the next exercise.

![ETL](./images/kinesis5.png)

## 14.5.3 Configure your AWS Firehose Delivery Stream

In the **Find Services** menu, search for **kinesis**. Click **Kinesis Data Firehose**.

![ETL](./images/kinesis6.png)

Click **Create delivery stream**.

![ETL](./images/kinesis7.png)

For **Source**, select **Amazon Kinesis Data Streams**. For **Destination**, select **Amazon S3**. Click **Browse** to select your data stream.

![ETL](./images/kinesis8.png)

Select your data stream. Click **Choose**.

![ETL](./images/kinesis9.png)

You'll then see this. Remember the **Delivery stream name** as you'll need it later.

![ETL](./images/kinesis10.png)

Scroll down until you see **Destination Settings**. Click **Browse** to select your S3 bucket.

![ETL](./images/kinesis11.png)

Select your S3 bucket and click **Choose**.

![ETL](./images/kinesis12.png)

You'll then see something like this. Update the following settings:

- Dynamic partitioning: set to **Enabled**
- Multi record deaggregation: set to **Disabled**
- New line delimiter: set to **Enabled**
- Inline parsing for JSON: set to **Enabled**

![ETL](./images/kinesis13.png)

Scroll down a bit, you'll then see this. Update the following settings:

- Dynamic partitionning keys
  - Key name: **dynamicPartitioningKey**
  - JQ expression: **.dynamicPartitioningKey**
- S3 bucket prefix: add the following code:

```bash
!{partitionKeyFromQuery:dynamicPartitioningKey}/!{timestamp:yyyy}/!{timestamp:MM}/!{timestamp:dd}/!{timestamp:HH}/}
```

- S3 bucket error ouput prefix: set to **error**

![ETL](./images/kinesis14.png)

Finally, scroll down a bit more and click **Create delivery stream**

![ETL](./images/kinesis15.png)

After a couple of minutes, your delivery stream will nbe created and **Active**.

![ETL](./images/kinesis16.png)

## 14.5.4 Configure your AWS IAM Role

In the **Find Services** menu, search for **iam**. Click **API Gateway**.

![ETL](./images/iam1.png)

Click **Roles**.

![ETL](./images/iam2.png)

Search for your **KinesisFirehose** role. Click it to open it.

![ETL](./images/iam3.png)

Click your Permissions Policy name to open it.

![ETL](./images/iam4.png)

In the new screen that opens, click **Edit Policy**.

![ETL](./images/iam5.png)

Under **Kinesis** - **Actions**, ensure that the **Write** permissions for **PutRecord** is enabled. Click **Review Policy**.

![ETL](./images/iam6.png)

Click **Save Changes**.

![ETL](./images/iam7.png)

You'll then be back here. Click **Roles**.

![ETL](./images/iam8.png)

Search for your **KinesisFirehose** role. Click it to open it.

![ETL](./images/iam3.png)

Go to **Trust relationships** and click **Edit trust policy**.

![ETL](./images/iam9.png)

Overwrite the current trust policy by pasting this code to replace the existing code:

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Effect": "Allow",
			"Principal": {
				"Service": [
                    "firehose.amazonaws.com",
                    "kinesis.amazonaws.com",
                    "apigateway.amazonaws.com"
                ]
			},
			"Action": "sts:AssumeRole"
		}
	]
}
```

Click **Update policy**

![ETL](./images/iam10.png)

You'll then see this. You'll need to specify the **ARN** for this role in the next step.

![ETL](./images/iam11.png)

## 14.5.5 Configure your AWS API Gateway

Amazon API Gateway is an AWS service for creating, publishing, maintaining, monitoring, and securing REST, HTTP, and WebSocket APIs at any scale. API developers can create APIs that access AWS or other web services, as well as data stored in the AWS Cloud. 

You will now expose the Kinesis data stream to the internet through a HTTPS endpoint which can then directly be consumed by Adobe services, like Event Forwarding. 

In the **Find Services** menu, search for **api gateway**. Click **API Gateway**.

![ETL](./images/kinesis17.png)

You'll then see something like this. Click **Create API**.

![ETL](./images/kinesis18.png)

Click **Build** on the **REST API** card.

![ETL](./images/kinesis19.png)

You'll then see this. Fill out the settings like this:

- Choose the protocol: select **REST**
- Create new API: select **New API**
- Settings:
  - API name: use `--demoProfileLdap---eventforwarding`
  - Endpoint Type: select **Regional**

Click **Create API**.

![ETL](./images/kinesis20.png)

You'll then see this. Click **Actions** and then click **Create Resource**.

![ETL](./images/kinesis21.png)

You'll then see this. Set **Resource Name** to **stream**. Click **Create Resource**.

![ETL](./images/kinesis22.png)

You'll then see this. Click **Actions** and then click **Create Method**.

![ETL](./images/kinesis23.png)

In the dropdown, select **POST** and click the **v** button.

![ETL](./images/kinesis24.png)

You'll then see this. Fill out the settings like this:

- Integration type: **AWS Service**
- AWS Region: select the region that is used by your Kinesis Data Stream, in this case: **us-west-2**
- AWS Service: select **Kinesis**
- AWS Subdomain: leave empty
- HTTP Method: select **POST**
- Action Type: select **Use action name**
- Action: enter **PutRecord**
- Execution role: paste the **ARN** of the execution role that is used by your Kinesis Data Firehose, as instructed in the previous exercise
- Content Handling: select **Passthrough**
- Use Default Timeout: enable the checkbox

Click **Save**.

![ETL](./images/kinesis25.png)

You'll then see this. Click **Integration Request**.

![ETL](./images/kinesis27.png)

Click **HTTP Headers**.

![ETL](./images/kinesis28.png)

Scroll down a bit and click **Add header**.

![ETL](./images/kinesis29.png)

Set **Name** to **Content-Type**, set **Mapped from** to `'application/x-amz-json-1.1'`. Click the **v** icon to save your changes.

![ETL](./images/kinesis30.png)

You'll then see this. For **Request body passthrough**, select **When there are no templates defined (recommended)**. Next, click **Add mapping template**.

![ETL](./images/kinesis31.png)

Under **Content-Type**, enter **application/json**. Click the **v** icon to save your changes.

![ETL](./images/kinesis32.png)

Scroll down to find a code editor window. Paste the below code in there:

```json
{
  "StreamName": "$input.path('StreamName')",
  "Data": "$util.base64Encode($input.json('$.Data'))",
  "PartitionKey": "$input.path('$.PartitionKey')"
}
```

Click **Save**.

![ETL](./images/kinesis33.png)

Next, scroll up and click **<- Method Execution** to go back.

![ETL](./images/kinesis34.png)

Click **TEST**.

![ETL](./images/kinesis35.png)

Scroll down, and paste this code under **Request Body**. Click **Test**.

```json
{
  "Data": {
    "message": "Hello World",
    "dynamicPartitioningKey": "v2"
  },
  "PartitionKey": "1",
  "StreamName": "--demoProfileLdap---datastream"
}
```

![ETL](./images/kinesis36.png)

You'll then see a similar result:

![ETL](./images/kinesis37.png)

You'll then see this. Click **Actions** and then click **Deploy API**.

![ETL](./images/kinesis38.png)

For **Deployment stage**, select **New Stage**. As **Stage name**, enter **prod**. Click **Deploy**.

![ETL](./images/kinesis39.png)

You'll then see this. Click **Save Changes**. FYI: the URL in the image is the URL to use to send data towards (in this example: https://vv1i5vwg2k.execute-api.us-west-2.amazonaws.com/prod).

![ETL](./images/kinesis40.png)

You can test your setup by using the below cURL request, all you need to do is replace the below URL by yours, `https://vv1i5vwg2k.execute-api.us-west-2.amazonaws.com/prod` in this example, and add `/stream` at the end of the URL.

```json
curl --location --request POST 'https://vv1i5vwg2k.execute-api.us-west-2.amazonaws.com/prod/stream' \
--header 'Content-Type: application/json' \
--data-raw '{
    "Data": {
        "userid": "--demoProfileLdap--@adobe.com",
        "firstName":"--demoProfileLdap--",
        "offerName":"10% off on outdoor gears",
        "offerCode": "10OFF-SPRING",
        "dynamicPartitioningKey": "campaign"
    },
    "PartitionKey": "1",
    "StreamName": "--demoProfileLdap---datastream"
}'
```

Paste the above updated code in a Terminal window, and hit enter. You'll then see this response, similar to the response you could see when testing above.

![ETL](./images/kinesis41.png)

## 14.5.6 Update your Event Forwarding property

You can now activate to your AWS Kinesis data stream through AWS API Gateway, so you can now send your raw experience events into the AWS ecosystem. Using Real-Time CDP Connections and Event Forwarding, you can now easily enable event forwarding to your newly created AWS API Gateway endpoint. 

### 14.5.6.1 Update your Event Forwarding property: Create a Data Element

Go to [https://experience.adobe.com/#/data-collection/](https://experience.adobe.com/#/data-collection/) and go to **Event Forwarding**. Search your Event Forwarding property and click it to open it.

![Adobe Experience Platform Data Collection SSF](./images/prop1.png)

In the left menu, go to **Data Elements**. Click **Add Data Element**.

![Adobe Experience Platform Data Collection SSF](./images/deaws1.png)

You'll then see a new data element to configure.

![Adobe Experience Platform Data Collection SSF](./images/de2.png)

Make the following selection:

- As the **Name**, enter **awsDataObject**.
- As the **Extension**, select **Core**.
- As the **Data Element Type**, select **Custom Code**.

You'll now have this. Click **</> Open Editor**.

![Adobe Experience Platform Data Collection SSF](./images/deaws3.png)

In the Editor, paste the following code on line 3. Click **Save**.

```javascript
const newObj = {...arc.event.xdm, dynamicPartitioningKey: "event_forwarding"}
return JSON.stringify(newObj);
```

![Adobe Experience Platform Data Collection SSF](./images/deaws4.png)


{% hint style="info" %}
In the above path, a reference is made to **arc**. **arc** stands for Adobe Resource Context and **arc** always stands for the highest available object that is available in the Server Side context. Enrichments and transformations may be added to that **arc** object using Adobe Experience Platform Data Collection Server functions.

In the above path, a reference is made to **event**. **event** stands for a unique event and Adobe Experience Platform Data Collection Server will always evaluate every event individually. Sometimes, you may see a reference to **events** in the payload sent by Web SDK Client Side, but in Adobe Experience Platform Data Collection Event Forwarding, every event is evaluated individually.
{% endhint %}

You'll then be back here. Click **Save** or **Save to Library**.

![Adobe Experience Platform Data Collection SSF](./images/deaws5.png)

### 14.5.6.2  Update your Adobe Experience Platform Data Collection Server property: Update your Rule

In the left menu, go to **Rules**. Click to open the rule **All Pages** which you created in one of the previous exercises.

![Adobe Experience Platform Data Collection SSF](./images/rlaws1.png)

You'll then see this. Click the **+** icon to add a new action.

![Adobe Experience Platform Data Collection SSF](./images/rlaws2.png)

You'll then see this. Make the following selection:

- Select the **Extension**: **Adobe Cloud Connector**.
- Select the **Action Type**: **Make Fetch Call**.

That should give you this **Name**: **Adobe Cloud Connector - Make Fetch Call**. You should now see this:

![Adobe Experience Platform Data Collection SSF](./images/rl4.png)

Next, configure the following:

- Change the request method from GET to **POST**
- Enter the URL of the AWS API Gateway endpoint you created in one of the previous steps, which looks like this: `https://vv1i5vwg2k.execute-api.us-west-2.amazonaws.com/prod/stream`

You should now have this. Next, go to **Headers**.

![Adobe Experience Platform Data Collection SSF](./images/rlaws5.png)

Under headers, add a new header with key **Content-Type** and value **application/json**. Next, go to **Body**.

![Adobe Experience Platform Data Collection SSF](./images/rlaws5a.png)

You'll then see this. Paste the following code in the field **Body (Raw)**. Click **Keep Changes**.

```json
{
    "Data":{{awsDataObject}},
    "PartitionKey": "1",
    "StreamName": "--demoProfileLdap---datastream"
}
```

![Adobe Experience Platform Data Collection SSF](./images/rlaws7.png)

You'll then see be back here. Click **Save** or **Save to Library**.

![Adobe Experience Platform Data Collection SSF](./images/rlaws10.png)

You've now configured your first rule in an Event Forwarding property. Go to **Publishing Flow** to publish your changes.
Open your Development library by clicking **Main**.

![Adobe Experience Platform Data Collection SSF](./images/rlaws11.png)

Click the **Add All Changed Resources** button, after which you'll see your Rule and Data Element changes appear in this library. Next, click **Save & Build for Development**. Your changes are now being deployed.

![Adobe Experience Platform Data Collection SSF](./images/rlaws13.png)

After a couple of minutes, you'll see that the deployment is done and ready to be tested.

![Adobe Experience Platform Data Collection SSF](./images/rl14.png)

## 14.5.7 Test your configuration

Go to [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). After logging in with your Adobe ID, you'll see this. Click your website project to open it.

![DSN](../images/web8.png)

You can now follow the below flow to access the website. Click **Integrations**.

![DSN](../images/web1.png)

On the **Integrations** page, you need to select the Data Collection property that was created in exercise 0.1. 

![DSN](../images/web2.png)

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

When you open up your browser Developer View, you can inspect Network requests as indicated below. When you use the filter **interact**, you'll see the network requests that are sent by Adobe Experience Platform Data Collection Client to the Adobe Edge.

![Adobe Experience Platform Data Collection Setup](./images/hook1.png)

If you select the raw payload, go to [https://jsonformatter.org/json-pretty-print](https://jsonformatter.org/json-pretty-print) and paste the payload. Click **Make Pretty**. You'll then see the JSON payload, the **events** object and the **xdm** object. In one of the previous steps, when you defined the Data Element, you used the reference **arc.event.xdm**, which will result in you parsing out the **xdm** object of this payload.

![Adobe Experience Platform Data Collection Setup](./images/hook2.png)

Switch your view to **AWS**. By opening your data stream and going into the **Monitoring** tab, you'll now see incoming traffic.

![Adobe Experience Platform Data Collection Setup](./images/hookaws3.png)

When you then open your delivery stream and go into the **Monitoring** tab, you'll also see incoming traffic.

![Adobe Experience Platform Data Collection Setup](./images/hookaws4.png)

Finally, when you have a look at your S3 bucket, you'll now notice files being created there as a consequence of your data ingestion.

![Adobe Experience Platform Data Collection Setup](./images/hookaws5.png)

When you download such a file and open it using a text editor, you'll see that it contains the XDM payload from the events that were forwarded.

![Adobe Experience Platform Data Collection Setup](./images/hookaws6.png)
