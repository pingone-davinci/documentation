## Daon IDV Connector
 
Author: Ryan Schafer
 
 
# Introduction
 
The Daon IDV connector is an OIDC redirect to the Daon service for identity verification.
 
Once redirected to Daon, the end user will verify their identity and liveness through a selfie via photo verification. Once the photo has been submitted and processed, the end user will need to verify a document, and can choose from one of the following: 
Passport
Driver's license
Other ID Document
 
For ease of use, the Daon service allows the end user to complete this verification process on their mobile device, even if the flow was initiated on their computer.
 
# Setup
In order to use the Daon IDV connector within a flow, the customer must have a tenant to both Daon and PingOne DaVinci. Within the Daon tenant, the customer setting up the connector will need to gather the below OIDC configuration points:
* Issuer URL
* Authorization Endpoint
* Token Endpoint
* Userinfo Endpoint
* Client ID
* Client Secret

Daon support will provide these details for your specific tenant. Once gathered, this information will need to be entered on the configuration pane of the connector. To access this pane, add the connector to the library under the “Connections” tab in DaVinci. You can either configure the connector here by selecting on the newly added connection or go to “Flow Studio”, add the connector to a flow via the black “+” button, click on the connector on the canvas, and select the gear icon next to the name of the connection. There, you will see all the fields to add the above OIDC endpoint information.
 
Once the connector is fully configured, you will then need to copy the “DaVinci Redirect URL” from that same configuration pane and add it to your Daon tenant. This URL ensures that there is a redirect back to DaVinci once the connector has been fully executed.
 
 
## Resources
 
For information and setup help, see the following sections of the Daon documentation:

 
 
## Requirements
 
To use the connector, you'll need:
* Issuer URL (Located in Daon tenant)
* Authorization Endpoint (Located in Daon tenant)
* Token Endpoint (Located in Daon tenant)
* Userinfo Endpoint (Located in Daon tenant)
* Client ID (Located in Daon tenant)
* Client Secret (Located in Daon tenant)
* DaVinci Redirect URL (Located in DaVinci)
 
All of the above endpoints are required in order to complete the OIDC handshake between Daon and DaVinci.

 
# Using the connector in a flow
 
You can use the connector in a variety of use cases, such as:
 
 
## Photo Verification
 
The end user can verify their identity through a selfie. This will require a picture to be taken live and can be done on their mobile device.
 
 
## Document Verification
 
The end user can further verify their identity via a document upload. This capability will allow the end user to upload pictures via their device of either a passport, drivers license, or other document.

 
# Capabilities
 
Leave this section blank: it will be generated automatically
 
 
### Daon Support

For help with setup, please contact your Daon representative or Daon Support at support@daon.com

