<p align="center" width="100%">
    <img src="https://marketplace.sumtotalsystems.com/content/images/vendor/SumTotal_logo.png"> 
</p>

# SumTotal Sample Code to Demonstrate Webhook/Event Usage

## Pre-requisites:
1. JDK latest version(Java 11 is used in this project).
2. Tomcat embedded Spring Tool Suite/Eclipse.

## Setup Guide:
1. Download the Source Code from GitHub Location.
2. Open SpringToolSuite/Eclipse in administration Mode.
3. Import the Project as Existing Maven Project (From File select Import, select Maven, then select existing Maven projects. After that select project location and project name).
4. Now right click on project and Run the project as Spring Boot App.
5. This will host the webhooklisterner and default browser url will be: [http://localhost:8080/](http://localhost:8080/)
6. Now the project is ready to receive the API calls. You can hit the project using the URL (http://localhost:8080/api/listenevent) or you can give your machinename in place of localhost in URL

## Steps:
1. Provide the webhooklisterner URL in webhooks configuration page, example: [http://localhost:8080/api/listenevent](http://localhost:8080/api/listenevent) or [http://machinename/api/listenevent](http://machinename/api/listenevent) 
2. If you are using http, make sure webhooks processor host and this sample project hosted in same domain/network - otherwise URL won’t hit the project when any event triggers
3. Trigger any event. It will call the post method "Listener" in ListenerController.java.
4. If you want to validate the payload signature value in request.header, copy the secretKey from webhookEndpoint in UI and update the secretKey in application.properties.

Trigger any event and it will show the signature is matched or not in response:
* If secretKey in application.properties is empty : response body in UI will be "Success and not validated the secret key as secretkey is empty".
* If secretKey in application.properties is updated correctly and if generated signature matched with request header signature, response body will be "Success and validated the secretkey with the payload signature and result is matched and secretkey is : xxxxx".
* If secretKey in application.properties is not updated correctly or if generated signature not matched with request header signature, response body will be "Success and validated the secretkey with the payload signature and result is NOT matched and secretkey is : xxxxx".
