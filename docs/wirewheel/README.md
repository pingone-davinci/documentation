# WireWheel Connector

Author: Ryan Schafer


# Introduction

Founded in 2016 by a team of privacy and technology experts, WireWheel is a leader in the privacy and data protection space. Leveraging the team’s deep privacy expertise, WireWheel has developed an easy-to-use platform that enterprises including large financial institutions, telecoms and consumer-facing brands use to manage their privacy programs.


# Setup


## Requirements

To use the connector, you'll need:

* WireWheel Base API URL: The Base API URL of the WireWheel environment
* Issuer URL: Issuer URL from WireWheel Channel settings
* Client ID: Client ID from WireWheel Channel settings
* Client Secret: Client Secret from WireWheel Channel settings

## Setting up the connector

In DaVinci, add a WireWheel connection.

Navigate to the “Connectors” tab within DaVinci > search in the top right corner “WireWheel” > Click into tile > Click “Add”.

Once the connector is added to the library, you can click into it and configure the General configuration. The connector can then be used as part of a flow.


# Using the connector in a flow

You can use the connector in a variety of use cases, such as:


## Get Channel Information

Retrieve WireWheel Channel Information

This capability requires a Channel ID as part of its configuration, which can be obtained from the WireWheel channel settings.

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "channel": {
        "type": "object"
      }
    }
  }
}
```


## Get Existing Consent

Retrieve the existing consent by the username

This capability requires a Username as part of its configuration, which can be obtained from a user input form earlier in the flow.

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "consent": {
        "type": "object"
      }
    }
  }
}
```


## Consent Form

Displays the WireWheel Consent Form

This capability has a few different inputs, as defined below:

* Channel ID (required): Channel ID from the WireWheel Channel settings
* Username (required): Username of the consent record
* Get Existing Consent (required): Toggle to retrieve existing consent record
* HTML Template: HTML template (a default template is provided) for the consent screen
* CSS: Styling for the webpage (a default template is provided)
* Script: Script to run for the webpage (a default template is provided)

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "consentPayload": {
        "type": "object"
      },
      "writeConsentStatusCode": {
        "type": "number"
      },
      "writeConsentStatusText": {
        "type": "string"
      }
    }
  }
}
```


## Write Consent Data

Saves the consent data to WireWheel

This capabibility requires a properly formatted JSON object for the Consent Payload.

Output Schema:

```
{
  "output": {
    "type": "object",
    "properties": {
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      }
    }
  }
}
```

## Resources

For information and setup help, see the following sections of the WireWheel documentation:

* [Wirewheel website](https://wirewheel.io/)
