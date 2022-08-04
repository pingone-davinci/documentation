# Microsoft Intune Connector


# Introduction

Microsoft Intune Connector can be used to access the resources and APIs available through Microsoft Graph. This connector allows you to:

1. User Device Management
2. Make Custom API Call

# Setup

## Resources

For information and setup help, see the following sections of the Microsoft Intune documentation:

- [Get Access Token](https://docs.microsoft.com/en-us/graph/auth-v2-service?context=graph%2Fapi%2F1.0&view=graph-rest-1.0#4-get-an-access-token)
- [Manage User Devices](https://docs.microsoft.com/en-us/graph/api/user-list-owneddevices?view=graph-rest-1.0&tabs=http)

## Requirements

To use the connector, you'll need:

- [Microsoft identity platform Account and API Access](https://docs.microsoft.com/en-us/graph/auth-v2-service?view=graph-rest-1.0)

## Setting up the connector

In Davinci, add a **Microsoft Intune** connection via the "Connections" tab in your Davinci Environment. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector Settings

Once you've added the Microsoft Intune connection click on it's logo, or click the "···" button and edit. You will see the connector's details pop-up. On the GENERAL tab, enter below Microsoft identity platform details:

1. Client ID
2. Client Secret
3. Tenant
4. Scope
5. Grant Type
6. Domain Name

and click apply. This ensures that whenever you use this connector you will not have to reenter this information and token generated using above parameters is used to authorize all capabilities in flow.

# Using the connector in a flow

## User Device Management

To get the list of devices that are owned by the user add a Microsoft Intune Connector in the flow studio. Then choose the User Device Management capability. Provide the parameters from previous nodes in the flow (HTML form) and submit the details.

## Make Custom API Call

To make an API call that is not available as a capability in the connector add a Microsoft Intune Connector in the flow studio. Then choose the Custom API Call capability. Provide the below properties from previous nodes in the flow (HTML form) and submit the details.

- Custom API End point (API path excluding Domain endpoint)
- Custom API Query parameters
- Custom API Request body
- Custom API Headers
- Custom API Method

# Capabilities

### Make Custom API Call (makeCustomApiCall)


Define a custom API call to Salesforce

#### Endpoint `textField` `required`


Endpoint

#### Method `dropDown` `required`


The HTTP Method.


 - GET
 - POST
 - PUT
 - DELETE
 - PATCH

#### Query Parameters `keyValueList`


Add query parameters and provide their values.

#### Headers `keyValueList`


Add HTTP headers and provide their values.

#### Body `codeEditor`


The raw JSON body, such as "{ "Username": "jsmith@example.com", "ProfileId": "00e8a0000024zkjAAA" }".

---

### User Device Management (userDeviceManagement)


User Device Management

#### User ID `textField`


user ID

#### User Principal Name `textField`


User Principal Name

---


# Limitations

Use of connector is limited by the availability of Microsoft Intune API and account access.
