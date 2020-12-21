# 9 Node Chat Application
The application deals with text and image responses only from the Watson assistant.
This project was bootstrapped with Create React App. This project deploys a react application that connects to a Watson API.

### 9.1 Installation

#### 0.	Clone this repo (https://github.com/IBM/cp4i-demos/tree/main/ace-weather-chatbot/assets/watson-assistant)

#### 1.	install 'yarn': follow the instructions for your OS

#### a.	Mac-specific: if you do not have it already, you will need to install xcode. This article gives detailed instructions.

#### 2.	Install the dependencies: yarn install

### 9.2 Configuration

Once you cloned the repository and installed the yarn packages, you will see a similar folder structure. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.1.png)

You can now configure the project with your preferences and demo environment details.  

### 9.2.1 Set access credentials in .env.local

The chatbot has the following immediate dependencies;

-	The API Credentials specific to your Watson Assistant
-	The credentials to access an image processing API, which is provided by an App Connect API Flow

The credentials for these are stored in the .env.local file, which you will need to create, in the same directory that you cloned this repo to. We have supplied a sample sample.env.local that you should edit and rename to .env.local.

##### REACT_APP_ASSISTANT_URL="https://..."
##### REACT_APP_ASSISTANT_API_KEY="xxxYYYzzz"
##### REACT_APP_IMAGE_PROCESS_URL="https://...""
##### REACT_APP_IMAGE_PROCESS_API_KEY="xxxYYYzzz"

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.2.png)

For your Watson assistant

-	The API URL for your Watson Assistant: REACT_APP_ASSISTANT_URL
-	The API key for accessing your Watson Assistant instance: REACT_APP_ASSISTANT_API_KEY

To get these;

Browse to your list of assistants on assistant.watson.cloud.ibm.com

Choose the assistant for this demo; from its overflow menu (⋮) select ‘Settings’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.3.png)

Select the 'API details' tab, where you will find "Assistant URL" and "API Key".

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.4.png)

##### For your App Connect Image Processing flow

-	The URL for your image processing API: REACT_APP_IMAGE_PROCESS_URL
-	The API Key for accessing your image processing API: REACT_APP_IMAGE_PROCESS_API_KEY

To get these;

From the API Connect Portal dashboard, click on the tile for the Storm Insurance APIs product.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.5.png)

Click on the tile for the chatbot API.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.6.png)

From the 'Overview' copy the Endpoint URL

This is used as your REACT_APP_IMAGE_PROCESS_URL

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.7.png)

Next, we need to get the value to use as REACT_APP_IMAGE_PROCESS_API_KEY.

From the API Connect Portal dashboard, click ‘Apps’. 

Click on the tile for the ‘Storm Insurance APIs’ product and navigate ‘Subscriptions’ tab.

The ‘Client ID’  is the value to use as REACT_APP_IMAGE_PROCESS_API_KEY

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.8.png)

### 9.2.2 Set the value of proxy in package.json

You must set the value of proxy in package.json. You need to do this to allow your client to communicate with Watson assistant - which does not allow 'Cross Origin' requests. This must be set to the same value as the base part of your REACT_APP_ASSISTANT_URL. For example, if your .env.local has;

REACT_APP_ASSISTANT_URL="https://api.us-south.assistant.watson.cloud.ibm.com/instances/ffcc1122/..."

then your package.json should contain;

  ...
  "proxy": "https://api.us-south.assistant.watson.cloud.ibm.com",
  ...  
### 9.2.3 File uploads

The Assistant.js component is currently configured to accept jpg, png and gif. Change the following line to update that.

const imageTypes = ["jpg", "jpeg", "png", "gif"];

### 9.2.4 File processing code

The file is processed via code in src/utils/imageApiCall.js. The supplied implementation calls an API, and constructs a Watson Assistant message based on the response.

This code is called from within src/components/Assistant.js using this code;

imageApiCall(result.value.data).then(
  (response) => {
    //addUserMessage(response)
    sendUserMessage(response)
      .then((res) => {
        console.log(JSON.stringify(res.data, null, 2))
        setConversation((prevState) => [...prevState, res.data]);
      })
      .catch((err) => {
        console.dir(err);
      });
  }
)

The current implementation sends the result of ‘imageApiCall’ to Watson Assistant (sendUserMessage) but does not display is in the chat dialog. The message can be displayed in the dialog by uncommenting the call to ‘addUserMessage’.

### 9.2.5 The dialog

The dialog adds both images the user adds and a text message depending on the number of files uploaded.

-	"file: uploads failed"
-	"file: upload failed"
-	"file: uploads successful"
-	"file: upload successful"

Comment out the ‘addUserMessage’ that follows these strings in Assistant.js to avoid displaying this string.

addUserMessage(msg);

### 9.2.6 Assistant response to files

The same text messages are sent to the Waston Assistant using ‘sendUserMessage(msg)’.

-	"file: uploads failed"
-	"file: upload failed"
-	"file: uploads successful"
-	"file: upload successful"

These need to be configured as intents in the Watson assistant with responses in the dialog.

### 9.3 Running your Node Chat Application 

We have installed and configured our application. Now we are ready to run it locally.

From your terminal navigate to your project folder and run the following command.

yarn start

Runs the app in the development mode.
Open http://localhost:3000 to view it in the browser.

The page will reload if you make edits. You will also see any lint errors in the console.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.9.png)

There are some other scripts in the project directory that you can run to test, build and eject the application

##### yarn test
Launches the test runner in the interactive watch mode.
See the section about running tests for more information.

##### yarn build
Builds the app for production to the build folder.
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.
Your app is ready to be deployed!

See the section about deployment for more information.

##### yarn eject
Note: this is a one-way operation. Once you eject, you can’t go back!

If you aren’t satisfied with the build tool and configuration choices, you can ‘eject’ at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except eject will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use ‘eject’. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.
### 9.4 Test everything – your cognitive integrated insurance chatbot! 

Let’s test our application end to end. 

Open http://localhost:3000 to view chatbot in the browser.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.10.png)

Type ‘yes’ to start your claim process.

Next the chatbot ask questions to collect details about you, your location and the date of the storm.

Please note that for the purpose of this demo we trained the chatbot to accept only US and UK postcodes. Also, we’ve embedded a logic to accept the claims requests that are not older than 16 months. In that case, it will ask you again to enter a valid date or you can refresh your page to start over again.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.11.png)

The location and the date given below in the screenshot is an occurrence that matches the criteria of storm in our integration flow. You can use the same or you can try other options.


![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.12.png)

At this point the chatbot uses the power of integration to return back a dynamically retrieved assessment result. In addition to that it will trigger claim process and create a provisional claim. 

You can see that your case is confirmed as a storm occurrence. 

Now all you need to do is to upload the image of the damage. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.13.png)

Again, your chatbot, powered with integration and Watson Visual Recognition, will analyse the damaged object.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture9.2.14.png)

IBM Watson Assistant replies to the user the analyses result along with the provisional claim details. The chat application displays the answer to the user. 
There you go! No need to worry about the issues like; how to make an insurance claim? what do I need to submit for an insurance claim? who will assess the damage? when should I make an insurance claim?... With couple of clicks your claim process has been initiated. 

