# Signicat Connector

Author: Peter Holko (peterholko@pingidentity.com)

# Introduction

The Signicat DaVinci connector redirects to the Signicat Identity Broker service which is a cloud platform where organisations can easily integrate a large number of ID methods via a simple user interface.  

# Setup

## Resources

For information and setup help, see the following sections of the Signicat documentation and lick on OpenID Connector tab: https://developer.signicat.com/express/docs/identification/guides/quick-start/#get-started 

## Requirements

To use the connector, you'll need:

- A configured Signicat tenant
- A Signicat user account to test authentication

## Setting up the Signicat connector configuration

In DaVinci, add the Signicat connector. For help, see
[Adding a connection](https://docs.pingidentity.com/csh?context=davinci_adding_a_connection).

### Connector settings

Signicat provides an OpenId Connect (OIDC) Identity Provider API. Default values are provided for OIDC settings where appropriate.

To obtain a Client ID and Client Secret create a OIDC client in the Signicat Dashboard. The DaVinci redirect URI is available on the Signicat Connector configuration screen which must be configured in the Signicat Dashboard. 

#### Client ID

The OIDC Client ID. This value is provided during the Signicat OIDC client creation.  

#### Client Secret

The OIDC Client Secret. This value is provided during the Signicat OIDC client creation.  

#### Redirect URL

This value is generated automatically by Davinci. It must be copied to the Signicat OIDC client in the Signicat Dashboard. 

#### Issuer URL

[OIDC Issuer Identifier](https://openid.net/specs/openid-connect-core-1_0.html#Terminology) for your Signicat tenant. 

#### Authorization Endpoint

[OIDC Authorization Endpoint](https://openid.net/specs/openid-connect-core-1_0.html#AuthorizationEndpoint) for your Signicat tenant.

#### Token Endpoint

[OIDC Token Endpoint](https://openid.net/specs/openid-connect-core-1_0.html#TokenEndpoint) for your Signicat tenant.
#### User Info Endpoint

[OIDC UserInfo Endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo) for your Signicat tenant.

#### Send state with request

When enabled, Davinci will auto-populate a random value to pass as the OIDC `state` parameter. This is enabled by default, but can be disabled if you want to provide a custom `state` as a query parameter in your flows.

If disabled, your flows should provide an alternative `state` as a query parameter.

Most deployments should not need to change this from the default value.

# Using the connector in a flow

## Authenticating users with Signicat

In your flow, perform the following steps (note the example below provides a login_hint query parameter to Signicat):

1. Add the Signicat Connector.
   1. Next in your flow, add the **Signicat Connector**.
   2. Configure the **Signicat** node:
      1. Under **Query Parameters**, click **+** to add a parameter.
      2. Enter `login_hint` for the **Key**.
      3. For the **Value**, click **{}** and select the `userName` output
         variable from your **HTML Form** above.
      4. Click **Apply**.
3. Show the result of Signicat authentication

   1. Next in your flow, add the **HTTP** connector and select the
      **Custom HTML Message** capability.

   ***

   **Note:** In a production authentication flow, you will redirect the user
   to the resource they were attempting to access. In this demonstration
   flow, we'll just show the response from Signicat.

   ***

   2. Configure the **Custom HTML Message** node:
      1. Choose a **Title**, such as `Sign in complete`.
      2. In **Message**, click **{}** and select the **output** variable from
         your **Signicat Connector** node by clicking **+**.
      3. Click **Apply**.

4. Test the flow

   1. Click **Save**, **Deploy**, and then **Run**.
   2. On the **Sign in** page, enter the username of your Signicat test user
      account. Click **Continue**. The browser will redirect to Signicat login.
   3. Log in with Signicat.
   4. On success, the browser redirects back to DaVinci. Your
      **Custom HTML Message** shows the result from Signicat.

For additional help, see the
[Creating an authentication flow](https://docs.pingidentity.com/csh?context=davinci_use_cases_creating_an_authentication_flow) guide.

# Capabilities

### Authenticate with Signicat (loginFirstFactor)


Redirects to Signicat via OIDC

---
