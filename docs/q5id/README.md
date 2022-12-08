# Q5ID Connector


Author: Ryan Curtis 


# Introduction

The Q5ID connector can be leveraged in the PingOne DaVinci flow to identify an individual using Q5ID Proven Identity Services.


# Setup

The connector is used to submit info to Q5ID and as a callback handler.

## Connector settings

### Submit Info

- **First Name**:
The first name of the individual who would need to be identified and validated by Q5ID

- **Phone Number**:
The phone number of the individual who would need to be identified and validated by Q5ID

- **Q5Id Api Key**:
The Q5ID API Key license key 

- **Callback Handler:**
The webhook would receive the challenge id and the validation result.

# Using the connector in a flow

An example of using the connector in a flow is available as a template in the flow library as "Q5ID Simple Demo Flow".


## Use Case - Shopping Cart:

You can leverage the connector to validate the individual by using the combination of the phone number and the name of the person before permitting the transaction.
