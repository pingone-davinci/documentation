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

Output Schema

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
Output Schema

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

Output Schema

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
