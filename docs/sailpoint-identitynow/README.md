# Sailpoint IdentityNow Connector

Author: Peter Holko


# Introduction

SailPoint IdentityNow is the industry's first and only true SaaS identity governance solution that allows you to easily control user access to all systems and applications, enhance audit response and increase your operational efficiency.


# Setup

## Requirements

To use the all the capabilities of the IdentityNow connector the following tokens and secrets are required:

  * Personal Access ID and Secret or OAuth Authorization Code access token for capabilities requiring elevated permissions
  * Client Credentials ID and secret for any other capabilities 

Further details available here: https://documentation.sailpoint.com/saas/user-help/accounts/generating_tokens.html#:~:text=A%20personal%20access%20token%20is,(API%20clients)%20with%20IdentityNow.


## Setting up the connector

Under the SailPoint IdentityNow connection general configuration, enter the tenant ID, the Client Credentials client ID and client secret.

# Using the connector in a flow

After you have set up the SailPoint IdentityNow connector, you can use the connector to:

  * Create a non-Employee Request 
  * Approve a request
  * Reject a request
  * Get Public Identities 
  * Get Accounts
  * Get Non-Employee Sources
  * Create Account (to notify IdentityNow of out-of-band account creation)
  * Make Custom API Call

## Create a non-Employee Request

This capability will create a non-Employee Request in IdentityNow.  A Personal Access Token or OAuth Authorization Code access token is required to use this capability.

## Approve a request

This capability will approve a request.  A Personal Access Token or OAuth Authorization Code access token is required to use this capability.

## Reject a request

This capability will reject a request.  A Personal Access Token or OAuth Authorization Code access token is required to use this capability.

## Get Non-Employee Sources

This capability will retrieve the list of non-Employee Sources.  A Personal Access Token or OAuth Authorization Code access token is required to use this capability.

## Get Public Identities

This capability will retrieve any IdentityNow identities using a SCIM filter.  

## Get Accounts

This capability will retrieve any IdentityNow identities using a SCIM filter.  

## Create Account 

This capability will create an IdentityNow account on the specified source, to be used in scenarios where out-of-band account creation has occurred and IdentityNow is required to be notified of the new account prior to scheduled aggregation.  A Personal Access Token or OAuth Authorization Code access token is required to use this capability.

## Create Account 

This capability allows any IdentityNow API call to be used within DaVinci, the capability will retrieve an acco

# Capabilities

### Create Non-Employee Request (createNonEmployeeRequest)


This request will create a non-employee record.

#### API Authentication Method `dropDown` `required`


IdentityNow API Authentication Method


 - OAuth 2.0 Client Credentials
 - OAuth 2.0 Authorization Code
 - Personal Access Token

#### Access Token `textField`


Access Token from authorization code grant flow (Optional)

#### Personal Access Token ID `textField`


Personal Access Token ID (Optional)

#### Personal Access Token Secret `textField`


Personal Access Token Secret (Optional)

#### Account Name `textField`


Requested identity account name.

#### First Name `textField`


Non-Employee's first name.

#### Last Name `textField`


Non-Employee's last name.

#### Email `textField`


Non-Employee's email.

#### Phone `textField`


Non-Employee's phone.

#### Manager `textField`


The account ID of a valid identity to serve as this non-employee's manager.

#### Source Id `textField`


Non-Employee's source id.

#### Data `textArea`


Attribute blob/bag for a non-employee, 10 attributes is the maximum size supported.

#### Start Date `textField`


Non-Employee employment start date. Date time format (YYYY-MM-DDThh:mmTZD)

#### End Date `textField`


Non-Employee employment end date. (YYYY-MM-DDThh:mmTZD)

---

### Approve Non-Employee Request (approveNonEmployeeRequest)


Approves a non-employee approval request and notifies the next approver.

#### API Authentication Method `dropDown` `required`


IdentityNow API Authentication Method


 - OAuth 2.0 Client Credentials
 - OAuth 2.0 Authorization Code
 - Personal Access Token

#### Access Token `textField`


Access Token from authorization code grant flow (Optional)

#### Personal Access Token ID `textField`


Personal Access Token ID (Optional)

#### Personal Access Token Secret `textField`


Personal Access Token Secret (Optional)

