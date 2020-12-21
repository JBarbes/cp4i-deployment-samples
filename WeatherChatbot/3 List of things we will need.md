# 3 List of things we will need:
As this is an integration lab, we will need systems and services to integrate to:

### 3.1 List of Systems and Services Endpoints 
#### Service Now: 
Service is an IT services management (ITSM) system provided as a SaaS i.e. it is hosted in the cloud.

In this scenario, we as a Storm Inc insurance company will use Service Now to log an insurance claim incident.

Service allows you to create developer instances/accounts free of charge. You will need a developer account to run this lab so instructions as to how to create them are included and you can set an account up as part of the lab (https://developer.servicenow.com/). If you already have a developer Service Now account, you can use that. 
#### IBM Weather Data:
IBM Weather Data provides historical, current and future information about Weather parameters of a particular geo location. You could connect to Weather Data using the API Key.

A free 30-day API key can be available here. 
https://epwt-www.mybluemix.net/software/support/trial/cst/programwebsite.wss?siteId=443&tabId=774&w=1

#### IBM Watson Visual Recognition: 

IBM Watson is available on the IBM Cloud and also in the IBM Cloud Pak for Data. IBM Cloud lets you create non-expiring free instances of the IBM Watson services that you can use for this lab (or anything else)

The IBM Watson Image Recognition service lets you send a picture (.jpg, .png) to Watson and returns a list of things that Watson can ‘see’.

In this use case we are using Visual Recognition to recognize the images of weather damaged objects, assess the maximum claim possible for the type of the object. You can train your Visual Recognition model with your set of images and classifiers.
#### IBM Watson Assistant: 
The IBM Watson Assistant service lets you build, train, and deploy conversational interactions into any application, device, or channel. Watson Assistant can be deployed in any cloud or on-premises environment – meaning smarter AI is finally available wherever you need it.

In this use case we are using Watson Assistant to build a chatbot dialog that takes place as a first step in claiming a storm damage, assisting the victim about the process as well as validating the data to filter fraudulent claims to a certain degree without frustrating the victim.

Source code is hosted on our Github repository.

#### Node.js Client Application:
This project deploys a react application that connects to a Watson API. It currently runs from localhost. The application deals with text and image responses only from the Watson assistant.

Source code is hosted on our Github repository. 
#### Some extra things we need for this lab: 
GitHub 
We’ve hosted our API flow definitions, our test scripts and some other things you might need on a public github repository, so they’re easy to download to your lab environment. 

The repo is here: https://github.com/IBM/cp4i-demos

In this way, if you want to redo this lab in your own environment you can use the assets that you need. 

Also, if you are using one-click install API Connect and App Connect assets will be available to you via Asset Repository. 

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture2.png)
