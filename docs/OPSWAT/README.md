# OPSWAT MetaAccess Connector

Author: Josh Porth, Jerold Lodge

# Introduction

OPSWAT's MetaAccess provides zero trust access to applications by ensuring endpoints are compliant as part of attempting to authenticate with an IdP like Ping Federation or an authentication flow builder like Ping DaVinci.

As part of the authentication process, the connector consults with MetaAccess to confirm if the device is compliant based on the policies your organization configures in MetaAccess. If the device is compliant, then the device gains access as it normally would, if the device is not compliant, the user will either be just warned or fully blocked (based on configuration), until the device is brought into compliance. The user is provided detailed instructions on how to self-remediate.

# Setup

## Resources

For information and setup help, see the following sections of the MetaAccess documentation:

About MetaAccess:

- MetaAccess Platform Overview: https://www.opswat.com/products/metaaccess
- Getting Started: https://docs.opswat.com/macloud-sdp/configuration---management

Integrating with Ping Identity's Davinci:  
https://docs.opswat.com/macloud-sdp/integrations/ping-davinci-guide

## Requirements

To use the connector, you'll need:

- A free MetaAccess account, you can create one [here](https://id.opswat.com/register?SAMLRequest=nZPNbtswEIRfReBdskTblU1YDlwHQQ30R0jUHnpjyHVDQCJV7ip2376UrLQq0BpBbwQ5nB1%2Bu9zcnJs6egaPxtmCZUnKIrDKaWO%2FFexzdRev2M12g7KpW7Hr6Mnew%2FcOkKJwz6IYDgrWeSucRIPCygZQkBIPuw%2FvBU9S0XpHTrmaRXfOKxhMCnaUNQKLDrcFM%2Fox5av1ERbximsdL6TMwirnMV%2Fky3kmpZ7nb4IWS4lonuH3bcQODhZJWioYTzmP02WcrqssF%2BlSZHmyXs6%2FsqgcI7w19vKwa3kfLyIU76qqjMtPDxWLvrwACgJ2wcHFUN1PQPDrxiE8eAo2bPtE1KKYzYxOXIsnSYlyzWY29R2rtOJjMDrclq426se02Kux7%2BranfYeJAVy5DsYOtFIum7Q7xgdHwepaHsCSGCJzX5FG2cB9NDUvbMEZ%2FqvjHvXtNIb7BnDWSoaKYup874OCO%2FhOKnwauJXZUqo3jps9xN2cl73EwMqvKzy0mLrPF2689c827Fz%2FwAyHv%2F5f7Y%2FAQ%3D%3D&app=appMA0001&redirect=https://gears.opswat.com)

## Create OAuth Application

Once your account is created, you can proceed with [registering your application](https://gears.opswat.com/o/app/register). Following submission, applications are confirmed and Client Key and Client Secret strings are provided. These keys are unique and should remain confidential.

## Enable Cross-Domain API

Enable Cross-domain API settings, in **Settings > Integrations**, on your MetaAccess account.

Once the cross-domain API setting is enabled, MetaAccess agent tries to open a cross-domain API at the configured port on an endpoint. Please make sure that the configured port is valid and not used by any existing applications running on the same endpoint.

## Setting up the connector

In Ping DaVinci, add a **OPSWAT MetaAccess** connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector settings

#### Oauth Client ID

The Oauth Client Key obtained from creating an Oauth Application in MetaAccess. Copy and paste the Client Key from the Oauth Application in [MetaAccess](https://console.metaaccess-b.opswat.com/o/app).

#### Oauth Client Secret

The Oauth Client Secret obtained from creating an Oauth Application in MetaAccess. Copy and paste the Client Secret from the Oauth Application in [MetaAccess](https://console.metaaccess-b.opswat.com/o/app).

#### MetaAccess Domain (Optional)

The MetaAccess domain used for making API calls to MetaAccess. In almost all cases the default value (`gears.opswat.com`) is correct. If you are using a different tenant, for example, the Beta tenant, then the value should be changed to `gears-beta.opswat.com`.

#### Cross-Domain API Port (Optional)

The port number of Cross-Domain API. The default value of `11369` should be correct if you did not customize the port number when enabling the Cross-Domain API. Verify the Cross-Domain API port number in MetaAccess under **Settings > Integrations**.

# Using the connector in a flow

The OPSWAT MetaAccess connector is designed to help DaVinci flow builders limit a user's progress in a flow based on the user's devices compliance status with MetaAccess. The OPSWAT MetaAccess connector provides device compliance and access control functionality within Ping DaVinci Flows.

## Blocking non-compliant devices

Blocking non-compliant devices is the primary use case of the MetaAccess Conector. Simply putting the connector inline with your flow, effectily limiting the progress of non-compliant devices at the point where the MetaAccess Connector is placed.

For example, placing the MetaAccess Connector immediately after a PingOne SSO Connector will allow all users to authenticate, but will only allow compliant devices to continure past the MetaAccess Connector. Users progressing beyond the MetaAccess connector must have successfully authenticated with PingOne SSO and passed the MetaAccess compliance check.

# Capabilities

### Compliance Check (complianceCheck)


Check device's compliance

---

