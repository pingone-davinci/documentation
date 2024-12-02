# CLEAR Connector

**Author:** Matthew Teets

# Introduction

CLEAR is a secure identity verification platform that allows businesses to quickly and accurately verify users. With CLEAR’s hosted ID Verification UI, businesses can enhance user authentication while maintaining the integrity and privacy of sensitive data.

The CLEAR connector for PingOne DaVinci integrates CLEAR’s verification services into your workflows, enabling seamless identity verification processes. This connector supports creating verification sessions and retrieving verification results.

# Setup

## Resources
For information and additional help, see the following sections of the CLEAR Verified documentation:
- [CLEAR Documentation](https://docs.clearme.com/docs/getting-started)
- [API Keys](https://docs.clearme.com/docs/api-keys-1)
- [Web App Verification](https://docs.clearme.com/docs/web-app)
- [Verification Session API](https://docs.clearme.com/reference/api-keys)

## Requirements

To use the CLEAR connector, the following are required:
- A valid API Key for accessing CLEAR’s API.
- A Project ID for the specific CLEAR project you wish to integrate with.

These can be found inside your CLEAR Console.

## Setting up the connector

- Navigate to the CLEAR connector's general configuration in PingOne DaVinci.
- Enter the required credentials:
   - **API Key**: The API key provided by CLEAR.
   - **Project ID**: The ID of the CLEAR project you are integrating with.
- Configure the following properties:
   - **Secure Endpoint Selection**: Choose between the following:
     - `https://verified.clearme.com` (returns non-sensitive PII).
     - `https://secure.verified.clearme.com` (returns sensitive PII).

# Using the connector in a flow

After setting up the CLEAR connector, you can use it in your flows to:

- Redirect users to CLEAR’s hosted UI for verification.
- Retrieve and process user verification results.

## Capabilities

### Redirect to CLEAR

This capability redirects a user to CLEAR's hosted ID verification UI, then redirects them back into the PingOne DaVinci flow.


