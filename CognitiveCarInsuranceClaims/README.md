# Cognitive Car Insurance Claims Demo
This demo shows how to use the IBM Cloud Pak for Integration to create, expose and manage an API which allows insurance customers to submit a car repair claim and have it automatically processed and a repair estimate returned in real-time.

It uses IBM Watson AI image recognition to analyse a photo of the car, IBM Watson AI to translate the claim into Spanish when using a 3rd party repair company and also shows integration with Salesforce and ServiceNow using the App Connect Smart Connectors.

The artefacts for this demo are currently stored in a different repository [Here](https://github.com/IBM/cp4i-demos/tree/main/cognitive-car-insurance-claims) - it is intended to move them to this repository in the future.

The instructions to build and run this demo are in this repository in the Docs directory [Here](Docs/README.md) - click to get started!

# DEPRECATION NOTICE for Image recognition
The Integrated Car Repair demo has a dependency on the Watson Visual Recognition service (to 'look' at the photo of the car and work out what type it is). Watson deprecated that service with the result that if you already had a Visual Recognition instance on IBM cloud, you could keep it for a year (to end 2021) but it you didn't then you couldn't create a new one.

There is a new version of the demo flow ("Car Insurance Cognitive API Lab Short V2.yaml") which we've uploaded and will be visible in the Asset Repo - this does not have the image recognition code in it so it can be used if you don't have a Watson VR image.