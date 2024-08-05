# iProov Connector


Author: Ryan Schafer (Ping Identity)


# Introduction

iProov's experience utilizes a secure inherence factor, facial biometrics, supplementing or complementing legacy identity processes. Identity proofing often relies on knowledge or possession factors which can be lost, stolen, or shared, resulting in fraud and abandonment. Static legacy systems struggle to keep up in the current environment, balancing user experience with providing security in an ever evolving threat landscape. With iProov it’s easy for organizations to create fully customized flows, without requiring users to jump through frustrating hoops or exposing them to social engineering and phishing. With robust device support, deepfake protection and flexible service levels based on use case, organization risk appetite, and level of identity assurance, we enable you to securely authenticate customers and workers anywhere, on any device, and in any flow.


# Setup


## Requirements

To use the connector, you'll need:

* iProov Tenant: The iProov tenant URL. This can be obtained from your iPortal account. **Do not include the protocol (https://)**. Please contact support@iproov.com for more information.
* iProov API Key: Your iProov Service Provider API key. This can be obtained from your iPortal account. Please contact support@iproov.com for more information.
* iProov Secret: Your iProov Service Provider Secret. This can be obtained from your iPortal account. Please contact support@iproov.com for more information.
* PingOne DaVinci tenant

The iProov details will need to be added to the General configuration tab from the connector. You can access this page after you add the connector to the connector library and click into it OR by adding the connector to a flow canvas, clicking into it, and selecting the gear icon next to the connectors name at the top of the connector window.

# Using the connector in a flow

You can use the connector in a variety of use cases, such as:

## Enrol new user in iProov

You can use the “Onboarding (Enrol)”, Custom HTML Template (to render the SDK), and “Validate Onboarding (Enrol)” capabilities to _*enroll a new user*_ in iProov.

Furthermore, you can use the “Onboarding (Photo Enrol)” capability to enroll a user using a trusted photo in iProov.

See the below flow JSON image for an example. This flow snippet can be downloaded from the iProov Enrol - Flow Snippet under the Resources section below.

![iProov Verify](iproovAuth.png)

## Authenticate existing user in iProov

You can use the “Authentication (Verify)”, Custom HTML Template (to render the SDK), and “Validate Authentication (Verify)” capabilities to _*authenticate an existing user*_ in iProov.

See the below flow JSON image for an example. This flow snippet can be downloaded from the iProov Verify - Flow Snippet under the Resources section below.

![iProov Auth](iproovVerify.png)


## Setting up the connector

In DaVinci, add an iProov connection. 

Navigate to the “Connectors” tab within DaVinci > search in the top right corner “iProov” > Click into tile > Click “Add”.


Once the connector is added to the library, you can click into it and configure the General configuration. The connector can then be used as part of a flow.


## Configure Enrol (Onboarding)

Generate a unique, one time use, enrolment token to create a new user on the iProov platform.

The primary purpose of this capability is to to generate a token that will need to be passed through to the SDK and will also be required in the “Validate Onboarding (Enrol)” capability. There are four fields to configure, as outlined below:

1. Resource: A traffic segregation mechanism based on use case. Please speak to your iProov Solution Architect for more information.
2. Assurance Type: The liveness assurance type, please speak to your iProov representative.
3. User ID: An anonymised pseudonym for a user. UUID is preferred. This must be stored for future authentication journeys.
4. Risk Profile: Only used for specific use cases, please speak to your iProov Solution Architect. 

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "resource": {
            "type": "string",
            "description": "The resource being accessed (e.g. URL)"
          },
          "assuranceType": {
            "type": "string",
            "description": "The assurance type of the claim"
          },
          "userId": {
            "type": "string",
            "description": "The asserted identifier of the user."
          },
          "riskProfile": {
            "type": "string",
            "description": "The pre-defined risk profile to use for this claim."
          }
        },
        "required": [
          "resource"
        ]
      }
    },
    "example": {
      "properties": {
        "resource": "onboarding",
        "assuranceType": "genuine_presence",
        "userId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "riskProfile": "D_33_1A"
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
      "fallback": {
        "type": "array"
      },
      "token": {
        "type": "string"
      },
      "primary": {
        "type": "string"
      },
      "user_id": {
        "type": "string"
      },
      "pod": {
        "type": "string"
      },
      "risk_profile": {
        "type": "string"
      }
    }
  }
}
```

## Configure Onboarding (Photo Enrol)

Enrol a user using a trusted photo (Identity document or other trusted source.)

This capability has 3 fields to configure, outlined below:

1. Image: The image to enrol the user with, in Base64 format
2. Token: The one time use token generated in the Onboarding (Enrol) step"
3. Source: The source of the trusted image: EID = from an electronic identity document (e-Passport), OID = Optically captured document (cropped image of the face), Selfie (Any other trusted source)

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "image": {
            "type": "string",
            "description": "The image to enrol the user with"
          },
          "token": {
            "type": "string",
            "description": "The enrolment token for the user"
          },
          "source": {
            "type": "string",
            "description": "The source of the image (i.e. Electronic ID or Optical ID)"
          }
        },
        "required": [
          "image",
          "token"
        ]
      }
    },
    "example": {
      "properties": {
        "image": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD",
        "token": "xxxxxxxxxxxxxx",
        "source": "selfie"
      }
    }
  }
}
```