#### Approval Item ID  `textField`


Approval Item ID of the IdentityNow request

#### Comment `textField`


Comment on the approval item.

---

### Reject Non-Employee Request (rejectNonEmployeeRequest)


This endpoint will reject an approval item request and notify user.

#### API Authentication Method `dropDown` `required`


IdentityNow API Authentication Method


 - OAuth 2.0 Client Credentials
 - OAuth 2.0 Authorization Code
 - Personal Access Token

#### Access Token `textField`


Access Token from authorization code grant flow (Optional)

#### Personal Access Token ID `textField`


Personal Access Token ID (Optional)

#### Personal Access Token Secret `textField`


Personal Access Token Secret (Optional)

#### Approval Item ID  `textField`


Approval Item ID of the IdentityNow request

#### Comment `textField`


Comment on the approval item.

---

### Get a list of public identities (publicIdentities)


Returns a list of public identities objects.

#### Offset `textField`


Offset into the full result set.

#### Limit `textField`


Max number of results to return.

#### Filters `textField`


Filter results using the standard syntax described in V3 API Standard Collection Parameters

---

### Get a list of accounts (accounts)


Returns a list of accounts.

#### Offset `textField`


Offset into the full result set.

#### Limit `textField`


Max number of results to return.

#### Filters `textField`


Filter results using the standard syntax described in V3 API Standard Collection Parameters

---

### List Non-Employee Sources (nonEmployeeSources)


This gets a list of non-employee sources.

#### API Authentication Method `dropDown` `required`


IdentityNow API Authentication Method


 - OAuth 2.0 Client Credentials
 - OAuth 2.0 Authorization Code
 - Personal Access Token

#### Access Token `textField`


Access Token from authorization code grant flow (Optional)

#### Personal Access Token ID `textField`


Personal Access Token ID (Optional)

#### Personal Access Token Secret `textField`


Personal Access Token Secret (Optional)

---

### Create Account (createAccount)


Notifies IdentityNow of an Out-of-Band account creation

#### API Authentication Method `dropDown` `required`


IdentityNow API Authentication Method


 - OAuth 2.0 Client Credentials
 - OAuth 2.0 Authorization Code
 - Personal Access Token

#### Access Token `textField`


Access Token from authorization code grant flow (Optional)

#### Personal Access Token ID `textField`


Personal Access Token ID (Optional)

#### Personal Access Token Secret `textField`


Personal Access Token Secret (Optional)

#### Source Name `textField`


Source Name in IdentityNow

#### Username `textField`


Username

#### User ID `textField`


User ID

#### Family Name `textField`


Family Name

#### Given Name `textField`


Given Name

#### Email `textField`


Non-Employee's email.

---

### Set Active Lifecycle State (setLifecycleState)


Sets the lifecycle of the identity profile of the user to active

#### API Authentication Method `dropDown` `required`


IdentityNow API Authentication Method


 - OAuth 2.0 Client Credentials
 - OAuth 2.0 Authorization Code
 - Personal Access Token

#### Access Token `textField`


Access Token from authorization code grant flow (Optional)

#### Source Name `textField`


Source Name in IdentityNow

#### Username `textField`


Username

#### Personal Access Token ID `textField`


Personal Access Token ID (Optional)

#### Personal Access Token Secret `textField`


Personal Access Token Secret (Optional)

---

### Make Custom API Call (makeCustomApiCall)


Define a custom API call to SailPoint IdentityNow.

#### API Authentication Method `dropDown` `required`


IdentityNow API Authentication Method


 - OAuth 2.0 Client Credentials
 - OAuth 2.0 Authorization Code
 - Personal Access Token

#### Personal Access Token ID `textField`


Personal Access Token ID (Optional)

#### Personal Access Token Secret `textField`


Personal Access Token Secret (Optional)

#### Access Token `textField`


Access Token from authorization code grant flow (Optional)

#### Endpoint `textField` `required`


The IdentityNow API endpoint, such as "accounts or identity-profiles".

#### API Version `textField` `required`


The IdentityNow API version ( ex. v3 )

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


# Troubleshooting

## IdentityNow Personal Access Token

Ensure the personal access token required for the non-Employee Request is not expired and has the required permissions.  
