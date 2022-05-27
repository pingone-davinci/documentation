# Acuant Connector


Author: Evan Green


# Introduction

Acuant®GO is a automated solution for identity verification, KYC, and digital onboarding.  The Acuant Connector for PingOne DaVinci allows a DaVinci flow to redirect to an Acuant®GO Customer Journey.


# Setup


## Resources

For information and setup help, see the following sections of the [Acuant®GO documentation](https://go-help.acuant.com/en/collections/3281656-acuant-go-v3-0)


## Requirements

To use the connector, you'll need: 


* Acuant®GO Subscription
* Completed Go Form Link


## AcuantGo Setup


1. Configure your Acuant®GO customer Journey
2. Configure result redirects
3. Add result Query Parameters


## Connector Setup


1. Create an Acuant Connector in your PingOne DaVinci Environment
2. Add the redirect URL from your Acuant Connection into the Integration AcuantGo Customer Journey into your connector
!(integration.png)
3. For each result, add a query parameter for Accept, Deny, or Review at the end of your PingOne DaVinci redirect URL, depending on the result. e.g. ?result=deny (see screenshot above)
4. Add the connection to a PingOne DaVinci Flow
5. Configure the Redirect to Journey capability with the AcuantGO Journey URL
6. Add any pre-poulated fields by clicking 'Add' and using the variable names as described in [Pass Field Information to a Journey through a URL](https://go-help.acuant.com/en/articles/5746430-pass-field-information-to-a-journey-through-a-url)



# Using the connector in a flow


You can use the connector in a variety of use cases, such as:


## Identity Verification

The connector can be used in a workflow to verify an identity as part of a workflow


## Onboarding

User data collection and identity verification as part of an onboarding flow


# Capabilities

### Redirect to Journey (initializeAuthorizationRequest)


Send user to the AcuantGo User Journey

#### Journey URL `textField`


The URL of the Journey in AcuantGo

#### Pre-populated Fields `variableInputList`


Pre-fill user information.

---



# Troubleshooting

For issues with AcuantGO please create a ticket in the [Acuant Support Portal](https://support.acuant.com/)
