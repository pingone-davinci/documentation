# SpyCloud Connector

Author: SpyCloud, Inc. 


# Introduction

The SpyCloud Enterprise Protection connector to Ping's Davinci platform serves an integral part of any password change workflow. Using SpyCloud’s extensive breach and malware data repository, you can easily test credential pair information against your SpyCloud watchlist to see if the user’s chosen password is exposed, allowing your users to choose another password that is not exposed.  


# Setup


## Requirements

To use the connector, you'll need:

* Configured SpyCloud Enterprise Protection Watchlist 
* SpyCloud Employee ATO Protection API Key configured for use with Ping DaVinci


## Configured SpyCloud Enterprise Protection Watchlist 

You will need to make sure your Enterprise Watchlist has been configured to include the domains that you plan to use with Ping. For example, if your user’s login with an email in the form xxx@example.com, make sure to include example.com in your watchlist and that example.com has been verified with SpyCloud. 

## SpyCloud Employee ATO Protection API Key configured for use with Ping DaVinci. 

Please request a SpyCloud Employee ATO Protection API Key and make sure that SpyCloud is aware that this API key is for use with Ping. 


## Setting up the connector

In DaVinci, add a SpyCloud connection. Navigate to the “Connectors” tab > select “Add Connector” > Search for SpyCloud Enterprise Protection > Select “ADD”.

Once it has been added to the connector library through the above steps, click into it. Add the SpyCloud Employee ATO Prevention API Key from your SpyCloud tenant and select “Apply”. You can now use the connector in a flow.


### Connector settings

[List and explain the connector settings that appear when the connection is opened from the **Connections** page. If you did not cover it earlier in the **Setup** section, tell the user how to complete each configuration field or where to get the information they need.

These typically on the **General** tab, but some connectors have a different name or multiple configuration tabs. Don't document **Capabilities**, or **In Flows**.]


# Using the connector in a flow

You can use the connector in a variety of use cases, such as:


## Check for compromised credentials using Email

Use this capability to check if an end user's email has been compromised in a data breach. This capability requires 2 inputs:
1. Email: Email of end user
2. inboundPassword: End user’s Password

Input Schema

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "email": {
            "type": "string",
            "description": "Email of end user"
          },
          "inboundPassword": {
            "type": "string",
            "description": "End user's password"
          }
        },
        "required": [
          "email",
          "inboundPassword"
        ]
      }
    },
    "example": {
      "properties": {
        "email": "sasha12@example.net"
      }
    }
  }
}

```

Output Schema

```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      },
      "isCompromised": {
        "type": "boolean"
      },
      "documentId": {
        "type": "string"
      },
      "sourceId": {
        "type": "number"
      }
    }
  }
}
```

## Check for compromised credentials using Username

Use this capability to check if an end user's username has been compromised in a data breach. This capability requires 2 inputs:
1. Username: Username of end user
2. inboundPassword: End user’s Password

Input Schema

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "username": {
            "type": "string",
            "description": "Username of end user"
          },
          "inboundPassword": {
            "type": "string",
            "description": "End user's password"
          }
        },
        "required": [
          "username",
          "inboundPassword"
        ]
      }
    },
    "example": {
      "properties": {
        "username": "lenny14846"
      }
    }
  }
}
```

Output Schema

```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      },
      "isCompromised": {
        "type": "boolean"
      },
      "documentId": {
        "type": "string"
      },
      "sourceId": {
        "type": "number"
      }
    }
  }
}
```

## Resources

Website: (spycloud.com)[https://spycloud.com/]
Please note, API reference documentation is located within the SpyCloud tenant