Output Schema:
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
      "token": {
        "type": "string"
      },
      "user_id": {
        "type": "string"
      },
      "success": {
        "type": "boolean"
      }
    }
  }
}
```


## Configure Validate Onboarding (Enrol)

Validate the result from the iProov process and activate the user.

There are five fields to configure for this capability, as outlined below:

1. User ID: An anonymised pseudonym for a user. UUID is preferred. This must be stored for future authentication journeys.
2. Token: The one time use token generated in the Onboarding (Enrol) step 
3. Client: Fingerprint or client identifier of the device making the request (e.g. User Agent)
4. Risk Profile: Only used for specific use cases, please speak to your iProov Solution Architect.
5. Activate: Mark the user as active on the iProov platform – this should be True by default.

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "userId": {
            "type": "string",
            "description": "The asserted identifier of the user"
          },
          "token": {
            "type": "string",
            "description": "The token for the claim"
          },
          "client": {
            "type": "string",
            "description": "Fingerprint or client identifier of the device making the request (e.g. User Agent)"
          },
          "riskProfile": {
            "type": "string",
            "description": "The pre-defined risk profile to use for this claim."
          },
          "activate": {
            "type": "boolean",
            "description": "Activate the user's account (default: On). User will be SUSPENDED if Off."
          }
        },
        "required": [
          "userId",
          "token",
          "client"
        ]
      }
    },
    "example": {
      "properties": {
        "userId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "token": "xxxxxxxxx",
        "client": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)",
        "riskProfile": "D_33_1A",
        "activate": true
      }
    }
  }
}
```

Output Schema:

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
      "passed": {
        "type": "boolean"
      },
      "token": {
        "type": "string"
      },
      "type": {
        "type": "string"
      },
      "frame_available": {
        "type": "boolean"
      },
      "frame": {
        "type": "string"
      },
      "frame_jpeg": {
        "type": "string"
      },
      "reason": {
        "type": "string"
      },
      "risk_profile": {
        "type": "string"
      },
      "assurance_type": {
        "type": "string"
      },
      "signals": {
        "type": "object"
      }
    }
  }
}
```

## Configure Authentication (Verify)

Generate a unique, one time use, verify token to authenticate an existing iProov user.

Similar to the “Onboarding (Enrol)” Capability, there are four capabilities:

1. Resource: A traffic segregation mechanism based on use case. Please speak to your iProov Solution Architect for more information.
2. Assurance Type: The liveness assurance type, please speak to your iProov representative.
3. User ID: An anonymised pseudonym for a user. UUID is preferred. This must be stored for future authentication journeys.
4. Risk Profile: Only used for specific use cases, please speak to your iProov Solution Architect.

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "resource": {
            "type": "string",
            "description": "The resource being accessed (e.g. URL)"
          },
          "assuranceType": {
            "type": "string",
            "description": "The assurance type of the claim"
          },
          "userId": {
            "type": "string",
            "description": "The asserted identifier of the user."
          },
          "riskProfile": {
            "type": "string",
            "description": "The pre-defined risk profile to use for this claim."
          }
        },
        "required": [
          "resource"
        ]
      }
    },
    "example": {
      "properties": {
        "resource": "onboarding",
        "assuranceType": "genuine_presence",
        "userId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "riskProfile": "D_33_1A"
      }
    }
  }
}
```

