# 5 Getting into the Cloud Pak and Building Your Integration
Getting started with Cloud Pak for Integration (CP4I) on Red Hat OpenShift Kubernetes Service (ROKS) on IBM Cloud has never been easier with one-click install. The following guide walks you through how to deploy Cloud Pak Integration on ROKS cluster.
https://ibm-garage-tsa.github.io/cp4i-demohub/cp4i-on-roks/

We’re going to be using API Connect, App Connect and the Asset Repository for this lab.

### 5.1 Accessing the Designer Integration Tooling

For either method, menu or instance view, click on ‘ace-designer-demo’ which is our instance of the designer tooling for this lab.

![](https://github.com/ilyastar12/markdown/blob/main/img/picture5.2.1.png)

You’ll arrive at the App Connect Designer here:

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.1.2.png)

This is where we can create all of our API integration flows and also manage our connectivity to our services and endpoints. You can create many integration flows and manage them all here.
### 5.2 Connecting the tooling to our endpoints

Let’s go to the connector catalog: 

The connector catalog appears with a list of the cloud pak connectors which are installed locally to this lab. There are many more connectors available although not all all of them run ‘locally’. Some of the connectors are currently available in the pak locally, all of them are available on the IBM cloud – you can use the ones that run on the IBM cloud directly from ICP4i designer as well – you just need to link to your IBM cloud account, which we won’t be doing in this lab. 

More connectors are being developed constantly – for a list, look here: https://www.ibm.com/cloud/app-connect/connectors/ 

You can choose whether you want to run the connectors locally or on the IBM cloud. For this lab, we will run them locally: 

![](https://github.com/ilyastar12/markdown/blob/main/img/img/Picture192.png)

### 5.2.1 Connect to IBM Watson Visual Recognition 

Let’s set up our Watson AI endpoint – scroll down until you see the IBM Watson connectors:

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.2.png)

Click on ‘IBM Watson Visual Recognition’. You’ll see that the connector expands and shows you the actions available for the connector.  CP4I connectors are smart connectors and are metadata driven – you don’t need to know what functions and data are in the endpoint – the connectors will usually show them to you.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.3.png)

Click on ‘Connect’

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.4.png)

Note that if you have already an account associated with the connector, you can click on ‘Add a new account’.  You can have multiple accounts connected to each application or API. You can also rename your App Connect accounts for ease of identification, update the credentials for your accounts when necessary, and remove accounts that you no longer need.

The ability to connect to multiple accounts enables you to create flows that use different accounts to connect to different instances of an application; for example, test and production instances, or instances in two different sites or geographies.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.5.png)

To connect to your Watson Visual Recognition account, you’ll need credentials – otherwise anyone could connect to it. The service is protected by an API key. You’ll now be asked for the API key that you kept safe from before: Enter it here and click ‘connect’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.6.png)

(Hint: you can use the ‘eye’ button to show the API key to check it’s correct)

IMPORTANT: DON’T MOVE ON YET! You’ll see ‘Account 1’ as the name of the account. WE NEED TO RENAME THE ACCOUNT FOR THE LAB TO WORK SEAMLESSLY.

To rename your account, Click the three dots menu and click ‘Rename Account’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.7.png)

In the dialog box, name the account ‘App Connect Trial’ (exactly as shown – capitals on the first letter of the words, spaces between the words) and click ‘Rename Account’ as shown below.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.8.png)

Your connector should now look like this.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.9.png)

### 5.2.2 Connect to ServiceNow

Let’s set up our ServiceNow endpoint – scroll down until you see the ServiceNow connector or you can locate it by filtering via the search box.

Click on ‘Connect’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.10.png)

You’ll now be asked for the following details that you kept safe from before: Enter it here and click ‘Connect’.

The **URL of your ServiceNow instance**, in the following form: https://<servicenow-id>.service-now.com/

The **username and password** that you use to log in to the instance. 

**ClientID** and **Secret** of your ServiceNow application (Oauth endpoint).

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.11.png)

Similarly, we want to rename the account for the Lab to work seamlessly. 

To rename your account, Click the three dots menu and click ‘Rename Account’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.12.png)

In the dialog box, name the account ‘App Connect Trial’ (exactly as shown –capitals on the first letter of the words, spaces between the words) and click ‘Rename Account’ as shown below.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.13.png)

Your connector should now look like this.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.14.png)

### 5.2.3 Connect to IBM Weather

Let’s set up our IBM Weather endpoint – scroll down until you see the IBM Weather connector or filter via the search box.

