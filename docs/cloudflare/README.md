# Cloudflare Connector


Author: Peter Holko


# Introduction

Cloudflare’s global cloud platform delivers a range of network services to businesses of all sizes around the world—making them more secure while enhancing the performance and reliability of their critical Internet properties.

The Cloudflare connector for PingOne Davinci currently allows Davinci to retrieve risk details of a specific IP address or domain from Cloudflare IP Intelligence platform. 


# Setup

## Requirements

To use the connector a Cloudflare API token will be required as well as the Cloudflare account ID.  

Further details on configuring a Cloudflare API token are available here: https://developers.cloudflare.com/api/tokens/create/


## Setting up the connector

Under the Cloudflare connection general configuration, enter the Account ID and API Token.  

# Using the connector in a flow

After you have set up the Cloudflare connector, you can use the connector to:

* Determine if a IP address has any risk types associated with it
* Determine if a Domain has any risk types associated with it


## IP Intelligence (Get IP Overview)

This capability returns the IP address details including any known associated risk types with the address.  If any risk types are returned the capability will return a riskFound boolean which can be used to either step-up or deny authentication.

IPv4 or IPv6 addresses are supported.  

The IP Intelligence endpoint must be enabled in the Cloudflare account to use this capability. 

## Domain Intelligence (Get Domain Overview)

This capability returns the Domain details including any known associated risk types with the domain.  If any risk types are returned the capability will return a riskFound boolean which can be used to either step-up or deny authentication.

The Domain Intelligence endpoint must be enabled in the Cloudflare account to use this capability. 

# Capabilities

### Get IP Overview (getIPOverview)


Returns Cloudflare IP Overview of a specific IP address

#### IP Address `textField`


IP Address

---

### Get Domain Overview (getDomainOverview)


Returns Cloudflare Domain Overview of a specific Domain

#### Domain `textField`


Domain

---

### Make Custom API Call (makeCustomApiCall)


Define a custom API call to Cloudflare.

#### Endpoint `textField` `required`


The Cloudflare API endpoint, such as "/accounts/eaa16507a7d5779d6b428b0780962120/intel/domain".

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


The raw formatted JSON body.

---

