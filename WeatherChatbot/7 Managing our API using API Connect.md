# 7 Managing our API using API Connect
Now it is the time to configure our facade API in API Connect, let’s go there and do some API Management.

We want to be able to add security, define some rate-limiting plans and publish the API to a secure gateway.

In addition we want to be able to use a self-service portal so that consumers can browse our APIs and sign up to use them.

Using the hamburger menu, click on ‘ademo’. This time, click on the name – we want to go to the API manager, not the APIC cloud manager…

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.1.1.png)

You’ll be asked to log into the API Manager. Click on ‘IBM Common Services user registry’. You should be logged in automatically using SSO. If not, use ‘admin’ and the same password you used to log into the cloud pak home page.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.1.2.png)

Make sure it says ‘Welcome to API Manager’.

Also check out the organisation at the top-right: Make sure it says ‘Org for Demo use’ – If it doesn’t, click on it and change it so it does.

7.1 Importing our Facade API flow into API Manager

We’re going to import our API flow from the Asset Repository: The 1-click install has put it there for you... 

Click ‘Develop APIs and Products’ tile.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.1.3.png)

Click ‘Add’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.1.4.png)

Select ‘From asset repository’ and click ‘Next’

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.1.5.png)

In the next window you will be provided an option to launch the asset repository. When you click on it a pop-up window opens. You should be logged in automatically using SSO. If not, use ‘admin’ and the same password you used to log into the cloud pak home page. which might ask you to login again.

Select the ‘chatbot’ Open API specification. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.1.6.png)

Once our asset is validated, we can click ‘Next’ to proceed with the import.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.1.7.png)

In the next window, you can configure to Activate API option which creates a draft Product, adds the API to the Product, and publishes the Product to the Sandbox Catalog so that the API is available to be called. We want to only publish to our demo catalog, so will not select this option.

Click ‘Next’. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.1.8.png)

### 7.2 Reviewing and editing our Facade API Flow

The Import API Summary panel indicates that the YAML file is loaded and valid.

Click ‘Edit API’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.1.png)

You can switch to the ‘Assemble’ tab to view the implementation details. 

This is a simple facade API secured by an API key which routes the incoming requests to our integration APIs based on request content. But you can always enrich the flow additional error handling or security constructs depending on your requirements. For the purpose of this demo, we will stick to our simple façade API    


![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.2.png)

Each invoke policy uses property values to specify the URL for our target integration APIs. (such as classifyImages-endpoint)

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.3.png)

Next, we need to update these endpoint properties to point to our deployed integration APIs. 

Switch to ‘Design’ tab and select ‘Properties’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.4.png)

First, click ‘summary-endpoint’ property and click ‘Add’ to define a catalog specific value.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.5.png)

Select our demo catalog and type the endpoint value of the ‘IncidentSummary API’. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.6.png)

Make sure you use the correct endpoint value here.

It should be in the following format:

http://<incidentsummary-hostname>/IncidentSummary/summary

You can check the value of the hostname from App Connect Dashboard.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.7.png)

Next, click ‘stormpath-endpoint’ property and click ‘Add’ to define a catalog specific value. Select our demo catalog and type the endpoint value of the ‘Tickets_StormIncWeatherAPI’. 

Make sure you use the correct endpoint value here.

It should be in the following format:

http://<stormpath-hostname>/Tickets_StormIncWeatherAPI/StormData/stormpath

You can check the value of the hostname from App Connect Dashboard.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.8.png)

Lastly, click ‘classifyImages-endpoint’ property and click ‘Add’ to define a catalog specific value. Select our demo catalog and type the endpoint value of the ‘classifyImagesV4 API’. 

Make sure you use the correct endpoint value here.

It should be in the following format:

http://<classifyImages-hostname>/ classifyImagesV4/images/classify

You can check the value of the hostname from App Connect Dashboard.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.2.9.png)

We finished editing our API, lets create a product! A product is a way of grouping together APIs. Consumers subscribe to products rather than individual APIs.

### 7.3 Publishing our Facade API Flow

Click the ‘Develop’ menu on the left.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.1.png)

Click ‘Add’ and select ‘Product’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.2.png)
![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.3.png)

Enter a product name such as ‘Storm Insurance APIs’ and a version ‘1.0.0’ will do.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.4.png)

Select ‘chatbot’ API to add to the product and click ‘Next’ 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.5.png)

You can add multiple rate limits and plans. But for now, Default plan will do.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.6.png)

Finally configure the ‘visibility and subscribability’ settings. You can leave the default settings. We will leave the ‘Publish product’ checkbox empty as we want to publish to our demo catalog later. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.7.png)

