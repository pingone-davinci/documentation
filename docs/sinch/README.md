# Sinch Connector

Author: Radosław Kot, Sinch


# Introduction

At Sinch, we give businesses the tools to boost their multi-factor authentication process with our versatile Verification API. Dive into our suite of phone number verification solutions, including SMS and Phone Call — all crafted with a sharp focus on security and user experience. Quick, reliable, and reaching users globally, our verification options are wallet-friendly and enterprise-trusted for swift onboarding and fraud deterrence.

# Setup

## Requirements

To use the connector, you'll need:

* An account at Sinch ([Setup an account for free](https://dashboard.sinch.com/signup))
* Application Key and Application Secret for Verification App from Dashboard
* Sufficient funds in the Sinch account


## Setting up Sinch account

See [how to sign up for your free Sinch account](https://community.sinch.com/t5/Customer-Dashboard/How-to-sign-up-for-your-free-Sinch-account/ta-p/8058)


## Retrieving Application Key and Secret

1. Open [Sinch Dashboard](https://dashboard.sinch.com) and log in
2. In Communication APIs menu to the left click on Verification
3. Click on Apps in a menu that appeared
4. Select an App (for new accounts App will be preselected for you)
5. Secret is an Application Secret and Key is an Application Key

You do not need to set other settings, defaults are ok. 

## Add credit to Sinch Dashboard account

See [how to add credit to your Sinch Dashboard account](https://community.sinch.com/t5/Customer-Dashboard/Adding-Credit-to-your-Sinch-Dashboard-Account/ta-p/12548)

## Setting up the connector

In DaVinci, add a Sinch connection. To do so, login to your PingOne tenant and open your DaVinci instance. Navigate to the Connectors tab on the left menu and select “Add Connector” and search for Sinch. Select the “+” icon on the tile for the connector and click Create.

Remaining on the Connectors tab, search for the Sinch connector you just added and click into it. Add the Sinch Application Key, Sinch Secret Key, and Language. All three of these fields are required to be completed in order to use the connector within a flow.


### Connector settings

The connector includes two capabilities as outlined below:
* Send Verification Code
* Verify Code

Review the below fields to configure the Send Verification Code capability:
* Method: Choose SMS or Phone Call. This changes how the code is delivered to the end user.
* Phone Number: Source this field from a form upstream in the flow. Select the {} icon and find the connector and phoneNumber field you would like to pull into this field.
* Expiry: Time after which verification process will be considered expired and reporting will no longer be possible. Accepts time in format HH:MM:SS.
* Code Type: Choose from Numeric, Alpha, Alphanumeric. The default is Numeric.

Review the below fields to configure the Verify Code capability:
* Method: This must match the Method from the Send Verification Code capability, otherwise this will error.
* Verification ID: This is returned as part of the output from the Send Verification Code capability (id)
* Code: Verification Code sent to end user via SMS or Phone Call

# Using the connector in a flow

This connector serves a single use case: verifying that the user possesses a phone number. It accomplishes this by sending a One Time Password (OTP) to a phone number through either an SMS message or a phone call.

Any flow using the Sinch connector will require a subsequent Functions connector on the back end of the Verify Code capability to properly parse the API response. Choose the A == B (Multiple Conditions) capability. Set Value A to status (select the {} icon, choose the Sinch - Verify Code connector earlier in the flow and find "status" in the list). Set value 1 to SUCCESSFUL, value 2 to PENDING, and value 3 to FAIL. Apply your changes. From the PENDING branch of the Functions connector, drag and release. Add an Error Customize connector and configure the message to your liking. This allows the end user retry their code up to 5 times.

Please reference the below image in the SMS Verification section for reference.


## SMS verification

Use this flow to deliver OTP via SMS message.

![Sinch Flow Image](sinchFlowImage.png)


## Phone call verification

Use this flow to deliver OTP via phone call.

The flow follows the same structure as the SMS Verification, just with “Phone Call” selected for the Method field. 


# Troubleshooting

While this integration aims to streamline the process, should you encounter any issues, consider the following:

- **Sufficient credits**: Ensure that your Sinch account has an adequate amount of credits.
- **Key and secret accuracy**: Double-check for typos in your App key or secret.
- **Transient problems**: Potential issues could arise from transient errors or reaching rate limits. Please wait for 5 minutes to eliminate this possibility.

If problems persist, reach out to Sinch support. Remember to include the `reference` or `id` returned from the Verification Service. Including it will facilitate the debugging process, enabling Sinch support to quickly diagnose and resolve your problem.

See also common problems below.

### The same code delivered multiple times

Sinch may reuse the code for subsequent verifications of the same number if previous attempts have failed. This approach addresses the issue of out-of-order or delayed OTP deliveries. If a user restarts the verification due to a missing message, and the original message arrives after the new verification has begun, reusing the same code prevents user confusion.

### Code type is not respected

If the code type is specified as Alphanumeric, but the OTP delivered consists only of digits, it is likely still correct. Alphanumeric means the code is generated from both digits and letters, but each OTP may not necessarily include both types. Perform a few verifications to confirm.

## Common solutions


### OTP code is not delivered

It is possible that SMS is not delivered or a phone call fails, especially in countries with less developed telco infrastructure. To mitigate this, ensure your process allows for user-initiated restarts.


## Troubleshooting resources

### Verification documentation

The portal includes documentation of all Verification APIs utilized by the connector. This information may assist in understanding the internals of the verification process. [Go to documentation](https://developers.sinch.com/docs/verification/)

### Sinch Community

A portal containing numerous articles on general Sinch matters—such as setting up accounts, adding credit, and more—also provides in-depth descriptions of various verification methods. Visit [Sinch Community](https://community.sinch.com/)


# Limitations

## Other verification methods

The connector supports only a subset of verification methods offered by Sinch. If you wish to utilize a method not supported by the connector, you'll need to directly integrate with Sinch.

## Sms templates 

The connector does not permit the specification of SMS Templates; this must be done through Sinch support. This limitation arises from the intricate and non-uniform legislation governing SMS templates across different countries.
