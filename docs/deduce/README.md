Author: Brandon Runkel, Senior Customer Success Engineer @ Deduce (brandon.runkel@deduce.com)

# Deduce Intelligent MFA
This guide details how to install and use the Deduce Intelligent MFA connector for your PingOne DaVinci flow. This no-code solution leverages our Deduce Identity Insights API and is configurable to more accurately determine when to present a challenge or trust a user at the moment of login.

## Requirements
To set up the Deduce Intelligent MFA connector, you'll need the following:
1. Deduce Insights API Key
2. Deduce Insights Site ID

# Integrate & Setup in Flow Studio
1. Select Add Integration (using the "+" symbol) at the bottom left corner of the Flow Studio.
2. With the connector present in the workflow, click on the Deduce step and select the blue pencil icon at the top of the panel. This is where you will input your API Key and Site ID (required) for making requests to the Deduce Insights endpoint.
3. The Connectors capabilities are available as a list at the connector level (under the text "Choose a Trigger or Action from the list"). Select the "Call Insights" capability from the list to set up your request.
4. With the "Call Insights" capability selected, you should see multiple tabs at the top of the modal. Select "General" to begin setting up how the request values will be passed to the Insights connector.
5. Parameters are made available to the Deduce connector from the global flow scope. Select the object brackets ("{}") at the right of the form input and select from "Global" scope to pass dynamic values into the Insights request. For example, for the IP field, it is recommended that you select "Global -> IP (string)" to pass in the users IP address value at the time the flow executes. For other values where the object brackets are not present, the option to pass dynamic values are not available. **NOTE:** Consult the table "Capability Configuration Reference" table below for additional information about the options and requirements for the Deduce Insights request.
6. The **Action** section should contain values based on implementation context. In the event a user is successful with login, the Deduce Intelligent MFA connector should use a value reflective of this result. In this particular example, the Deduce Intelligent MFA connector should be added to the flow with an action value of **auth.success.iam**. The same configuration can be used in a login failure case, to test for account cycling behavior (the value would of the action would be **auth.failure.iam**)
7. Once you have set up your Deduce Intelligent MFA connector with the "Call Insights" capability, click "Apply" to save your connector configuration.

## Capability Configuration Reference
The following table should be used to set required parameters for the Deduce Intelligent MFA request based on global environment variables:
**IP** = Global -> IP (string)
**User Agent** = Global -> UserAgent (string)
**Action** = Hard-coded based on context

## Passthrough Mode
The Deduce Intelligent MFA connector can be added without any action being taken in order to log responses based on data sent to the API.

To enable Passthrough Mode, with the capability selected, enable the toggle for "Passthrough" under "General -> Passthrough".

This will result in PingOne DaVinci user data being sent to the API and insights being returned but no action taken on the data returned.

## Production
In order to allow Deduce Intelligent MFA decisioning to impact the user flow, Passthrough Mode must be disabled. To disable Passthrough Mode, in the "General" section, select **&quot;Disable&quot;** in the Passthrough Mode toggle under the capability settings.

## Insights Signals
When users interact online, they create a digital fingerprint that characterizes their typical patterns of behavior. The networks, devices, geographies, and more all factor into our understanding of account identity. Deduce Identity Insights leverages this understanding and generates signals which are leveraged to help companies make security decisions that are uniquely tailored to them.

# Using the connector in a flow
You can use the Deduce Intelligent MFA connector in a variety of use cases, such as:

## Login - Success/Failure
The Deduce Intelligent MFA connector can be leveraged at the point of login, to analyze user details and conditions around specific outcomes, in order to better mitigate risk associated with user fraud and account takeover. When an authentication request responds with an outcome, you can plug in the contextual action values to the Deduce Insights request to gain a better understanding of this user/account observed behavior, and if the Deduce Identity Network deems this action to be a risk. 

# Capabilities
### Call Insights (callInsights)


Request signal data from Deduce Insights

#### IP `textField` `required`


The IP address for the user connection

#### Email `textField` `required`


The email address for the user profile

#### User Agent `textField` `required`


The user agent details for the user connection

#### Action `textField` `required`


The resulting action from the auth flow

#### Passthrough Mode `toggleSwitch` `required`


For testing purposes

---


# Troubleshooting
The following section describes troubleshooting techniques/suggestions for common errors:

(1) Request Time-Out -- check environment credentials (site ID / API key) -- if the request times out, it is likely that the connector is attempting to access a resource that either doesn't exist or is not available. Make sure your environment credentials are accurate and correspond to the correct Deduce Insights endpoint.

(2) Bad Request (Status 400) -- malformed JSON, missing or incorrectly formatted parameters -- if the request returns a "Bad Request - Status 400", this is likely due to the request body being incorrectly formatted. In this case, check how required parameters are being passed to the connector to ensure that they are formatted correctly in terms of type (these values should be type "string").

(3) Unauthorized (Status 401) -- incorrect credentials, endpoint not provisioned -- if the request returns an "Unauthorized - Status 401", verify that your credentials are correct and if the issue still persists, contact your Deduce representative for support.

### Testing capabilities

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).
