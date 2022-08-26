# Badge Connector

Author: The Badge Inc. Team

# Introduction

The Badge DaVinci connectors provides privacy-preserving user authentication
services to all DaVinci flows using the Badge technology. The trigger is an
authentication request via any device – trusted, new, or shared. From there, the
customer can select their preferred authentication factors to enable a holistic and
safe user experience on any device.

# Setup

## Resources

For information and setup help, see the following sections of the Badge
documentation:

## Requirements

To use the connector, you'll need:

- A configured Badge tenant
- A Badge account to use for testing

## Setting up the Badge connector configuration

In DaVinci, add the Badge connector. For help, see
[Adding a connection](https://docs.pingidentity.com/csh?context=davinci_adding_a_connection).

### Connector settings

Badge provides an OpenId Connect (OIDC) Identity Provider API. Default values are provided for OIDC settings where appropriate.

To obtain a Client ID and Client Secret, please contact Badge sales. You will need to provide to Badge the value pre-populated in the connector config's **Redirect URL**.

#### Client ID

The OIDC Client ID. This value will be provided to you by Badge.

#### Client Secret

The OIDC Client Secret. This value will be provided to you by Badge, and should be kept secret.

#### Redirect URL

This value is generated automatically by Davinci. It must be provided to Badge to configure the Badge side of the integration.

#### Issuer URL

[OIDC Issuer Identifier](https://openid.net/specs/openid-connect-core-1_0.html#Terminology) for Badge. Most deployments should not need to change this from the default value.

#### Authorization Endpoint

[OIDC Authorization Endpoint](https://openid.net/specs/openid-connect-core-1_0.html#AuthorizationEndpoint) for Badge. Most deployments should not need to change this from the default value.

#### Token Endpoint

[OIDC Token Endpoint](https://openid.net/specs/openid-connect-core-1_0.html#TokenEndpoint) for Badge. Most deployments should not need to change this from the default value.

#### User Info Endpoint

[OIDC UserInfo Endpoint](https://openid.net/specs/openid-connect-core-1_0.html#UserInfo) for Badge. Most deployments should not need to change this from the default value.

#### Send state with request

If enabled, Davinci will auto-populate a random value to pass as the OIDC `state` parameter. This is enabled by default, but can be disabled if you want to provide a custom `state` as a query parameter in your flows.

If disabled, your flows should provide an alternative `state` as a query parameter.

Most deployments should not need to change this from the default value.

# Using the connector in a flow

## Authenticating users with Badge

![Example Badge connector flow](../assets/flow.png)

In a new flow, perform the following steps:

1. Create a sign on form:
   1. Add the **HTTP** connector and select the **HTML Form** capability.
   2. Configure the **HTML Form** node:
      1. Choose a **Title** such as `Sign in with Badge`.
      2. In the **Fields List** section, click **Add**.
      3. In **Property Name**, type `userName`.
      4. In **Display Name**, type `User Name`.
      5. In **Next Button Text**, type `Continue`.
      6. Click **Apply**.
2. Add Badge.
   1. Next in your flow, add the **Badge OIDC Connector**.
   2. Configure the **Badge** node:
      1. Under **Query Parameters**, click **+** to add a parameter.
      2. Enter `login_hint` for the **Key**.
      3. For the **Value**, click **{}** and select the `userName` output
         variable from your **HTML Form** above.
      4. Click **Apply**.
3. Show the result of Badge authentication

   1. Next in your flow, add the **HTTP** connector and select the
      **Custom HTML Message** capability.

   ***

   **Note:** In a production authentication flow, you will redirect the user
   to the resource they were attempting to access. In this demonstration
   flow, we'll just show the response from Badge.

   ***

   2. Configure the **Custom HTML Message** node:
      1. Choose a **Title**, such as `Sign in complete`.
      2. In **Message**, click **{}** and select the **output** variable from
         your **Badge OIDC Connector** node by clicking **+**.
      3. Click **Apply**.

4. Test the flow

   1. Click **Save**, **Deploy**, and then **Run**.
   2. On the **Sign in** page, enter the username of your Badge test user
      account. Click **Continue**. The browser will redirect to Badge login.

   ![Example sign in page](../assets/signin.png)

   3. Log in with Badge.
   4. On success, the browser redirects back to DaVinci. Your
      **Custom HTML Message** shows the result from Badge.

   ![Success](../assets/success.png)

For additional help, see the
[Creating an authentication flow](https://docs.pingidentity.com/csh?context=davinci_use_cases_creating_an_authentication_flow) guide.

# Capabilities

### Badge Authentication (loginFirstFactor)


OIDC redirect to Badge IdP

---
