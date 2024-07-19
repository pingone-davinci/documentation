# Sift Connector

Author:Inayat Shariff Owen Barnes


# Introduction

##  The Sift > Ping Connector can be used to protect your revenue from fraud by leveraging the Sift Score and Decisions API to get accurate risk profiling on your Customers. In addition, the Sift score can be used to create smoother workflows for good Customers by ensuring minimal friction is used for trusted users, both familiar and unfamiliar.

For example, you can use the Sift connector to retrieve a Sift score to determine the riskiness of a given log-in event. If the score returns low, you can skip additional friction such as certain types of verification or velocity checks on subsequent purchases, while quarantining high score accounts to limit their ability to engage with certain aspects of your business.

Sift uses cutting edge technology and its cohort data model to review the risk of users across a wide Customer base. 

For more information, see the Sift [API Documentation](https://developers.sift.com/docs/curl/apis-overview)


## Resources

For information and setup help, see the following sections of the Sift documentation:

* [Score API](https://developers.sift.com/docs/curl/score-api/overview)
* [Decisions API](https://developers.sift.com/docs/curl/decisions-api/overview)
* [Events API](https://developers.sift.com/docs/curl/events-api/overview)


## Requirements

To use the connector, you'll need:

* A valid Ping account with the Sift Connector added
* Sift Science credentials
* Sift Science API keys


## Sift Console Set up

Configure Sift Decisions.
Create a test Sift Workflow.
Copy the Sift Sandbox API key.

Configure Sift Decisions
In the Sift Console navigate to Automate > Decisions.

Create or edit Sift Decisions for Users based on the following categories:
- Category "Accept"
- Category "Block"
- Category "Watch"

For each Category, the configured decision will need to align with the decisions configured in DaVinci.
Create a test Sift Workflow.

Next, navigate to Automate > Workflows.

Here you will configure a new Workflow that will generate an automated decision or review case for each login attempt.

Full instructions for configuring Workflows can be found [here](https://developers.sift.com/tutorials/workflows)

Copy the Sift Sandbox API key.

Before managing real login events, you can test the Sift set up by configuring DaVinci to use the SIft sandbox environment, To do this, navigate to Developer > API Keys and 




You will use this Sandbox API key in the next section, Setting up the Connector



# Setting up the connector

In DaVinci, add a Sift connection. In DaVinci, Navigate to the Connectors tab > select “+Add Connector” > search for Sift > select the “+” button to add it to your connector library.

In most applications it will be necessary to capture device information for browser and/or mobile apps. Device information provides Sift with more intelligence to accurately identify potentially suspicious actions. With Sift device information is captured by integrating Sift’s JS Snippet (browser) or Mobile SDK (mobile app). Instructions for both are available here:

[JS Snippet integration instructions](https://developers.sift.com/docs/curl/javascript-api/overview)
[Mobile SDK integration instructions](https://developers.sift.com/docs/curl/mobile-sdk/overview)

## Connector settings
The Sift connector only requires the Sift API Key as part of its general configuration. Please see Step 3 of the Sift Console Set Up section for where to access and how to copy this key.

Capability specific configuration is located under the “Capabilities” section below.

## Capabilities

Each capability has its own unique configuration, with the exception of these standard fields for Event driven capabilities:

* Workflow Status: Receive the Workflow Decision synchronously when sending an event to Sift.
* Return Score: Get scores back when sending an event.
* Abuse Types: The type of abuse for which you want to send a label.
* Score Percentiles: Include scores percentiles when sending an event - this feature must be enabled as part of your plan.

See below for the specific configuration required per capability:

* Record Login Event
  * Login Status (required)
  * Failure Reason
  * User ID (required)
  * Session ID (required)
  * IP Address (required)
  * Email
  * Phone Number
  * Username
  * User Agent
  * Accept Language
  * Content Language
* Record Logout Event
  * User ID (required)
  * IP Address
  * User Agent
  * Accept Language
  * Content Language
* Record Create Account Event
  * User ID (required)
  * Session ID
  * Email
  * Phone Number
  * Full Name
  * Primary Phone Number
  * Billing (Name, Phone Number, Address, City, Region, Country, Zip Code)
  * Shipping (Name, Phone Number, Address, City, Region, Country, Zip Code)
  * IP Address
  * User Agent
  * Accept Language
  * Content Language
* Record Updated Account Event
  * User ID (required)
  * Changed Password
  * Email
  * Phone Number
  * Full Name
  * Billing (Name, Phone Number, Address, City, Region, Country, Zip Code)
  * Shipping (Name, Phone Number, Address, City, Region, Country, Zip Code)
  * IP Address
  * User Agent
  * Accept Language
  * Content Language
* Record Password Update Event
  * User ID (required)
  * Session ID (required)
  * Status (required)
  * Reason (required)
  * Email
  * Phone Number
  * IP Address
  * User Agent
  * Accept Language
  * Content Language
* Record Verification Event
  * User ID (required)
  * Session ID (required)
  * Status (required)
  * Verified Event
  * Verified Reason
  * Verification Type
  * Verified Value
  * IP Address
* Record Link Session to User Event
  * User ID (required)
  * Session ID (required)
  * IP Address
* Apply Decision
  * Account ID
  * User ID
  * Session ID Decision
  * Decision Type
  * Decision ID
  * Source (required)
  * Analyst
  * Description
* Get Decision Status
  * Decision Type
  * Account ID (required)
  * User ID
  * Session ID Decision
* Make Custom API Call
  * Endpoint (required)
  * Method (required)
  * Query Parameters
  * Headers
  * Body

## Using the connector in a flow

You can use the connector in a variety of use cases, such as:

### Record Login Event
Use Login to record when a user attempts to login.

### Record Logout Event
Use Log out to record when a user logs out.

### Record Create Account Event
Use Create Account to capture user details at account creation.

### Record Updated Account Event
Use Update Account to record changes to the user’s account information.

### Record Password Update Event
Use Password Update to record all password changes, whether initiated by the user or the service.

### Record Verification Event
When a user attempts a high-value activity (e.g., login, view or change account information) that you deem risky, you may decide to verify whether the user is who they say they are.

### Record Link Session to User Event
Use Link Session to User to associate data from a specific session to a user. Generally used only in anonymous checkout workflows.

### Apply Decision
The Apply Decisions API allows you to apply Decisions to users or sessions.

### Get Decision Status
The Decision Status API allows you to query the latest Decision for an entity. Sift returns the latest Decision status for each abuse type so that you have a full view of the entity.

### Make Custom API Call
Define a custom API call to Sift.