Output Schema:

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
      "fallback": {
        "type": "array"
      },
      "token": {
        "type": "string"
      },
      "primary": {
        "type": "string"
      },
      "user_id": {
        "type": "string"
      },
      "pod": {
        "type": "string"
      },
      "risk_profile": {
        "type": "string"
      }
    }
  }
}
```

## Configure Validate Authentication (Verify)

Validate the result from the iProov process.

There are four different fields to configure for this capability.

1. User ID: An anonymised pseudonym for a user. UUID is preferred. This must be stored for future authentication journeys.
2. Token: The one time use token generated in the Onboarding (Enrol) step 
3. Client: Fingerprint or client identifier of the device making the request (e.g. User Agent)
4. Risk Profile: Only used for specific use cases, please speak to your iProov Solution Architect.

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "userId": {
            "type": "string",
            "description": "The asserted identifier of the user"
          },
          "token": {
            "type": "string",
            "description": "The token for the claim"
          },
          "client": {
            "type": "string",
            "description": "Fingerprint or client identifier of the device making the request (e.g. User Agent)"
          },
          "riskProfile": {
            "type": "string",
            "description": "The pre-defined risk profile to use for this claim."
          }
        },
        "required": [
          "userId",
          "token",
          "client"
        ]
      }
    },
    "example": {
      "properties": {
        "userId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
        "token": "xxxxxxxxx",
        "client": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)",
        "riskProfile": "D_33_1A"
      }
    }
  }
}
```

Output Schema:

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
      "passed": {
        "type": "boolean"
      },
      "token": {
        "type": "string"
      },
      "type": {
        "type": "string"
      },
      "frame_available": {
        "type": "boolean"
      },
      "frame": {
        "type": "string"
      },
      "frame_jpeg": {
        "type": "string"
      },
      "reason": {
        "type": "string"
      },
      "risk_profile": {
        "type": "string"
      },
      "assurance_type": {
        "type": "string"
      },
      "signals": {
        "type": "object"
      }
    }
  }
}
```

# Configuring the SDK

There is an SDK component that is required to complete a full iProov flow. Please reference the “Using the connector in a flow section” for a flow image that shows where the SDK is rendered as part of a flow snippet.

The templatized HTML, CSS, and Script are located below to copy into the HTTP > Custom HTML Template connector. There are a few important things to note regarding the Script section that **must** be changed for the SDK to process properly:

* On line 1, replace {{IPROOV URL}} parameter with the SDK URL provided by your iProov representative
* On line 3 and 31, replace the {{IPROOV TOKEN}} parameter with and source the token that is generated from the “Onboarding (Enrol)” or the “Authentication (Verify)” capabilities.

Please contact your iProov representative for any questions or issues.


HTML:

```
<div>   <p>UI - User Education & inital guidence placeholder</p><div id="iProov-wrapper"></div>  <form  id="iProovForm"  method="post"  >  <input type="hidden" name="iProovToken" id="iProovToken"/>  <input type="hidden" name="iProovEvent" id="iProovEvent"/>  <input type="hidden" name="iProovClientReason" id="iProovClientReason"/>    <button    type="hidden"    data-skcomponent="skbutton"    data-skbuttontype="form-submit"    class="hidden-button"    data-skbuttonvalue="submit"    data-skform="iProovForm"    id="iProovSubmitBtn"  ></button></form></div>



