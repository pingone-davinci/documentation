# coreIDENTITY Connector

Authors: IDI, LLC.

# Introduction

IDI's coreIDENTITY Connector provides a seamless method to implement low friction identity workflows for your customers. The connector enables input of claimed identity data and returns match results against our authoritative source data. The results include match/no-match/partial-match at the identity and attribute level. In addition, IDI returns synthetic ID and fraud flags which uses our suite of fraud checks and algorithms. The API will also return match scores, reason codes, data source classifications, and OFAC check.

In addition to Identity Verification, the connector also returns current PII information for a claimed identity. Enterprises can use this capability to maintain freshness of consumer information, ensure continual KYC compliance, and implement solutions such as verified pre-fill.

The DaVinci connector easily enables you to implement our KYC API's for Identity Verification or Identity Data Refresh as part of your identity workflows. It can be implemented post doc-verification to address the high 'indeterminant' signals from most doc auth processes. In addition, the API's allow for single attribue verification such as SSN or phone verification to enable step-up authorization or processes such as pre-verified pre-fill.

# Setup

In DaVinci, add a coreIDENTITY connector. For help, see [Adding a connector](https://docs.pingidentity.com/csh?context=davinci_adding_a_connection).
Configure your connector with the following Connector Settings and coreIDENTITY Connector Details in order to successfully setup the coreIDENTITY connector.
<br>

# Connector Settings

**Action**

There are 2 coreIDENTITY connector actions available:

1. KYC Verification - Select this for option to verify consumer identities.
2. KYC Refresh - Select this to receive the most recent name and contact information (e.g. phone, email, IP address, mailing address) for a given consumer.

**GLBA (Gramm-Leach-Billey Act)**

The GLBA parameter in your request specifies the GLBA-approved use case that your organization is operating under. Valid GLBA selections are specified in idiCORE's API
documentation.

**DPPA (Drivers Privacy Protection Act)**

The DPPA parameter in your request specifies the DPPA-approved use case that your organization is operating under. Valid DPPA selections are specified in idiCORE's API
documentation.

**Raw JSON Payload**

This is a JSON object used to pass your search parameters (e.g. name, SSN, DOB) to the connector. The JSON object should match the format specified in idiCORE's API
documentation.

# coreIDENTITY Connector Details

**Company Key**

This is the unique key assigned to your company in idiCORE. If you haven't received your Company Key from idiCORE, please contact idiCORE's customer support.

**API Secret**

This is the API Secret provided to you by idiCORE. If you haven't received your API Secret from idiCORE, please contact idiCORE's customer support.

**Environment**

This is the coreIDENTITY environment you would like to query. 'API Test' is available for testing purposes, be sure to switch to 'Production' when ready.

**Site Key**

This is the Site Key provided to you by idiCORE. If you haven't received your Site Key from idiCORE, please contact idiCORE's customer support.

**Unique URL**

This is the Unique URL provided to you by idiCORE. If you haven't received your Unique URL from idiCORE, please contact idiCORE's customer support.

## Resources

In DaVinci, add a coreIDENTITY connector. For help, see [Adding a connector](https://docs.pingidentity.com/csh?context=davinci_adding_a_connection).  
<br>

# Using the connector in a flow

You can use the coreIDENTITY connector to add identity verification to different types of flows, such as when new customers sign up.

# Capabilities

### KYC Verification (getKYCVerification)

Calls the KYC Verification endpoint in idiCORE

#### GLBA Selection `textField` `required`

Please enter your GLBA selection

#### DPPA Selection `textField` `required`

Please enter your DPPA selection

#### Raw JSON Payload `codeEditor`

Optional Raw JSON Payload

---

### KYC Refresh (getKYCRefresh)

Calls the KYC Refresh endpoint in idiCORE

#### GLBA Selection `textField` `required`

Please enter your GLBA selection

#### DPPA Selection `textField` `required`

Please enter your DPPA selection

#### Raw JSON Payload `codeEditor`

Optional Raw JSON Payload

---

## Troubleshooting

If you are having issues with the coreIDENTITY connector, you can try the following:

- For each connector in the flow, make sure that all of the mandatory inputs have been provided.
- Select the Options icon, and turn on Show Node ID. This will make it easier to identify the source of inputs and outputs.
- Use the Analytics feature to see where the flow stopped
