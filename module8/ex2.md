---
title: Adobe Journey Optimizer - External Weather API, SMS Action & more - Define an external data source
description: Adobe Journey Optimizer - External Weather API, SMS Action & more - Define an external data source
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: e3e04415-4258-4ad7-a227-0e68dfcba235
---
# 8.2 Define an external data source

In this exercise, you'll create a custom external data source by making use of Adobe Journey Optimizer.

Login to Adobe Journey Optimizer by going to [Adobe Experience Cloud](https://experience.adobe.com). Click **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

You'll be redirected to the **Home**  view in Journey Optimizer. First, make sure you're using the correct sandbox. The sandbox to use is called `--aepSandboxId--`. To change from one sandbox to another, click on **PRODUCTION Prod (VA7)** and select the sandbox from the list. In this example, the sandbox is named **AEP Enablement FY22**. You'll then be in the **Home** view of your sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

In the left menu, scroll down and click **Configurations**. Next, click the **Manage** button under **Data Sources**.

![Demo](./images/menudatasources.png)

You'll then see the **Data Sources** list.
Click **Create Data Source** to start adding your data source.

![Demo](./images/dshome.png)

You'll see an empty data source popup.

![Demo](./images/emptyds.png)

Before you can start configuring this, you'll need an account with the **Open Weather Map** service. Follow these steps to create your account and get your API key.

Go to [https://openweathermap.org/](https://openweathermap.org/). On the homepage, click **Sign In**.

![WeatherMap](./images/owm.png)

Click **Create an Account**.

![WeatherMap](./images/owm1.png)

Fill out the details.

![WeatherMap](./images/owm2.png)

Click **Create Account**.

![WeatherMap](./images/owm3.png)

You'll then be redirected to your Account Page.

![WeatherMap](./images/owm4.png)

In the menu, click **API Keys** to retrieve your API Key, which you'll need to setup your custom external data source.

![WeatherMap](./images/owm5.png)

An **API Key** looks like this: `b2c4c36b6bb59c3458d6686b05311dc3`.

You can find the **API Documentation** for the **Current Weather** [here](https://openweathermap.org/current).

In our use-case, we'll implement the connection with Open Weather Map based on the city the customer is in.

![WeatherMap](./images/owm6.png)

Go back to **Adobe Journey Optimizer**, to your empty **External Data Source** popup.

![Demo](./images/emptyds.png)

As a Name for the data source, use `--demoProfileLdap--WeatherApi`. In this example, the data source Name is `vangeluwWeatherApi `.

Set Description to: `Access to the Open Weather Map`.

The URL for the Open Weather Map API is: **http://api.openweathermap.org/data/2.5/weather?units=metric**

![Demo](./images/dsname.png)

Next, you need to select the Authentication to use.

Use these variables:

| Field               | Value              |
|:-----------------------:| :-----------------------|
| Type            |**API key**            |
| Name           | **APPID**         |
| Value           | **your API Key**         |
| Location           | **Query Parameter**         |

![Demo](./images/dsauth.png)

Finally, you need to define a **FieldGroup**, which is basically the request you'll be sending to the Weather API. In our case, we want to use the name of the City to request the Current Weather for that City.

![Demo](./images/fg.png)

According to the Weather API Documentation, we need to send a parameter `q=City`.

![Demo](./images/owmapi.png)

In order to match the expected API Request, configure your FieldGroup as follows:


{% hint style="warning" %}
The Field group name has to be unique, please use this naming convention: `--demoProfileLdap--WeatherByCity` so in this case, the name should be `vangeluwWeatherByCity`
{% endhint %}

![Demo](./images/fg1.png)

For the Response Payload, you need to paste an example of the Response that will be sent by the Weather API.

You can find the expected API JSON Response on the API Documentation page [here](https://openweathermap.org/current).

![Demo](./images/owmapi1.png)

Or you can copy the JSON Response from here:

```json
{"coord": { "lon": 139,"lat": 35},
  "weather": [
    {
      "id": 800,
      "main": "Clear",
      "description": "clear sky",
      "icon": "01n"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 281.52,
    "feels_like": 278.99,
    "temp_min": 280.15,
    "temp_max": 283.71,
    "pressure": 1016,
    "humidity": 93
  },
  "wind": {
    "speed": 0.47,
    "deg": 107.538
  },
  "clouds": {
    "all": 2
  },
  "dt": 1560350192,
  "sys": {
    "type": 3,
    "id": 2019346,
    "message": 0.0065,
    "country": "JP",
    "sunrise": 1560281377,
    "sunset": 1560333478
  },
  "timezone": 32400,
  "id": 1851632,
  "name": "Shuzenji",
  "cod": 200
}
```

Copy the above JSON Response to your clipboard, then go to your custom data source configuration screen.

Click the **Edit Payload** icon.

![Demo](./images/owmapi2.png)

You'll see a popup where you now have to paste the above JSON Response.

![Demo](./images/owmapi3.png)

Paste your JSON Response, after which you'll see this. Click **Save**.

![Demo](./images/owmapi4.png)

Your custom data source configuration is now complete. Scroll up and click **Save**.

![Demo](./images/dssave.png)

Your data source has now been created successfully and is part of the **Data Sources** list.

![Demo](./images/dslist.png)
