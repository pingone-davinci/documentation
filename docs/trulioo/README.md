# Trulioo Connector

# Introduction

Trulioo delivers a global identity platform that gives you the agility, ease and efficiency to onboard the right customers anywhere in the world while minimizing costs and mitigating fraud.

The Trulioo PingOne DaVinci connector leverages two capabilities to do this:
1. Verify
2. Make Custom API Call

This connector allows for flexibility in calling the Trulioo API’s with easy drag and drop functionality in any DaVinci flow.

# Setup


## Resources

For information and setup help, see the following sections of the Trulioo documentation:
* [Identity Verification Overview](https://developer.trulioo.com/docs/identity-verification)
* [Verify API](https://developer.trulioo.com/reference/post_v3-verifications-verify)
* [General Trulioo API Documentation](https://developer.trulioo.com/reference/trulioo-normalized-api-intro)
* [Integratoni Guide](https://developer.trulioo.com/docs/integration-guide)

## Requirements

To use the connector, you'll need:

* Client ID
* Client Secret

Both of these will need to be generated from within your Trulioo tenant and need to be configured on the connector Configuration pane. There are no other requirements regarding higher level configuration of the connector.

These combined are used to execute an API call to generate a bearer token that will be used in subsequent API calls made through the connector capabilities.


## Setting up the connector
* Navigate to the Trulioo connector via the Connections tab in DaVinci.
* Select New Connection in the upper right-hand corner
* Search for the desired connector (in this case, Trulioo).
* Click on the Trulioo connector and add it to your connector list.
* Add in the Client ID and Client Secret from the Requirements section above.



## Add connector to the canvas

You can add the connector to a canvas by navigating to Flows > Add Flow > Create New  > Select the black “+” button in the bottom left corner and search for Trulioo. 

For additional help help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


# Using the connector in a flow

You can use the connector in a variety of use cases, such as:

* Identity Verification for KYC or fraud use cases
* Get list of Country Codes
* Get Transaction Record
* Get Transaction Status
* etc… 

## Identity Verification

This capability sends a POST to the Verify endpoint: https://api.trulioo.com/v3/verifications/verify

A sample JSON body is provided below for the country of Great Britain (designated with CountryCode GB). This will vary depending on customer requirements and per country code. Please reference [v3 Verify API documentation](https://developer.trulioo.com/reference/post_v3-verifications-verify) on the Trulioo site for detailed information regarding each field.

```
{
    "VerboseMode": false,
    "PackageId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    "CleansedAddress": true,
    "CountryCode": "GB",
    "CustomerReferenceID": "{{ConsumerID}}",
    "VerificationType": "{{TruliooVerificationType}}",
    "DataFields": {
        "PersonInfo": {
            "FirstGivenName": "{{FirstName}}",
            "FirstSurName": "{{LastName}}",
            "DayOfBirth": {{dayWithoutLeading}},
            "MonthOfBirth": {{monthWithoutLeading}},
            "YearOfBirth": {{output.Year}}
        },
        "Location": {
            "City": "{{City}}",
            "PostalCode": "{{ZipCode}}",
            "AdditionalFields": {
                "Address1": "{{AddressLine1}}"
            }
        },
        "Communication": {
            "Telephone": "{{PhoneNumber}}"
        },
        "NationalIds": [
            {
                "Number": "{{IDNumber}}",
                "Type": "{{IDType}}"
            }
        ]
    }
}
```


## Make any Trulioo API call
The connector allows for very flexible usage through the https://api.trulioo.com/v3/ base API URL. 

Make Custom API Call (makeCustomApiCall)
Define a custom API call to Trulioo.

Endpoint textField required
The Trulioo API endpoint, such as "transaction/{id}/status".


Method dropDown required
The HTTP Method.

* GET
* POST
* PUT
* DELETE
* PATCH

Query Parameters keyValueList
Add query parameters and provide their values, if required.

Headers keyValueList
Add HTTP headers and provide their values.

Body codeEditor
The raw formatted JSON body.


## Troubleshooting resources


### Contact Trulioo

For technical support questions, please reach out to support@trulioo.com or call +1 778 658 0809.
