# Keyr QR Login Connector

Author: Keyri, Inc.

# Introduction

The [Keyri](https://keyri.com) connector provides login-with-QR capabilities on your desktop web application.

Users scan the QR code, rendered by the Keyri web widget, on your web app's login page, and if they have your mobile app installed (which has the Keyri mobile SDK installed), the Keyri connector will validate the cryptographic signature sent by your mobile app. If the signature for the given user is valid, the Keyri connector will inform other connectors that can log the user in.

# Setup

## Before configuring your flow

- Create two applications on the [Keyri dashboard](https://app.keyri.com) - one with the domain name of your development environment web app and one with the domain name of your production web app on which the Keyri QR widget will actually be used.
- Configure your mobile apps to use the Keyri mobile SDK, employing the `appKey` obtained from the `Setup & Credentials` page of the Keyri dashboard. Instruction for mobile integration are available in the full [Keyri documentation](https://docs.keyri.com)

## Resources

For full information and setup help, including setup in your mobile app, please see the official Keyri documentation referenced above.

Additionally, you may leverage the example flow located [here](https://s3.us-east-2.amazonaws.com/static.keyri.com/Keyri-Ping-Assets/Keyri_DaVinci+Example+Login+Flow.json)

You can also see the full source code of demo iOS and Android apps configured to work with the PingOne system in the following repositories:

- iOS: (https://github.com/Keyri-Co/keyri-ios-ping)
- Android: (https://github.com/Keyri-Co/Keyri-Android-Example-Ping-Identity)

You can install our example Android app compatible with Keyri QR login to try the system for yourself: [download APK here](https://s3.us-east-2.amazonaws.com/static.keyri.com/Keyri-Ping-Assets/keyri-ping-example-debug.apk)

For the iOS example app, please contact us for TestFlight access through our [contact form](https://keyri.com/contact/)

## Requirements

To use the connector, you'll need:

- A valid Keyri account with two applications - one configured for your DaVinci development web app domain, and the other configured for your production web app domain.
- A mobile app configured to use the Keyri mobile SDK.

## Interacting with other connectors

1. The Keyri connector accepts three required inputs from other connectors: `User Public Key`, `Authentication Challenge`, and `User Signature`. The latter two are obtained directly from the Keyri web widget via a form submission, while the `User Public Key` should come from PingOne based on the `username` that your app sends as part of the payload via the Keyri mobile SDK.
   1. The Keyri connector can be used in conjunction with the `HTTP` connector's `Custom HTML Template` capability that is configured to render the Keyri QR widget. An example of this HTML template configuration can be found in the example flow file in this documentation directory. The HTML should include a form into which the Keyri QR widget will submit the user's `username`, `data` (Authentication challenge), and `userSignature`.
2. After the `Custom HTML Template` capability is configured, it must pass the `username` output to the PingOne connector's `Read User` capability.
3. The Keyri connector follows the PingOne Read User capability and received the `nickname` from PingOne, which is where the user's public key is stored
4. The Keyri connector outputs a boolean for whether or not the user's authentication request is valid. This boolean can be used in subsequent connectors to log the user in.

## Setting up the connector

The Keyri connector requires three parameters, each obtained from the preceding two connectors:

1. User Public Key: This should be the `nickname` from the PingOne "Read User" connector. Keyri uses the `nickname` user attribute to store the user's public key
2. Authentication challenge: This should be the `payload.output.data` value from the initial HTTP connector
3. User Signature: This should be the `payload.output.userSignature` value from the initial HTTP connector

# Troubleshooting

## Common solutions

If the Keyri QR code does not render on your webpage, please confirm in the Keyri [dashboard](https://app.keyri.com) that you have registered the correct domain for your application. You may create one service under the "Developer" plan for your development environment domain and another service for your live production domain.

## Troubleshooting resources

### Keyri documentation

You can review the full Keyri documentation here: (https://docs.keyri.com). Of particular use is the mobile app configuration section, where instructions on SDK installation, deep link setup, and login payload creation are provided.

# Capabilities

### Verify user's authentication request (verifyPayload)


Returns whether the user's login signature is valid

#### User Public Key `textField` `required`


Specify the user's nickname from the PingOne connector. This is the user's public key against which the signature is validated

#### Authentication challenge `textField` `required`


Specify the payload.output.data from the HTML template containing the Keyri QR code

#### User Signature `textField` `required`


Specify the payload.output.userSignature from the HTML template containing the Keyri QR code

---