```

CSS:

```
.hidden-button{
 display: none;
}
```

Script:

```
import("{{IPROOV URL}}").then(function(module) {
 const iProovMe = document.createElement("iproov-me")
 iProovMe.setAttribute("token", "{{IPROOV TOKEN}}")
 iProovMe.setAttribute("base_url", "{{IPROOV URL}}")
 document.getElementById("iProov-wrapper").appendChild(iProovMe)




 iProovMe.addEventListener("ready", iProovEvent)
 iProovMe.addEventListener("started", iProovEvent)
 iProovMe.addEventListener("canceled", iProovEvent)
 iProovMe.addEventListener("streaming", iProovEvent)
 iProovMe.addEventListener("streamed", iProovEvent)
 iProovMe.addEventListener("progress", iProovEvent)
 iProovMe.addEventListener("passed", iProovEvent)
 iProovMe.addEventListener("failed", iProovEvent)
 iProovMe.addEventListener("error", iProovEvent)
 iProovMe.addEventListener("unsupported", iProovEvent)
 iProovMe.addEventListener("permission", iProovEvent)
 iProovMe.addEventListener("permission_denied", iProovEvent)
  function iProovEvent(event) {
   switch (event.type) {
     case "canceled":
     case "error":
     case "unsupported":
     case "permission":
     case "permission_denied":
     case "passed":
     case "failed":
       console.warn("iProov " + event.type + " - " + event.detail.reason)
       callback('{{IPROOV TOKEN}}',event.type,event.detail.reason)
       break
     case "progress":
       console.info(event.detail.message + " (" + event.detail.progress + "%)")
       break
     default:
       console.log("iProov " + event.type)
   }
 }




});




function callback(token, eventType, reason){


 document.getElementById('iProovToken').value = token;
 document.getElementById('iProovEvent').value = eventType;
 document.getElementById('iProovClientReason').value = reason;


 document.getElementById('iProovSubmitBtn').click();
 const iProovSubmitBtn = document.getElementById(
   'iProovSubmitBtn'
 );
 if (iProovSubmitBtn) {
   iProovSubmitBtn.addEventListener('click', true);
 }
}




```

Output Schema:

```
{
   "type": "object",
   "properties": {
       "buttonValue": {
           "type": "string",
           "propertyName": "buttonValue"
       },
       "iProovToken": {
           "type": "string",
           "propertyName": "iProovToken"
       }
       "iProovEvent": {
           "type": "string",
           "propertyName": "iProovEvent"
       }
       "iProovClientReason": {
           "type": "string",
           "propertyName": "iProovClientReason"
       }
   }
}
```

Define the Output Fields List to match the output schema:

iProov Token

1. Property Name: iProovToken
2. Display Name: iProovToken
3. Control Type: Text Field
4. Data Type: String

iProov Event

1. Property Name: iProovEvent
2. Display Name: iProovEvent
3. Control Type: Text Field
4. Data Type: String

iProov Client Reason

1. Property Name: iProovClientReason
2. Display Name: iProovClientReason
3. Control Type: Text Field
4. Data Type: String

Button Value

1. Property Name: buttonValue
2. Control Type: Text Field
3. Data Type: String


## Resources

For information and setup help, see the following sections of the Ping and iProov documentation:

* [iProov Enrol - Flow Snippet](https://support.pingidentity.com/s/marketplace-integration/a7iUJ0000000igzYAA/iproov-enrol-flow-snippet)
* [iProov Verify - Flow Snippet](https://support.pingidentity.com/s/marketplace-integration/a7iUJ0000000iibYAA/iproov-verify-flow-snippet)
* [iProov API Reference](https://secure.iproov.me/docs.html#section/Introduction)
