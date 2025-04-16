# KYXStart Connector

Author: KYXStart Team

# Introduction

KYXStart is an AI-powered identity verification platform that redefines Identity Verification, KYC (Know Your Customer) and KYB (Know Your Business) processes. This connector allows you to seamlessly integrate KYXStart's advanced identity verification capabilities into your DaVinci flows. By leveraging KYXStart's global reach and AI-driven engine, you can verify and onboard customers and businesses efficiently, mitigate fraud in real-time, and ensure compliance with global regulations.
The main use cases this connector supports include:

* Real-time Identity Proofing: Verify the identity of new users during the onboarding process.
* Business Verification: Verify the legitimacy and details of businesses.
* Global Customer Onboarding: Verify individuals and businesses across 170+ countries.
* Risk Mitigation: Identify and prevent fraudulent activities by leveraging AI-driven data sequencing.
* Compliance Automation: Streamline KYC and KYB compliance requirements.
* Cross-Border Verification: Verify foreign-born individuals using their country-of-origin identity documents and visas.

# Setup

## Resources

For information and setup help, see the following sections of the KYXStart documentation:


## KYXStart API Documentation:
* KYXStart API Documentation https://api.prod.app.kyxstart.ai/v2/specs
* KYXStart Integration Guides: KYXStart Integration Guides https://api.prod.app.kyxstart.ai/v2/specs

KYXStart Help Center: KYXStart Help Center - support@kyxstart.com

## Requirements

To use the connector, you'll need:
* A KYXStart account: You need to have an active KYXStart account with the necessary credentials to access their API.
* KYXStart API Key: You will need to obtain your unique API key from your KYXStart account to authenticate the connector.
* Familiarity with KYC/KYB processes: Understanding the basic concepts of Know Your Customer and Know Your Business will be beneficial.

## Setting up the connector

