
# Google Analytics (Universal Analytics) Connector
  

Author: Scott Banducci (scottbanducci@pingidentity.com)


# Introduction

Google Analytics is a web analytics service offered by Google that tracks and reports website traffic, currently as a platform inside the Google Marketing Platform brand. This connector is for the **Google Analytics - Universal Analytics, Measurement Protocol API**. 

The Google Analytics Measurement Protocol allows developers to make HTTP requests to send raw user interaction data directly to Google Analytics servers. This allows developers to measure how users interact with their business. Developers can then use this connector  to:
-   Measure user activity in new environments.
-   Tie online to offline behavior.
-   Send data from both the client and server.

It does this via the only capability for this connector: **Send Event(Hit)**. 
# Setup


## Resources

For information and setup help, see the following sections of the Google Analytics documentation:

* [Google Analytics (Universal Analytics) Documentation](https://developers.google.com/analytics/devguides/collection/protocol/v1 " Overview for Google Analytics UA API Reference. Protocol Reference and Parameter Reference")

* [Common 'Hits' (events)](https://developers.google.com/analytics/devguides/collection/protocol/v1/devguide#commonhits "Documentation for common hit.")

* [Google 'Hit Builder' tool](https://ga-dev-tools.web.app/hit-builder/ "Hit builder tool to evaluate payload validity")


## Requirements


To use the connector, you'll need:

* A Google Analytics Account 
* A Google Analytics **Universal Analytics** Tracking ID
* Anonymous Client ID
* Hit Type
* Other mandatory parameters depending on the **Hit Type**

## Setting up the connector

  

In DaVinci, add a **googleanalyticsua** connection via the "Connections" tab. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings
  

Once you've added the connection click on its logo, or click the "**·****·****·**"  button and "Edit".

You will see the connector's details pop-up. On the GENERAL tab, enter in your

1) version number (probably "**1**")
2) Google Analytics Universal Analytics **Tracking ID** (UA-XXXXXXXXX-Y)

and click apply. This ensures that whenever you use this connector in a flow you will not have to reenter enter this information.


# Using the connector in a flow


The Google Analytics Universal Analytics connector allows you to send raw user interaction data to Google Analytics servers from within DaVinci. This allows you to measure how users interact with your DaVinci flows.

First, add the googleanalyticsua connector via the "Connections" tab (remember to setup your Version and Tracking ID). In the DaVinci Flow Studio add a googleanalyticsua connector. Select the only capability "Send Event(Hit)".  Some commonly used parameters are provided for your convenience. Any other parameters can be included in the contentInfoList List of key-value pairs where the key should be the parameter name (ex. "tid") and the value should be the corresponding value.


## Send Event(Hit)

The required values for each payload are:

* v=1              // Version.
* &tid=UA-XXXXX-Y  // Tracking ID / Property ID.
* &cid=555         // Anonymous Client ID.
* &t=              // Hit Type.

Depending on the **Hit Type** you are sending you will likely have other parameters required.   


# Capabilities
  

# Troubleshooting

Google Analytics Universal Analytics is scheduled to be discontinued in July 2023. At this time you will have to switch to Google Analytics 4 (GA4).

The contentInfoList key-value fields allows you to input any parameter(s) into your payload. 

All "Toggles" represent boolean values. Off is False, On is True.

# Limitations

This connector does not allow you to access the debug endpoint for Google Analytics: "www.google-analytics.com/**debug**/collect". If you need to use this for debugging it is recommended you first try the [Hit Builder](https://ga-dev-tools.web.app/hit-builder/ "Hit builder tool to evaluate payload validity") or Postman.
