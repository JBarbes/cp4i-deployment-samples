# 2 Plan of Work
This solution has a number of moving parts, so we’ll tackle them in a logical sequence. If you’re familiar with how to do any of the steps, feel free to do them in the way you prefer or are familiar with. 

If you’re familiar with any of the tools we’re using, feel free to embellish or change the lab –as long as you make sure it all ‘hangs together’. You can build the ‘extension’ version if you’re familiar with the tooling. 

We recommend you make one journey through the lab as we describe it and then go back and explore if you have time. You can make changes and redeploy new versions afterwards. 

We’ll be doing the following:

#### •	Set up our integration systems and services endpoints
We are going to integrate with SaaS systems and IBM Watson AI services. We will need to have these endpoints created and create credentials for so that we can integrate to them securely in the lab.
In the ‘real world’ systems like IBM's Weather service or ServiceNow will be running at customers already – this is a lab task.

#### •	Create an integration flows for our ‘Storm Claim APIs’
This will create our three separate APIs which are independently deployable and scalable and the integrations to all of our endpoints. We will create an ‘integration flow’ which takes the API request, calls the endpoints in the correct order, maps the data between them and sends an appropriate API response back to the caller. These APIs will leverage IBM Watson Visual Recognition and IBM's Weather service using built-in connectors.

#### •	Deploy the API to the Cloud Pak for Integration (CP4I) runtime
Once we have developed our flows and tested it, we will deploy it to CP4I running on OpenShift. This will create a Kubernetes container/pod deployment with highly available replicas which we can then scale up and down as we wish.

#### •	Manage the API, applying security and rate-plans and publish it to our Self-Service Portal
We will create an API which will route across the three ‘Storm Claim APIs’ and secure it using API keys and rate-limited API plans. This way our consumers can discover it, get the information they need to use it and preferably sign up for access in a self-service and secure manner. 

#### •	Set up our Watson Assistant and Node.js application
We are going to implement a chatbot using Watson Assistant and use a Node.js client application to embed the chatbot.  

#### •	Create an ‘application’ to consume our API. We’ll use the portal to discover the API and self-service register it. 
We will register to our Watson Assistant chatbot embedded Node.js application to API server. Registering Applications allows us to assign API keys and also to monitor the calls made to the API by that application.


