# 1Kosmos Connector

Author: Vinoth Baskaran

# Introduction

1Kosmos is the world's only cybersecurity solution that combines digital identity proofing and passwordless authentication. Using advanced biometrics and a private blockchain, BlockID by 1Kosmos protects your workforce and customers from password-based attacks by performing identity-based authentication.

# Setup

The 1Kosmos connector allows for easy integration with the BlockID passwordless experience by performing an OIDC redirect to 1Kosmos for device authentication, redirecting back to PingOne DaVinci to finish the authentication flow.

## Resources

Please see [OIDC Application Integrations](https://docs.1kosmos.com/productdocs/docs/app-integrations/oidc-application/) for more information on adding OIDC applications to BlockID.

## Requirements

To use the connector, you'll need:

- BlockID tenant with community admin access

## Setting up the connector

In DaVinci, add a new **1Kosmos connection** and assign it a name.
Click the hamburger menu for a new connection and select **edit** to view connection details.

Copy the **Redirect URL** to use in BlockID. The remaining details will be filled out after getting the required information in BlockID.

Open a new tab and log in to your BlockID tenant as a community admin.
In BlockID, click **Applications -> Add Application -> OIDC**.

Enter a name to use, and enter the following details:

- Grant Type: Authorization Code (recommended)
- Signing Algorithm for ID Token: RS256
- Sign-in Redirect URIs: your DaVinci **Redirect URL**

Click **create**. Your new OIDC application will now be visible, along with connection details.

Copy the following connection information to use in DaVinci:

- Client ID
- Client Secret

In DaVinci, add the **Client ID** and **Client Secret** you copied from BlockID to the 1Kosmos connection setup page.

Return to _BlockID_ to fetch the remaining details.
Click **Settings -> Authorization Server -> Metadata URI**

Copy the following parameters from the metadata response:

- Issuer URL
- Authorization Endpoint
- Token Endpoint
- User Info Endpoint

Return to DaVinci add the remaining details copied from BlockID: **Issuer URL**, **Authorization Endpoint**, **Token Endpoint**, **User Info Endpoint**.

Add **openid**, **email**, **profile** to Scope if not already present.
Toggle **Send state with request** to enable the setting.

Click **Apply** to save your settings and finish creating the 1Kosmos connector.

### Connector settings

# Using the connector in a flow

## Authenticating Users with 1Kosmos

Create a new **HTTP connector** and select the **HTML Form** capability.

Configure the **HTML Form** node:

1. Enter a **Title**, such as `Sign in with `1Kosmos`
2. In the **Fields List** section, click **Add**
3. In **Property Name**, type `email`
4. In **Display Name**, type `Email`
5. Click **Apply**.

Connect and add the **1Kosmos connector** to the flow.

Configure the **1Kosmos** node and add the following:

1. Under **Query Parameters**, add a new parameter
2. Enter `login_hint` as the **Key**
3. Under **Value**, click `{}` and select the `email` output variable from your **HTML Form**
4. Click **Apply**

# Capabilities

### Redirect to 1Kosmos (loginFirstFactor)


OIDC redirect to 1Kosmos

#### OIDC Login `button`

#### showPoweredBy `toggleSwitch`

#### skipButtonPress `toggleSwitch`

---

