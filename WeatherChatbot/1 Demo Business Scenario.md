# 1 Demo Business Scenario

#### 1.1 Storms can cause chaos – for insurance customers and insurance companies!
   Sadly, the chaos after a serious storm can be devastating. Many people who are badly affected are likely to contact their insurance company, to find basic information       about how to make an insurance claim and to claim compensation for damage caused by the storm. With this sudden load, the supporting systems are often overwhelmed, and communication lines get congested with claim requests and questions.
What do I do if my home's been flooded or damaged in a storm? How to make an insurance claim? What do I need to submit for an insurance claim? Who will assess the damage? When should I make an insurance claim?...
In times of crisis, fraudulent requests also surge and which in turn forces insurance companies to apply tedious processes for claim evaluation. Multiple layers and checks to discriminate between fraud and genuine claims are time-consuming for both parties which usually creates frustration among genuine victims and loyal customers. 

#### 1.2 Avoid the chaos with integrated cognitive technology
A chatbot can play a critical role in helping insurance companies to accelerate the process of claim evaluation checks and quickly gather information about storm damage and offering smoother user experience.  
IBM Watson Assistant helps you build, train, and deploy conversational interactions that takes place as a first step in claiming a storm damage, assisting the victim about the process as well as validating the data to filter fraudulent claims to a certain degree without frustrating the victim. With IBM Cloud Pak for Integration you can elevate your chatbot experience from intelligent conversational interactions to real, cognitive system interactions by integrating with multiple applications. IBM Cloud Pak for Integration allows you to orchestrate your integration flows;
  -	to verify that there was a storm on the date and location provided by the victim with IBM's Weather service
  -	to create an online insurance claim 
  -	to identify the items claimed for by analyzing the photographs uploaded by the victim using IBM Watson Visual Recognition and using this information to provide an   estimate of value of the damage

#### 1.3 The integrated solution architecture
An insurance company that specializes in 'Storm insurance' wants to streamline its claims process. They have a chatbot that verifies that there was a storm on the date and location provided by the victim and provides an initial estimate for property damage, by analyzing images uploaded by the customer and raises a provisional claim ticket for follow-up by a specialist. This will dramatically increase the efficiency of the specialist, by eliminating obviously fraudulent claims, gathering key information, and providing an initial claim estimate.
This solution shows how IBM Watson Assistant on IBM cloud can be used together with IBM Cloud Pak for Integration to create an engaging chatbot experience implemented in Node.js which allows users to make online insurance claims and also upload photographs of the items for which they wish to claim. 



Three separate APIs which are independently deployable and scalable are brought together to support chatbot application. These APIs also leverages IBM Watson Visual Recognition and IBM's Weather service using built-in connectors.

![](https://github.com/ilyastar12/markdown/blob/main/img/Picture1.png)

1.	The user visits the insurance company’s site with the storm insurance chatbot application to raise a storm claim.
2.	The chat application calls IBM Watson Assistant hosted in IBM Cloud.
3.	IBM Watson Assistant uses natural language understanding and machine learning to extract entities and intents of the user question.
4.	IBM Watson Assistant collects address and date information from the user to validate the eligibility to raise a storm claim.  
5.	Watson Assistant invokes the API hosted on IBM App Connect for claim validation. 
6.	IBM App Connect uses IBM Weather data connector to determine if the path of storm from historical data actually crosses home location and severity would warrant such damage. Based on outcome, the claim is rejected or accepted. 
7.	If the claim is accepted IBM App Connect uses ServiceNow connector to create a provisional claim and returns back the claim details along with validation message.
8.	IBM Watson Assistant replies to the user the validation message and asks the user to upload the photograph of the damage for claim assessment.  The chat application displays the chat answer to the user.
9.	The user uploads the photograph of the damaged object. 
10.	IBM Watson Assistant application invokes the API hosted on IBM App Connect for damage assessment. 
11.	IBM App Connect feeds the photograph into IBM Watson Visual Recognition running in IBM Cloud. 
12.	IBM Watson Visual Recognition analyzes the photograph and determines the object category and maximum amount user can claim for the item.
13.	IBM App Connect returns the analyses result.

IBM Watson Assistant replies to the user the analyses result along with the provisional claim details. The chat application displays the answer to the user. 
