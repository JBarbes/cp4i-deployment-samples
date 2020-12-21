# 6 Deploying the Integration flow to CP4I Runtime via the App Connect Dashboard

We’ve now got our flow running in the designer and we’ve tested it – now we need to deploy it ‘for real’ on the cloud pak runtime. To do this, we’ll export a .bar file of our flow from the designer. 

This .bar file contains everything in our flow –with the exception of the connector credentials, which we’ll configure later in a Kubernetes secret. 

When we deploy, it will create a 3 HA replica container pods running on OpenShift – automatically.

### 6.1 Exporting the executable bar file:

To export the .bar file, go into the designer dashboard and click the ‘...’ menu on the integration tile and click ‘Export...’

![](https://github.com/ilyastar12/markdown/blob/main/img2/picture6.1.1.png)

You’ll get a dialog box. Select ‘Runtime flow asset (BAR)’ and click ‘Export’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.1.2.png)

The browser may prompt you for a download location – otherwise it will place the ‘Tickets_StormIncWeatherAPI.bar’ file in the Downloads directory.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.1.3.png)

That’s it – we now have our executable flow – let’s see what we need to do to deploy it.

6.2 Navigating to the App Connect dashboard and importing the .bar file

From the menu, click ‘App Connect’ and then click ‘ace-dashboard-demo’: This is the runtime, we need not the tooling.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.1.png)

You’ll then be taken to the App Connect Dashboard.
Click ‘Create A Server’ 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.2.png)


Now we need to select the kind of tooling we used to build the integration. We used App Connect Designer, so click that and click ‘Next’.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.3.png)

You’re now prompted to upload the .bar file you exported before. In the dialog box, click ‘Drag and drop a BAR file or click to upload’. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.4.png)

Browse to the location of the ‘Tickets_StormIncWeatherAPI.bar’ file that you exported from designer and select it with ‘Open’ and then click ‘Next’.

In the next step, we need to choose configurations for the connector account credentials as we want to use locally deployed connectors.  For the purpose of this demo, we will use ‘ace-designer-demo-designer-acc’ accounts configuration which holds all the connector credentials we configured previously in App Connect Designer.  

Select that as below and click ‘Next’.

(note: For the purpose of this demo, you don’t need to click ‘create configuration’ here unless you want to use different credentials for your connector accounts.)

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.5.png)

You’re now on the last screen! 

Enter a name for our integration server – note that permitted characters are lowercase alphanumeric and "-” and must start and end with lowercase alphanumeric characters.

In these flows we will use local connectors only, so we select ‘local’ for ‘Designer flows mode’.  This option will extend the functionality of each pod by deploying sidecar containers, which are needed to run APIs that are authored in App Connect Designer, and local connectors. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.6.png)

Now click ‘Create’ 

You’ll see:

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.7.png)

When you get refreshed screen, you will see the integration server displayed as a tile on the Servers page of the dashboard, with an initial status of Unavailable ( ), which then changes to Started when the deployment completes. (so, DON’T PANIC! – this is the cloud pak spinning up 3 pods of the integration server – it won’t show a green tick until all the pods are running. Give it a couple of minutes or so and refresh your browser.) 

The Servers page will also display any other integration servers that are installed in the same namespace.

Switch to ‘Integration’ view and click the ‘Tickets_StormIncWeatherAPI’ tile to see further the details about your integration API.

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.8.png)
![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.9.png)

You can see the REST operation; example test request and you can even download the OpenAPI (also called swagger) document. Hence, after you deploy an integration server to the cluster, you can view the underlying API definition. You can then test the API by using the built-in testing facilities. (learn more)

Repeat the same steps for ‘IncidentSummary’ and ‘classifyImagesV4’ assets. Eventually you will have all the integration APIs deployed as shown below. 

![](https://github.com/ilyastar12/markdown/blob/main/img2/Picture6.2.10.png)

Now would be a good time to test it again. 

You can also use the below ‘curl’ request examples, where you need to replace with your hostnames. Also remember to use the incident number returned from the first call in the subsequent calls.

### 1)	Call ticketsstormincweather API

curl --request POST \
  --url http://REPLACE_ticketsstormincweather_HOSTNAME/Tickets_StormIncWeatherAPI/StormData/stormpath \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"postCode": "70510:US", "date": "2019-07-13", "name": "Alan ACE"}'**

### 2)	Call classifyimages API
curl --request POST \
  --url http://REPLACE_classifyimages_HOSTNAME/classifyImagesV4/images/classify \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"incident_id": "REPLACE_INCIDENTNUMBER", "image_name": "my damaged car","image_url": "https://raw.githubusercontent.com/IBM/cp4i-demos/main/ace-weather-chatbot/images/car.jpg"}' **

### 3)	Call incidentsummary API
curl --request GET \
  --url http://REPLACE_incidentsummary_HOSTNAME/IncidentSummary/summary/REPLACE_INCIDENTNUMBER \
  --header 'accept: application/json' **













