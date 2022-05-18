# Human Connector

Author: Rick Rosser and Brian Henning

# Introduction

The HUMAN Connector is used to identify BOT threats using HUMAN signal data. This decision can used to mitigate BOT threats.

# Setup

## Resources

For information and setup help, see the following sections of the HUMAN documentation:

## https://docs.humansecurity.com/index.html

## Requirements

To use the connector, you'll need:

- [HUMAN JS Tag](https://docs.humansecurity.com/detection-tag.html)
- HUMAN Customer Id
- HUMAN Mitigation API Token
- HUMAN Policy Name (Optional)

## Setup form to capture HUMAN signal data.

To use the HUMAN connector, you will first need the HUMAN tag provided by your HUMAN representative. This tag will collect
and return signal data which will be passed to the HUMAN connector. Signal data is required to receive a bot-or-not decision from the HUMAN connector. 

You can view additional information about the HUMAN tag in the [documentation](https://docs.humansecurity.com/detection-tag.html).

There is also a sample flow template that demonstrates its usage.

## Setting up the connector

In Singular Key, add a **PingOne SSO** connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector settings

The following fields are required in the GENERAL tab:
* HUMAN Customer ID
  - Provided by your HUMAN representative 
* HUMAN Authentication Token
  - Provided by your HUMAN representative 
* HUMAN Policy Name
  - Provided by your HUMAN representative 
  - *This may be an empty string
* IP Address
  - Global property 
* User Agent
  - Global property 
* Session
  - OZ_TC property returned by HUMAN tag
* Payload
  - OZ_SG property returned by HUMAN tag
* DataToken
  - OZ_DT property returned by HUMAN tag

# Using the connector in a flow

You can use the connector in a variety of use cases, such as:

## User Registration/Login

The HUMAN tag should be loaded immediately to begin collecting signal data. Once the user finishes filling out the form and submits, you can retrieve the necessary fields (OZ_TC, OZ_SG, OZ_DT) provided by the HUMAN tag and pass those to their respective fields in the HUMAN connector (session, payload, dataToken). Please see the sample flow template for an example of this use case.

# Capabilities

### HUMAN Verification Engine (verification)


Know Who's Real on the Internet.

#### HUMAN Customer ID `textField`


Customer ID from HUMAN

#### HUMAN Authentication Token `textField`


Bearer Token from HUMAN

#### HUMAN Policy Name `textField`


HUMAN mitigation policy name

#### IP Address `textField`


IP address

#### User Agent `textField`


User Agent

#### Session `textField`


Session Token

#### Payload `textField`


Payload Token

#### Data Token `textField`


Data Token

---