In DaVinci, add an KYXStart connection. For help, see [Adding a connection](https://docs.pingidentity.com/davinci/connectors/davinci_adding_a_connector.html).

### Connector settings

When configuring the KYXStart connection in DaVinci, you will need to provide the following information:
* API Key: Enter the API key you obtained from your KYXStart account. This key is used to authenticate your requests to the KYXStart API.
* API Endpoint (Optional): In most cases, the default KYXStart API endpoint will be sufficient.

# Using the connector in a flow

Once the KYXStart connector is set up, you can use its capabilities within your DaVinci flows to perform various identity verification tasks.
You can use the connector in a variety of use cases, such as:

## New User Onboarding
Integrate KYXStart into your user registration flow to instantly verify the identity of new users. This can involve:
* Collecting user information: Gather necessary personal details from the user.
* Sending verification requests: Use the KYXStart connector to send the collected information to KYXStart for verification.
* Evaluating the verification response: Based on the response from KYXStart, proceed with the onboarding process (e.g., grant access, request further information, or reject the application).
* (Potential Flow Template): A generic "User Onboarding with Identity Verification" flow template in DaVinci could be adapted for use with the KYXStart connector.

## Business Account Creation
Incorporate KYXStart's KYB capabilities into your business account creation process to verify the legitimacy of organizations. This can involve:
* Collecting business details: Gather information such as company name, registration number, address, and key personnel.
* Submitting for verification: Use the KYXStart connector to send the business details for verification.
* Decision logic: Based on the verification results, decide whether to approve or reject the business account creation.
* (Potential Flow Template): A generic "Business Account Verification" flow template in DaVinci could be adapted for use with the KYXStart connector.

## High-Risk Transaction Monitoring
For specific transactions deemed high-risk, you can trigger KYXStart verification to ensure the identity of the transacting parties.
* Transaction risk assessment: Implement logic in your flow to identify potentially high-risk transactions.
* Identity re-verification: Use the KYXStart connector to re-verify the user's or business's identity before processing the transaction.
* Conditional approval: Approve or reject the transaction based on the outcome of the re-verification.

# Capabilities

## Send Verification request to KYXStart
This capability includes one input property, a **HTTP Body (JSON)** that requires a properly formatted JSON object. Example JSON body is below:

```
{
    "userConsent": true,
    "testMode": true,
    "clientReference": "test2",
    "checks": [
        "kyc2+2Basic"
    ],
    "country": "CAN",
    "ssn": "888888888", 
    "firstName": "John",
    "lastName": "Smith",
    "middleName": "",
    "address1": "11015 Bracebridge Rd",
    "city": "Alpharetta",
    "state": "GA",
    "postalCode": "30022",
    "province": "Fulton",
    "dob": "1977/12/01",
    "email": "johnsmith@gmail.com",
    "phoneNumber": "18888889999",
    "ipAddress": "99.4.33.103"
}
```

### Checks Array
Add the "check" value below to the "checks" array in the API call to return specific data for each type of verification. The more data that is provided on the end user, the more data will be returned to make better decisioning.

**KYXStart IDV**

check: kycPhoneBasic
* KYC 1+1 Basic + phone number verification + name-to-phone match
* Includes fraud analysis (device, email, IP, phone, name)

**KYXStart IDV Advanced**

check: kycPhoneAdvanced
* KYC 2+2 Basic + phone number verification + name-to-phone match
* More extensive fraud analysis and digital footprint evaluation

**KYXStart KYC 1+1**

check: kyc1+1Basic
* Name must match with at least 1 additional attribute (e.g., DOB, national ID, address) within a single data source
* No fraud analysis included

**KYXStart KYC 1+1 Advanced**

check: kyc1+1Advanced
* Name must match with at least 2 attributes within a single data source
* No fraud analysis included

**KYXStart KYC 2+2**

check: kyc2+2Basic
* Name must match with at least 2 attributes across 2 distinct data sources
* Same attributes may be matched in both sources
* No fraud analysis included

**KYXStart TrustFlow AML**

check: aml
* Anti-Money Laundering screening
* Watchlist screening, news media screening, PEP checks
* Used for regulatory compliance and financial risk mitigation

**KYXStart Fraud Check**

check: fraud
* Standalone fraud risk analysis
* Includes email risk, phone verification, postal validation, IP analysis, fraud scoring

**KYXStart Know Your Payee (KYP)**

check: kypBasic
* Name must match bank account details (account number, routing number etc)
* Optionally includes DOB, national ID, address
* No fraud analysis included

**KYXStart KYP Advanced**

check: kypAdvanced
* Same as KYP Basic but includes comprehensive fraud analysis

**KYXStart KYP Fraud**

check: kypFraud
* Standalone fraud analysis for user’s bank account
* No identity match with account required

**KYXStart KYP Phone**

check: kypPhoneBasic
* KYP Basic + phone verification + name-to-phone match
* No fraud analysis included

**KYXStart KYP Phone Advanced**

check: kypPhoneAdvanced
* KYP Advanced + phone verification + name-to-phone match

**KYXStart KYP Phone Fraud**

check: kypPhoneFraud
* KYP Fraud + phone verification + name-to-phone match

**KYXStart ProfileFill**

* check: prefill Streamlines identity verification by using minimal user input—such as phone number, SSN, or date of birth—to automatically generate complete, verified personal profiles by aggregating data from multiple trusted sources, including social networks and digital services.

## Common solutions

**Invalid API Key**: Double-check that you have entered the correct API key from your KYXStart account in the connector settings.

**API Connection Issues**: Ensure that your network allows outbound connections to the KYXStart API endpoint.

**Incorrect Input Data**: Verify that the data you are sending to the KYXStart connector in your flow matches the expected format and requirements of the KYXStart API (refer to their API documentation).

**API Rate Limiting**: If you are making a large number of requests in a short period, you might encounter API rate limits imposed by KYXStart. Review their API documentation for information on rate limits and implement appropriate throttling mechanisms in your flow.

## Troubleshooting resources

### KYXStart Portal
Consult the KYXStart Portal for support services, case management, and resolution of transaction issues. Access provided by KYXStart.

## KYXStart Support
Contact KYXStart's support team for assistance with any issues related to their API or your account at support@kyxstart.com


### Testing capabilities

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


# Limitations

* The specific capabilities and data points available for verification depend on your KYXStart account plan and the regulations in the target country. Refer to KYXStart's documentation for details on coverage and available features.
* The performance and response times of the KYXStart API are subject to their infrastructure and network conditions.
* Ensure that your usage of the KYXStart connector complies with KYXStart's terms of service and any applicable data privacy regulations.
