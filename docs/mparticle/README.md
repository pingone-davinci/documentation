# mParticle Connector


Author: Ryan Schafer, Ping Identity


# Introduction

mParticle is a customer data platform (CDP) that helps companies collect, organize, and use customer data to power their marketing and other initiatives. The platform is designed to be easy to integrate and use, and it can help companies make decisions quickly and confidently.

The mParticle connector allows you to manage users in your account through the below capabilities:
*Create an account
* Get a single account
* Update an account
* Delete an account
* Get all audiences
* Get all calculated attributes
* Upload an event batch


# Setup


## Resources

For information and setup help, see the following sections of the mParticle API documentation:


* (Platform API Overview)[https://docs.mparticle.com/developers/platform/overview/]
* (Event API)[https://docs.mparticle.com/developers/server/http/]


## Requirements

To use the connector, you'll need:

* Client ID: Client ID from mParticle tenant
* Client Secret: Client Secret from mParticle tenant
* Pod: Pod from mParticle tenant. Only required for ‘Upload an event batch’ capability


## Setting up the connector

In DaVinci, add an mParticle connection. Navigate to the Connectors tab on the left menu and select “+ Add connector” in the upper right corner. Search for mParticle, click into it, and select “Add” to add it to your library. Once added, you can find it in the list of connectors and add the above configuration details (Client ID, Client Secret, Pod).


# Using the connector in a flow

You can use the connector in a variety of use cases, such as:


## Create an account

Create a new account within mParticle.

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "displayName": {
            "type": "string",
            "description": "The display name of the account."
          }
        },
        "required": [
          "displayName"
        ]
      }
    },
    "example": {
      "properties": {
        "displayName": "Firstname Lastname"
      }
    }
  }
}
```

## Get a single account

Get information on an existing account within mParticle.

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "accountId": {
            "type": "string",
            "description": "Account ID from your mParticle account."
          }
        },
        "required": [
          "accountId"
        ]
      }
    },
    "example": {
      "properties": {
        "accountId": "1"
      }
    }
  }
}
```





## Update an account

Update an existing account within mParticle

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "accountId": {
            "type": "string",
            "description": "Account ID from your mParticle account."
          },
          "updatedName": {
            "type": "string",
            "description": "The display name of the account."
          }
        },
        "required": [
          "accountId",
          "updatedName"
        ]
      }
    },
    "example": {
      "properties": {
        "accountId": "1",
        "updatedName": "Firstname Lastname"
      }
    }
  }
}
```









## Delete an account

Delete an existing account within mParticle

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "accountId": {
            "type": "string",
            "description": "Account ID from your mParticle account."
          }
        },
        "required": [
          "accountId"
        ]
      }
    },
    "example": {
      "properties": {
        "accountId": "1"
      }
    }
  }
}
```



## Get all audiences

Get all audiences for an account. Audiences allow you to segment your users and view their historical context for re-engagement, for example 'Abandoned Shopping Cart audience'

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "accountId": {
            "type": "string",
            "description": "Account ID from your mParticle account."
          }
        },
        "required": [
          "accountId"
        ]
      }
    },
    "example": {
      "properties": {
        "accountId": "1"
      }
    }
  }
}
```


## Get all calculated attributes

Calculated attribute is a read-only value about a single user, providing granular insight into user behavior. Create a flow that leverages this API to view 'check out' step, for example.

Input Schema:

```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "workspace": {
            "type": "string",
            "description": "Workspace number from mParticle account."
          },
          "nameOptional": {
            "type": "string",
            "description": "The display name of the account."
          }
        },
        "required": [
          "workspace"
        ]
      }
    },
    "example": {
      "properties": {
        "workspace": "1234",
        "nameOptional": "Firstname Lastname"
      }
    }
  }
}
```


## Upload an event batch

Send event data directly to mParticle

This capability does not have a standard input schema as there is a JSON text area that will be used to upload an event batch.
