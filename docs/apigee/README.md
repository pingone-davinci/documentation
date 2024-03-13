
# Google Apigee Edge Connector


Author: Ping Identity


# Introduction

Apigee Edge is a platform for developing and managing APIs. By fronting services with a proxy layer, Edge provides an abstraction or facade for your backend service APIs and provides security, rate limiting, quotas, analytics, and more.

The Apigee Edge connector in PingOne DaVinci includes a single capability to retrieve the Apigee Edge Token from 

# Setup
To set up the connector you will need the Apigee Edge OAuth2 client created for PingOne DaVinci and the following configuration items listed below:

* Audience
* Issuer
* Token Endpoint
* Client ID
* Client Secret (for Client Credentials)
* Signing Algorithm (for JWT)
* Signing Private key (used to sign the client assertion)
* Token Endpoint Authentication Method (for Client Credentials)
* kid (To include in the client assertion)
* Expiry (for JWT)


## Resources

For information and setup help, see the following sections of the Apigee Edge documentation:

- https://docs.apigee.com/api-platform/get-started/what-apigee-edge


## Requirements

To use the connector, you'll need:

* Apigee Edge tenant and OAuth2 client 


### Connector settings

In the connector settings, under General, provide the following:

* Audience: The Apigee Edge OAuth2 audience value
* Issuer: The Apigee Edge OAuth2 issuer value
* Token Endpoint: The Apigee Edge OAuth2 token endpoint
* Client ID: The Apigee Edge OAuth2 client ID
* Signing Private Key: The Apigee Edge private key to sign the client assertion
* Kid: The Apigee Edge key id to include the client assertion

# Using the connector in a flow

You can use the connector in a flow to retrieve the Apigee Edge access token. 

## Use Case

The connector gives an organization the ability to terminate all PRA sessions on a host (by hostname) and/or terminate all PRA sessions a particular identity (by username) may have across any host.   The hostname and/or username can be provided to the connector though a HTML form, or can be fed directly into the connector as part of a larger workflow. 


# Capabilities

### Get Token witj JWT


Returns the the Apigee Edge token for the specified client

### Get Token with Client Credentials


Returns the the Apigee Edge token for the specified client