Click on ‘Connect’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.15.png)

The service is protected by an API key. You’ll now be asked for the API key that you kept safe from before: Enter it here and click ‘Connect’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.16.png)

Similarly, we want to rename the account for the Lab to work seamlessly. 

To rename your account, Click the three dots menu and click ‘Rename Account’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.17.png)

In the dialog box, name the account ‘App Connect Trial’ (exactly as shown – capitals on the first letter of the words, spaces between the words) and click ‘Rename Account’ as shown below.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.18.png)

Your connector should now look like this.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.2.19.png)

Great! We’re now all connected up! Let’s go and see our flow!

### 5.3 Importing the Integration flow into designer

Go back to the ‘Home’ page in Designer by clicking the ‘home’ icon.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.3.1.png)

We’re going to import our flow from the Asset Repository: The 1-click install has put it there for you...

Click on ‘Create from an asset’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.3.2.png)

We have a flow to use already stored in the Asset Repository: We’re going to import it to save you typing and clicking!

There is a lot of detailed designer flow documentation for when you want to delve deeper – a good place to start is https://ibm.biz/learnappconnect

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.3.3.png)

Click on the ‘+’ sign to the right on the ‘Tickets_StormIncWeatherAPI’ asset and create from the asset.

Repeat the same for ‘IncidentSummary’ and ‘classifyImagesV4’ assets.

### 5.4 Reviewing our API Integration Flows:

This section is for you understand how the flow is built, as the flows are pre-built and we won’t change it in the lab, you can skip straight to ‘Starting the flow’ section and come back here later. 

Go back to the ‘Dashboard’ page in Designer by clicking the ‘Dashboard’ icon where you can access all your flows.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.1.png)

### 5.4.1 The ‘Tickets_StormIncWeatherAPI’ API flow

This API checks the weather on a date and location and opens a ServiceNow ticket if it determines that a storm has happened.

Click on the ‘Tickets_StormIncWeatherAPI’ API flow tile. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.2.png)

What you can see first is our API model.

App Connect Designer builds your API for you – you don’t need to worry about OpenAPI specs or Swagger editors – it’s all built in. To create your API, you just type in the names of the fields you want to use in plain English. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.3.png)

Now that we’ve told the API what data to use, we need to define what actions to perform on that data. Click ‘Operations’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.4.png)

Click ‘Edit flow’ to see the details of the flow.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.5.png)

The first step in the flow uses date and location in the request input and retrieves the weather observations on that specified date and location. 

You can also test this step independently by defining sample data and clicking ‘Try this action’. 

You will be amazed by how much data you can retrieve related to Weather observation. For the purpose of this demo, we will use wind and precipitation to evaluate the storm condition. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.6.png)

The ‘If” construct checks if the ‘wind speed is greater than or equal to 20’ and ‘precipitation is greater than or equal to 10’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.7.png)

If the above condition evaluates to true, we assume there is a storm occurrence and create a provisional storm claim in ServiceNow and return the claim id and the evaluation result. 

If the above condition evaluates to false, we directly return the evaluation result. 

### 5.4.2 The ‘classifyImages’ API flow

This API takes an image and a ServiceNow ticket number as input, analyses the image with Watson Image Recognition and finally updates the ticket with analysis results.

Click on the ‘classifyImagesV4’ API flow tile. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.8.png)

What you can see first is our API model.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.9.png)

Now that we’ve told the API what data to use, we need to define what actions to perform on that data. Click ‘Operations’ of ‘images’ data model.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.10.png)

Click ‘Edit flow’ to see the details of the flow.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.11.png)

Retrieves the ServiceNow ticket.

Checks that either an image (file base64 encoded) or a URL to an image has been supplied.

-	If an image has been supplied, it adds it as an attachment to ServiceNow
-	If a URL has been supplied, it does not add an attachment and adds the attachment ID as the IF output context
-	If neither supplied, exits the flow with error

Invokes Watson Visual Recognition to get the recognised 'classes' for the image from the 'default classifier'

Uses the JSON parse node to set an arbitrary set of 'claimable values' for a few classes

The set variable node augments the discovered classes with their claimable value.

It responds with what the image was recognized as, and its maximum claimable value. It also augments the ticket.

-	Adds the image as an attachment to the ticket
-	Augments the description field with a JSON structure that holds the information discovered (for later retrieval)

### 5.4.3 The ‘IncidentSummary’ API flow

This API simply takes a ServiceNow ticket number as input, returns the details.