Click ‘Done’. You will be redirected to the ‘Develop’ page. Now, we are ready to publish to the Portal!

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.8.png)

Now click on the three-dot overflow menu by the ‘Storm Insurance APIs’ product and click ‘publish’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.9.png)

You’ll be prompted for a catalog to publish to – select ‘Catalog for Demo use’. We only have one gateway installed so we can leave the checkbox blank – click ‘Publish’

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.10.png)

You will see a notification once the publish finishes. (in seconds) 

If you now go back to your catalog and look for products, you can see the status is ‘published’ (go to the ‘Manage’ menu and then click on the Catalog for Demo use)


![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.11.png)

You can see our Default plan added into the product. You can also see that we’ve published our API to a secure DataPower Gateway.

The gateway has been configured as an APIC gateway service and bound to the catalog as part of the 1-click demo installation for this lab.


![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.3.12.png)

### 7.4 Discovering and consuming our API 

Now that we’ve published our API, we need to make sure that our API consumers can discover it and use it.

Our Portal will allow customers to view the APIs, sign up and subscribe to plans in a self-service manner, test the APIs, download the OpenAPI / Swagger documents and more.

Click ‘Catalog settings’ and ‘Portal’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.1.png)

You can see that a portal service has been created for you as part of the 1-click demo installation.

You can directly access to the Portal URL from your browser. Notice that ‘Storm Insurance APIs’ are already visible as we set the visibility as ‘public’. 
We’re going to need to register a consumer and get an API key – luckily, we can do that self-service! Click ‘Sign in’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.2.png)

Click ‘Sign up’ to create a new account. (if you don’t have already one)

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.3.png)

Fill in your details and then click ‘sign up’.


![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.4.png)

Tip: If you’re using mailtrap.io as your mail server, you can use any email address. Use **‘chatbot@example.com’** to be safe – example.com is guaranteed to not be a real domain. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.5.png)

We’ll need to get the email: You’ll find it in your email page in your mailtrap.io. account. 
API Connect thinks you are now a new consumer user and has sent you an email to welcome you. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.6.png)

Copy and paste the link into the browser in the lab desktop machine. You should eventually get the portal with the notice:

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.7.png)

Make sure you’re using demo catalog user registry and sign in with your credentials you just created.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.8.png)

You’ll get the following home screen:

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.9.png)

We’re going to create a new application: This will give us an API key so we can call our APIs.

Click on ‘Create a new App’.

Give our App a title e.g Storm Insurance Chatbot and click ‘Submit’:

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.10.png)

This gives us an API key and secret. You’ll only ever be able to see the secret once here. For this lab, we haven’t asked for secrets, so you won’t need to remember it.

Click ‘Copy’ ( )to get your API key. Copy it somewhere safe then click ‘Ok’

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.11.png)

You’ll now see the details for your application. Dashboard tab shows you the stats of your application. At the moment, we don’t have an API calls, so no stats...

We’ve not also subscribed to any APIs yet – click on ‘Why not browse the available APIs?’

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.12.png)

Click on the ‘Storm Insurance APIs’ product.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.13.png)

You can now see the plans: 
We have only Default plan. Click on ‘subscribe’.


![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.14.png)

Select the ‘Storm Insurance ChatBot’ application we have just created.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.15.png)

We now need to confirm our subscription – click ‘Next’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.16.png)

Now our application subscribed to the ‘Default plan’ of the ‘Storm Insurance APIs’ product.

What does this mean?

This means, ChatBot application can make 100 calls per hour for free. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.17.png)

We’re now back at the product screen – click on the API itself, not the plan. Click on POST – note the portal has everything you need to call your API – if you scroll down, it’s even generated clients in various languages for you (that’s how we created our test clients in curl in our scripts for this lab).

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture7.4.18.png)

You can go ahead and test your API.

Notice that API key will be automatically filled by the ‘Storm Insurance Chatbot’ application’s client id.

You can use the below request examples. Remember to use the incident number returned from the first call in the subsequent calls.

### 1)	Route to ticketsstormincweather API
{
  "apiName": "stormpath",
  "postCode": "70510:US",
  "date": "2018-07-13",
  "name": "John ACE"
}
### 2)	Route to classifyimages API
{
   "apiName": "classifyImages",
   "image_url":" https://raw.githubusercontent.com/IBM/cp4i-demos/main/ace-weather-chatbot/images/car.jpg",
   "incident_id": "REPLACE_INCIDENTNUMBER",
   "image_name":"My damaged car using a URL"
}
### 3)	Route to incidentsummary API
{
  "incidentId": "REPLACE_INCIDENTNUMBER",
  "apiName": "summary"
}

Now we are ready to consume our API from Watson Assistant chatbot! 




