# Berbix Connector

## Doc draft

Author:

# Introduction

Berbix is an instant and accurate identity verification platform. Berbix connector developed for Davinci can be used to:

1. Create Transaction
2. Get Transaction Verifications
3. Make Custom API Call

# Setup

## Resources

For information and setup help, see the following sections of the [Berbix documentation](https://docs.berbix.com/reference/introduction):

- [Create Transaction](https://docs.berbix.com/reference/createtransaction)
  - Required API secret key to create transactions. Refer [here](https://docs.berbix.com/docs/settings#section-api-keys) for API secret key generation steps
- [Get Transaction Verifications](https://docs.berbix.com/reference/gettransactionmetadata)
  - Require access token to get transaction data. Refer [here](https://docs.berbix.com/reference/createtoken) to generate the access token

## Requirements

To use the connector, you'll need:

- Berbix API and Account Access

## Setting up the connector

In Davinci, add a **Berbix** connection via the "Connections" tab in your Davinci Environment. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector Settings

Once you've added the Berbix connection click on it's logo, or click the "···" button and edit. You will see the connector's details pop-up. On the GENERAL tab, enter below details:

1. Domain Name
2. API Path
3. User Name

and click apply. This ensures that whenever you use this connector you will not have to reenter this information and above parameters are used to authorize all capabilities in flow.

# Using the connector in a flow

## Create Transaction

To creates a transaction that is associated with a provided CustomerUID add a Berbix Connector in the flow studio. Then choose the Create Transaction capability. Provide the input parameters from previous nodes in the flow (HTML form) and submit the details.

![Create Transaction](../assets/CreateTransaction.png)

## Get Transaction Verifications

To retrieve metadata about the transactions completed verifications add a Berbix Connector in the flow studio. Then choose the Get Transaction Verifications capability. Provide the input parameters from previous nodes in the flow (HTML form) and submit the details.

![Get Transaction Verifications](../assets/GetTransactionVerification.png)

## Make Custom API Call

To make an API call that is not available as a capability in the connector add a Berbix Connector in the flow studio. Then choose the Make Custom API Call capability. Provide the below properties from previous nodes in the flow (HTML form) and submit the details.

- Custom API End point (API path excluding Domain endpoint)

Update below capability level properties specific to the Custom API to be called:

- Custom API Query parameters
- Custom API Request body
- Custom API Headers
- Custom API Method

![Make Custom API Call](../assets/MakeCustomAPICall.png)

# Capabilities

### Get Transaction Verifications (getTransactionVerifications)


Get Transaction Verifications

#### Token `textField` `required`


Provide token

---

### Make Custom API Call (makeCustomApiCall)


Define a custom API call to Berbix

#### Token `textField` `required`


Provide token

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

### Create Transaction (createTransaction)


Creates a transaction that is associated with a provided Customer UID.

#### Template Key `textField` `required`


Template to associate with this transaction

#### Customer UID `textField` `required`


Unique identifier for the user. Used for duplicate ID detection.

#### Consents to automated facial recognition `toggleSwitch`


Whether the user has given consent to automated facial recognition Only effective if the corresponding customer setting is set

#### Email `textField`


Optional email adress to be used for pre-filling the handoff-to-phone screen on desktop.

#### ID Country `textField`


The 2-letter country code (ISO 3166-1 alpha-2) for the country that has issued the ID. Only pass this property if you intend to upload images through the Berbix API for this Transaction. Do not pass this property if you intend to use a web or mobile Guided SDK for this transaction. This field isn't required, but providing it may improve results.

#### ID Type `dropDown`


The type of the ID to be verified. Use 'P' for a passport, 'DL' for a driver's license, 'PRC' for a permanent resident card, 'PC' for a passport card and 'ID' for other types of ID cards. Only pass this property if you intend to upload images through the Berbix API for this Transaction. Do not pass this property if you intend to use a web or mobile Guided SDK for this transaction. This field isn't required, but providing it may improve results.


 - P
 - DL
 - ID
 - PRC
 - PC

#### Completion Email `textField`


Email address to alert when transaction has been completed This property should only be set if you intend to create a hosted transaction. Do not set this property if you intend to use a Guided SDK.

#### Redirect URL `textField`


URL to redirect the user to after they complete the transaction. If not specified, the URL specified in the Berbix dashboard will be used instead. This property should only be set if you intend to create a hosted transaction. Do not set this property if you intend to use a Guided SDK.

#### Phone `textField`


Optional phone number to be used for pre-filling the handoff-to-phone screen on desktop.

---


# Limitations

- Use of connector is limited by the availability of Berbix API and account access.