Click on the ‘IncidentSummary’ API flow tile. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.12.png)

What you can see first is our API model.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.13.png)

Now that we’ve told the API what data to use, we need to define what actions to perform on that data. Click ‘Operations’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.14.png)

Click ‘Edit flow’ to see the details of the flow. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.4.15.png)

### 5.5 Testing our API Integration Flows

Now we’ve built our API, we need to test it. When you create an API flow in your App Connect Designer instance, the definition provides an API that you can expose. 
After you start the flow, you can verify its behaviour by using the built-in test facility to call the endpoints for each of the implemented API operations.

In the course of this lab, we want to test our APIs using built-in test facilities. This will give the us the assurance to promote our flows from Designer runtime (which is a development environment) to integration runtime. 

If the flow is not already open, click ‘Dashboard’ in the navigation pane and then click the flow tile.

Let’s start with ‘Tickets_StormIncWeatherAPI’ flow.

Click ‘Start API’

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.5.1.png)

Click the ‘Test’ tab.

The Overview page displays the API type and the base URL for the API endpoint. To the right of the "Overview" title, a tag is provided for each model that is defined in the API flow.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.5.2.png)

A Download Open API Document link is also provided for the OpenAPI document that describes the API. 

If you download this document, it is saved as a YAML file to the default download location that is configured for your browser. The format of the file name is ‘flowName-version.yaml’; for example, Tickets_StormIncWeatherAPI-1.0.0.yaml. The version number is derived from the version of the API in the OpenAPI document and is always set to 1.0.0.

You can use the OpenAPI document to test your flow in any other test tool or you can proceed with the embedded test option. 

From the left pane, click ‘POST /StormData/stormpath’ operation to view its details and test the behaviour. Notice that the tag shown will reflect the model that an operation belongs to.

The Details tab displays the following information:
-	The HTTP method and request for the operation.
-	The authentication method (security scheme) that the API uses.
-	The header parameters in a collapsible section.
-	The body, path, or query parameters with examples, and the schema if relevant, in collapsible sections. The parameters that you see will depend on the operation's settings.
-	Tooling languages that can be used when making the request, and a code sample for calling the operation in the selected language.
-	Response status codes for the operation, and the response body schema with an example.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.5.3.png)

Again, you can use the embedded test scripts to test your flow from your preferred tooling language or proceed with the embedded test option.

To proceed with the embedded test option, click ‘Try it’.

Use the below test data which passes the storm validation and creates a ServiceNow incident. 

{
  "postCode": "70510:US",
  "date": "2019-07-13",
  "name": "John ACE"
}

Note that authentication credentials are auto generated and displayed together with the request parameters.

Click ‘Send’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.5.4.png)

Then review the request and response that are displayed.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.5.5.png)

For our POST example, the Response section displays the success code that is returned (200 OK), the headers, and the claimNumber value that represents the ID assigned by ServiceNow.

We will use this claimNumber as an input parameter to test the other APIs.

Next, we will start ‘classifyImagesV4’ API. 

If the flow is not already open, click ‘Dashboard’ in the navigation pane and then click the ‘classifyimagesV4’ flow tile.

Click ‘Start API’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.5.6.png)

Click ‘POST /images/classify’ and ‘Try it’.

Use the below test data which passes the ServiceNow incident id created in the previous step along with the image url. 

{
  "incident_id": "INC0010001",
  "image_name": "my damaged car",
  "image_url": "https://raw.githubusercontent.com/IBM/cp4i-demos/main/ace-weather-chatbot/images/car.jpg"
}

Click ‘Send’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture5.5.7.png)

Then review the request and response that are displayed.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture5.5.8.png)

For our POST example, the Response section displays the success code that is returned (200 OK), the headers, and the classification values provided by Watson Image Recognition for the input image.

Lastly, we will start ‘incidentSummary’ API. 

If the flow is not already open, click ‘Dashboard’ in the navigation pane and then click the ‘incidentSummary’ flow tile.

Click ‘Start API’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture5.5.9.png)

Click ‘GET /summary/{id}’ and ‘Try it’.

Use the ServiceNow incident id created in the previous steps.

Click ‘Send’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture5.5.10.png)

Then review the request and response that are displayed.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture5.5.11.png)

For our GET example, the Response section displays the success code that is returned (200 OK), the headers, and the updated claim details.
We’ve now got our flow running in the designer and we’ve tested it – now we are ready deploy it ‘for real’ on the cloud pak runtime. 



























































