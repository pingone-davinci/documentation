Authors: Red Violet, Inc.

# Introduction

The IDI coreIDENTITY connector to Ping's Davinci platform serves an integral part of onboarding workflows. Using coreIDENTITY, you can easily perform identity data verification as part of a comprehensive KYC workflow. coreIDENTITY's KYC check can be performed in parallel or as part of a waterfall workflow to verify the consumer's PII data. In addition, the Ping connector can be used to perform attribute verification such as phone number verification, SSN verification, and address verification for workflows that require real-time verification of attributes. IDI has a full suite of Identity Data services to enable you to handle onboarding, transacting, and personalizing your consumer identity data while providing synthetic fraud signals.

# Setup

In DaVinci, add an IDI coreIDENTITY connector. For help, see [Adding a connector](https://docs.pingidentity.com/csh?context=davinci_adding_a_connection).
Configure your connector with the following Connector Settings and coreIDENTITY Connector Details in order to successfully setup the coreIDENTITY connector.
<br>

# Connector Settings

**Action**

There are 2 coreIDENTITY connector actions available:

1. KYC Verification - Select this for identity verification.
2. KYC Refresh - Select this to receive the most recent data.

**GLBA**

This is a string that specifies which GLBA selection you would like to make. Valid GLBA selections are specified in idiCORE's API documentation.

**DPPA**

This is a string that specifies which DPPA selection you would like to make. Valid DPPA selections are specified in idiCORE's API documentation.

**Raw JSON Payload**

This is a JSON object used to pass in the data that you have for the customer to the connector. The JSON object should match the format specified in idiCORE's API documentation.

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

Leave this section blank: it will be generated automatically.

## Troubleshooting

If you are having issues with the coreIDENTITY connector, you can try the following:

- For each connector in the flow, make sure that all of the mandatory inputs have been provided.
- Select the Options icon, and turn on Show Node ID. This will make it easier to identify the source of inputs and outputs.
- Use the Analytics feature to see where the flow stopped
