# 4 Getting Started – Setting up the endpoints
Before we can build our API integration, we need to set up the endpoints that we need will integrate to.

This lab doesn’t use emulators, shims or stubs – we’re going to connect to real endpoints in the real-world cloud! You can use these endpoints after this lab to explore more with CP4I and to do other demos – they’re your endpoints to ‘take home and keep’!

All of these endpoints have been deliberately chosen for this lab as they have free versions that we can use – don’t worry, you won’t need a credit card to create them.

We will set up endpoints to connect to:
• IBM Watson Image Recognition
• ServiceNow
• IBM Weather Company

(If you already have Watson Services and a ServiceNow Developer Account e.g., you can skip this section)

Later, we will connect to the following endpoints.
### 4.1 Setting up the Service Now

To get started you will require admin level access to your ServiceNow account. If you want to create a free ServiceNow account to test out App Connect, you’ll have to register (https://developer.servicenow.com/) for a ServiceNow Account.  Once your account is activated, you can request a ServiceNow personal developer instance.

Once your account is activated, you can request a ServiceNow free developer instance.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.1.png)

Click on ‘Request an Instance’ and select the location of your instance.  

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.2.png)

Click on ‘Request’. This will only take a few seconds.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.3.png)

Please note your instance URL and credentials. You will need these later when we configure the ServiceNow connector. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.4.png)

Click on ‘Open Instance’

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.5.png)

Search for Registry in ‘Filter Navigator’ search bar and then select ‘Application Registry’. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.6.png)

We will create an OAuth API endpoint for external clients. Click on ‘New’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.7.png)

Select ‘Create an OAuth API endpoint for external clients’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.8.png)

In the config panel give it a unique name and hit submit.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.9.png)

This will create a new OAuth endpoint with Client ID and Client Secret generated. You can view these details by clicking and viewing the new endpoint. You will be providing Client ID and Client Secret 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.1.10.png)

Great! We’ve now a running ServiceNow instance with an Oauth app/endpoint registered for it which represents our App Connect!

Please keep in mind that this is a free developer instance, it will be reclaimed in 10 Days and also to support the developer program, instances hibernate when they are idle. But you can easily restore instance from the reclaimed instance's backup. Similarly, you can easily wake up a hibernating instance. (Learn more; https://developer.servicenow.com/dev.do#!/guides/orlando/now-platform/pdi-guide/understanding-pdis)

You’ll be later asked for the following details about your ServiceNow instance and Oauth endpoint to integrate with the service. Please keep them safe. 

-	The URL of your ServiceNow instance, in the following form: https://<servicenow-id>.service-now.com/
-	The username and password that you use to log in to the instance. 
-	ClientID and Secret of your ServiceNow application (Oauth endpoint).

### 4.2 Setting up the IBM Watson Services

You will need an IBM Cloud account to do this. You can use your existing one if you wish or you can set up a new one.

IBM cloud access is free and can be provisioned instantly.

Once you have an account, all of the Watson services have ‘lite’ plans which allow you to use them for free – the only restriction is the number of calls you can make per month. Don’t worry, we won’t be getting anywhere near that number – and you won’t get charged if you hit the limit, it will just stop working until the next month.
Logging in to IBM Cloud 
The IBM Cloud can be accessed at https://cloud.ibm.com.

If you’ve not been to the IBM cloud recently, the UI has just had a makeover, so yes, you are in the right place if you don’t recognize it. 

If you don’t have an IBM ID then click ‘Create an account’ – all you need is an email, you don’t need a credit card. 

When you have an IBM ID, sign in at https://cloud.ibm.com (Depending on your company, e.g. if you’re an IBMer, you may go through a Single Sign-on process). 

Once you’re in, you’ll be presented with the cloud dashboard showing which services you have provisioned: 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.1.png)

### 4.2.1 Creating your free Lite-Plan IBM Watson Visual Recognition
On the IBM Cloud Dashboard, click ‘Catalog’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.2.png)

You’ll see a list of services (if not, click on ‘services’).
Check the ‘AI’ filter checkbox on the left to filter for Watson services. (You can also search for them by name)

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.3.png)

Scroll down and click on the ‘Visual Recognition’ tile.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.4.png)

Inside, you’ll be able create a lite plan (free) instance as shown in the screenshot below.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.5.png)

Select the free ‘lite’ plan and provision the service.
You can change the service name to something more memorable if you wish.
Once you create the service, you will be redirected to ‘Getting Started’ page of your service where you can learn the basics and go through tutorials. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.6.png)

Or, you’ll be able to access the service later from your cloud dashboard (to get to the cloud Dashboard,
click the ‘hamburger’ menu at the top left of the screen and select ‘Dashboard’)

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.7.png)

Look under ‘Services’ and you’ll find your newly created service.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.8.png)

Click on your new service and you’ll see the ‘Manage’ tab:

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.9.png)

The API key and URL are what we are going to need to integrate with the service. You can click ‘Show credentials’ and copy/paste them somewhere for later use in this lab or you can click ‘Download’ and they will be downloaded as a text file for you.

### 4.2.1 Creating your free Lite-Plan IBM Watson Assistant
On the IBM Cloud Dashboard, click ‘Catalog’.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.10.png)

You’ll see a list of services (if not, click on ‘services’).
Check the ‘AI’ filter checkbox on the left to filter for Watson services. (You can also search for them by name)

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.11.png)

Scroll down and click on the ‘Visual Assistant’ tile.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.12.png)

Inside, you’ll be able create a lite plan (free) instance as shown in the screenshot below.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.13.png)

Select the free ‘lite’ plan and provision the service.
You can change the service name to something more memorable if you wish. Once you create the service, you will be redirected to home page of your service.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture4.2.14.png)

Congratulations, you’ve provisioned a free Watson Assistant service. We will be later using this service to create a chatbot. 

### 4.3 Setting up the Weather Data Connector

You can use App Connect to retrieve details on the following objects:
-	Historical Data
-	Forecast
-	Near Locations
-	Locations
-	Location by Point
-	Current Conditions

To use App Connect to integrate IBM Weather Company Data with your other applications, you need to connect App Connect to your IBM Weather Company Data account. To do that, you’ll need to provide the following information:

IBM Weather Company Data API key. 
Claim your 30-day free API key from here - https://epwt-www.mybluemix.net/software/support/trial/cst/programwebsite.wss?siteId=443&tabId=774&w=1
























