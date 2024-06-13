# Forter Connector

Author: Tom Smith, Forter

# Introduction

You can use the Forter connector as part of a PingOne DaVinci flow to make risk-based decisions at major points in the user journey:

sign-up
sign-in
profile updates / account changes

Forter’s extreme precision ensures that good users experience no friction, while suspicious users can be challenged for a 2nd factor or denied altogether.

Forter’s extreme precision derives from our network of more than 1.5 billion identities that we have assembled by making identity-based decisions for many of the world’s largest brands. Using our patented ML algorithm, we compare each user event to the users and events we’ve seen over our last 10+ years of making identity-based decisions across the globe.

# Setup

## Setting up the connector

In DaVinci, add a **Forter** connection. For help, see [Adding a connector](https://docs.pingidentity.com/r/en-us/davinci/davinci_adding_a_connection).

## Connector settings

You can retrieve the necessary connector settings from your [Forter portal](https://portal.forter.com/app/developer/api/api/general/introduction).


### SiteID

### Secret Key

### API version

# Using the connector in a flow

You can use the Forter connector to retrieve a risk decision at any point in the user journey: sign-up, sign-in, profile updates / account changes.

Forter makes decisions by collecting information about the user’s device, network location, and online behavior through a JavaScript snippet. You should add Forter’s JavaScript snippet to all of the pages on your site (preferably) or at least the pages that are involved in identity decisions (sign-up page, login page, profile page).

The JavaScript snippet generates a token on the front end that is passed to Forter on the back end by the connector in order to get a decision from Forter. You can find documentation on the JavaScript snippet here: https://portal.forter.com/app/developer/api/api/services-and-apis/javascript-integration

The snippet can be embedded easily using the core HTTP connector and the HTML Template capability. Paste the JavaScript snippet referenced in the above documentation link to the Script code editor and update any HTML tags to properly capture the variable for the Forter Token, as this is required for the Forter capabilities. You will then be able to source this field by selecting on the {} of the Forter Token Cookie field within the Forter connector, selecting the HTTP connector in the dropdown you want to pull the value from, and then selecting the parameter.

## Sign-up

At the point of sign-up, Forter can return a decision of APPROVE, DECLINE, or VERIFICATION REQUIRED.

In the case of DECLINE, you can present your own custom error message to the suspicious user (or bot).

In the case of VERIFICATION REQUIRED, you can present your own message to the suspicious user and conduct an async review of the registration attempt.

## Sign-in

At the point of sign-in, Forter can return a decision of APPROVE, DECLINE, or VERIFICATION REQUIRED.

In the case of DECLINE, you can present your own customer error message to the suspicious user (or bot).

In the case of VERIFICATION REQUIRED, you can initiate an MFA challenge for the user via PingOne MFA or any other third party MFA provider available in the connector library.

Note that when Forter returns a VERIFICATION REQUIRED decision, Forter will include a `correlationId`. After the user has completed the MFA challenge (or not), this `correlationId` should be sent to the Forter’s Authentication Attempt API along with the result of the challenge (success || failure). This communication helps train the Forter model and, in the rare cases when Forter has incorrectly challenged a user, ensures that that user is extremely unlikely to be challenged again. 

## Profile Access

When a user is attempting to do something with their account that has financial or security considerations, Forter can return a risk decision. Examples of these types of changes include updating contact information such as a phone number, email address, or mailing address, and also adding payment methods (credit card) to an account.

As with the other points in the user journey, Forter can return a decision of APPROVE, DECLINE, or VERIFICATION REQUIRED.

## Make Custom API Call

The Forter connector includes a capability to send a custom API call to any Forter endpoint. This is particularly useful in cases where the built-in capabilities do not meet the data you are looking to capture. The Make Custom API Call capability can be used to capture the below custom configurations:
Endpoint
Method
Query Parameters
Headers
JSON Body

**Note**: For any custom JSON body that will have parameterized values, you will need to use dot notation to parse through the raw response and find the value you would like to send - EX {{local.`nodeId`.payload.output.`value`}} where `nodeId` is the node whose output you want to reference and `value` is what you would like to pass through from the raw output.

## Resources

For information and setup help, see the following sections of the Forter documentation:

[Forter developer portal](https://portal.forter.com/app/developer/api/api/general/introduction)

[Public Forter documentation (identity flows)](https://docs.forter.com/docs/account-takeover-protection)

## Troubleshooting resources

### Forter API docs and Integration guides:

​​https://docs.forter.com/reference/api-reference-overview

### Forter support email

support@forter.com

### Testing capabilities

To test API calls to Forter, you can use one of the following designated ip addresses in the connectionInformation.customerIP field of the API request:

0.0.0.1	APPROVED
0.0.0.2	DECLINED
0.0.0.3	NOT_REVIEWED
0.0.0.4	VERIFICATION_REQUIRED	['EMAIL_VERIFICATION']
0.0.0.5	VERIFICATION_REQUIRED	['SMS_VERIFICATION']
