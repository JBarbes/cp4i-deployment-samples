# 8 Create your Watson Assistant chatbot 
Now it is time to create our chatbot which will consume the APIs we’ve created before. 
Login to your cloud account. (sign in at https://cloud.ibm.com Use your IBM ID, or if you’re an IBMer, you may go through a Single Sign-on process). 
Once you’re in, you’ll be presented with the cloud dashboard showing which services you have provisioned.
From the ‘Resource summary’ tile click on the ‘Services’, you’ll find your Watson Assistant service that you’ve created before.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.1.png)

An assistant helps your customers complete tasks and get information faster. It may clarify requests, search for answers from a knowledge base, and can also direct your customer to a human if needed. In our demo, 

-	it will search for answers to queries like ‘can customer claim a storm insurance?’ via validating the storm occurrence with IBM Weather Service.
-	it will analyse the image uploaded by customer to get an estimate value for the damage via connecting to Watson Visual Recognition service.
-	And moreover, it will automate the claim creation process. 

Click on your new service and you’ll see the ‘Manage’ tab. Click ‘Launch Watson Assistant’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.2.png)

Click ‘Create assistant’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.3.png)

Name the Watson Assistance instance ‘Storm Insurance’ and click ‘Create assistant’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.4.png)

Next, we are going to add the dialog skill that is hosted on our Git repo (https://github.com/IBM/cp4i-demos/tree/main/ace-weather-chatbot/assets/watson-assistant-skills).

A dialog skill is a container for the artifacts that define the flow of a conversation that your assistant can have with your customers.

Download or clone the dialog skill (skill-Stormy-Insurance.json).

Click ‘Add dialog skill’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.5.png)

Click ‘Import skill’ tab.

Select ‘skill-Stormy-Insurance.json’ file that you’ve downloaded from Git repo and click ‘Import’

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.6.png)

You will see that dialog is added to your assistant.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.7.png)

Now that you’ve created your Watson Assistant-enabled chatbot, you need to connect it to a data source. The following section shows you how to do that by adding webhooks to Watson Assistant that query for dynamic data.

Our insurance chatbot uses our facade API to communicate with the integration flows. ¬

Click on your ‘Storm Insurance’ dialog tile to open the dialog

Click on Options on the left. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.8.png)

Under Options, click ‘Webhooks’. 
A webhook is a mechanism that allows you to call out to an external program based on something happening in your program. When used in a dialog skill, a webhook is triggered when the assistant processes a node that has a webhook enabled. The webhook collects data that you specify or that you collect from the user during the conversation and saves in context variables.

In the URL text box, type the endpoint value of your chatbot API (that you’ve exposed via API Connect)

In the ‘X-IBM-Client-Id’ Header value text box, type the Client ID (API key) value of your chatbot API (that you’ve exposed via API Connect). 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.9.png)

Note: If you didn’t take a note of these values you can follow the steps below to access 

From the API Connect Portal dashboard, click on the tile for the Storm Insurance APIs product.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.10.png)

Click on the tile for the chatbot API.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.11.png)

From the 'Overview' copy the Endpoint URL

This is used as your webhook URL

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.12.png)

Next, we need to get the value to use as ‘X-IBM-Client-Id’ HTTP Header value.

From the API Connect Portal dashboard, click ‘Apps’. 

Click on the tile for the ‘Storm Insurance APIs’ product and navigate ‘Subscriptions’ tab.

The ‘Client ID’  is the value to use as ‘X-IBM-Client-Id’ HTTP Header value.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture8.1.13.png)







