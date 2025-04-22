# Intellicheck Connector

Author: Intellicheck 
 
# Introduction 
Intellicheck is the only identity validation platform that uses a unique and proprietary analysis of DMV-issued IDs to create trusted, real-time customer identity verification experiences. To make the process easier, Intellicheck provides a PingOne DaVinci connector. The connector integrates the Intellicheck Capture solution. Intellicheck Capture sends a text to your customer’s mobile phone, and then the customer completes the identity validation process on the phone. Intellicheck Capture can be a one, two, or three-step process depending on the use case. Intellicheck Capture validates the identity document. It can also handle facial liveness, risk scoring, international documents, and additional checks for regulatory needs. Results are delivered back to the connector for your associate. The customer does not see results.

## Resources 
Before you begin, take a few moments to familiarize yourself with the developer documentation for Intellicheck Capture.

### Intellicheck Capture documentation 
* [About Capture](https://idn-capture.readme.io/docs/capture)
* [API Reference: Start Endpoint](https://idn-capture.readme.io/reference/mvp_start_api_v1_start_post)
* [Document Type Descriptions](https://idn-capture.readme.io/docs/document-type-descriptions-1)
* [Signal Descriptions](https://idn-capture.readme.io/docs/signal-descriptions)

### DaVinci Documentation 
* [Adding a connector](https://docs.pingidentity.com/davinci/connectors/davinci_adding_a_connector.html)
* [Using connectors securely](https://docs.pingidentity.com/davinci/connectors/davinci_using_connectors_securely.html)
* [Using DaVinci flow templates](https://docs.pingidentity.com/davinci/flows/davinci_using_davinci_flow_templates.html)

## Requirements 
To use the connector, you will need the following: 

* Your Intellicheck API key
* Your unique Intellicheck customer ID 

Contact your Intellicheck account executive or visit https://www.intellicheck.com/support 

# Setting up the connector 
Add the connector in DaVinci as shown in [Adding a connector](https://docs.pingidentity.com/davinci/connectors/davinci_adding_a_connector.html). 


# Start a Transaction 
The connector submits a request to the Intellicheck API /start endpoint. The connector makes it easy to submit parameters such as document type, signals, and a redirect URL. Results are returned for use in your DaVinci flow.

To start a transaction, click the Intellicheck connector, and then select the **GENERAL** tab. Here are descriptions of the parameters you can provide to the connector:

* **Phone Number**: Required. This field is prepopulated. It is the phone number of your end user (customer or applicant). Prefix the phone number with a plus sign, for example, +1. Do not include separators.
* **Redirect URL**: A redirect can occur at the completion of the capture process. For example, this redirect URL could load your company's webpage into the end user's browser. Use HTTPS in the URL with a fully qualified domain. 
* **Error Redirect URL**: An error redirect can occur if the end user does not complete the capture process, for example, if the end user declines camera access. Another example is if the end user does not complete the capture process in time, as defined by the time-to-live (TTL) parameter. After an error, this URL loads in the browser, redirecting the end user. Use HTTPS in the URL with a fully qualified domain.
* **TTL**: Time-to-live, also known as the timeout value. Values are in minutes. The default is 10 minutes. The maximum is 30 minutes. IMPORTANT: Ensure that this TTL value matches the Poll Interval in the DaVinci polling component, which is part of the templated Intellicheck flow.
* **Document Type**. Required. The three Document Type values (Driver’s License, Passport, and Other) are categories for most federal, state, and international documents used as primary identification. You can select one Document Type per transaction.
  
  * **Driver’s License**: Select this for a North American driver's license, including REAL ID, enhanced ID, learner permit, US military ID, and non-driver state identity card. This can include the United States, Canada, and Mexico identification.
  * **Passport**: Select this for a passport booklet or visa.
  * **Other**: Select this for an international passport card, a trusted traveler card, or a permanent resident card. 
* **Device Validation**: If toggled off (default), no device validation results are returned. If toggled on, device validation results are returned. Device validation includes customer quality checks such as device fingerprint, IP address, and phone validation.
* **Signals**: Required. Signals are the distinct validation checks to be performed. Each signal represents one check. Select one or more signals to customize an identity verification workflow. Signals and document types share some dependencies. You must understand which ones go together. See Document Types and Signals. If you select more than one signal, only certain combinations are allowed. See Multi-Signal Requests for more information.
  
  * **ID Check**: Barcode analysis on North American driver's licenses, including real IDs and extended IDs.
  * **Document Liveness**: Document probability checks for on-screen presentation, printed copy, and portrait substitution.
  * **OCR Scan**: OCR scan on passport books, passport cards, and other forms of identification.
  * **OCR Match**: Compare the OCR scan to the barcode or MRZ data.
  * **Selfie**: Facial matching and liveness.

# Connector Settings

## Configuration Settings 
TBD

# Use cases 
This section includes three common use cases for authenticating a North American driver’s license.

## Use case: Driver’s license barcode analysis 
In this use case, the customer scans the back of a driver’s license. 
* In **Document Type**, select **Driver’s License**
* In **Signals**, select **ID Check**.
  
[Connector GENERAL tab screenshot TBD]

### Results 
Results are provided in the ID Check response for the barcode data.
In the response data, look for the following properties: 
* ID Check ```processResult``` to see if the ID passed (```DocumentProcessOK```) or failed (```DocumentUnknown```). 
 
## Use case: Driver’s license barcode analysis with OCR capture 
In this use case, the customer scans the back of a driver’s license and then takes a picture of the front of the license. 
* In **Document Type**, select **Driver’s License**
* In **Signals**, select **ID Check** and **OCR Scan**.

[Connector GENERAL tab screenshot TBD] 

### Results 
Results are provided in the ID Check response for the barcode data, and in the OCR response for the front-side data. 
In the response data, look for the following properties: 
* ID Check ```processResult``` to see if the ID passed (```DocumentProcessOK```) or failed (```DocumentUnknown```).
* OCR ```documentRecognized``` to see if the front-side passed. 
 
## Use case: Driver’s license barcode analysis with OCR capture and OCR matching 
In this use case, the customer scans the back of a driver’s license and then takes a picture of the front of the license. Intellicheck compares the OCR text from the front of the license to the decoded text from the barcode. 
* In **Document Type**, select **Driver’s License**
* In **Signals**, select **ID Check**, **OCR Scan**, and **OCR Match**.

[Connector GENERAL tab screenshot TBD]

### Results 
Results are provided in the ID Check response for the barcode data, in the OCR response for the front-side data, and in the OCR Match response for the front-back comparison. 
In the response data, look for the following properties: 
* ID Check ```processResult``` to see if the ID passed (```DocumentProcessOK```) or failed (```DocumentUnknown```).
* OCR ```documentRecognized``` to see if the front-side passed.
* OCR Match ```success``` to see if the front matches the barcode. 

# Capabilities 

## Start Transaction Capability
Description: Starts a transaction. For Capture, you begin and end the transaction with a single call to the ```/start``` endpoint.
Functionality: Sends a text message to the end user that includes a link to 

Input Schema
```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "intellicheckRedirectUrl": {
            "type": "string",
            "description": "A redirect can occur at the completion of the capture process. For example, this redirect URL could load your company's webpage to the end user browser. Use HTTPS in the URL with a fully qualified domain."
          },
          "intellicheckErrorRedirectUrl": {
            "type": "string",
            "description": "An error redirect can occur if the end user does not complete the capture process, for example, if the end user declines camera access. Another example is if the end user does not complete the capture process in time, as defined by the ttl property of the private_data object. The default ttl value is 10 minutes. After an error, this URL loads in the browser, redirecting the end user. Use HTTPS in the URL with a fully qualified domain."
          },
          "documentTypeSelection": {
            "type": "string",
            "description": "Identification type. Values: na_dl, passport, other. Select only one. If you specify na_dl, then at a minimum, you must include the idcheck signal. Likewise, if you select passport or other, then at a minimum, you must include the ocr_scan signal. If these minimum signal requirements are not specified in your request body, then they will be used by default."
          },
          "signals": {
            "type": "array",
            "description": "Array of Signals to run for this transaction that is verified against the subscribed list. Possible values include document_liveness_idrnd, idcheck, ocr_match, ocr_scan, and selfie. Leave blank to request all signals to which you are subscribed."
          },
          "ttl": {
            "type": "number",
            "description": "Override of the default minutes to complete. Maximum value is 30."
          },
          "phoneNumber": {
            "type": "string",
            "description": "End user's phone number"
          },
          "deviceValidation": {
            "type": "boolean",
            "description": "If enabled, device fingerprinting and IP address validation fields are returned in the results. If disabled, they are not."
          }
        },
        "required": [
          "phoneNumber",
          "signals"
        ]
      }
    },
    "example": {
      "properties": {
        "intellicheckRedirectUrl": "https://redirect.com",
        "intellicheckErrorRedirectUrl": "https://error.redirect.com",
        "documentTypeSelection": "na_dl",
        "signals": "idcheck",
        "ttl": "15",
        "phoneNumber": "+1xxxxxxxxxx",
        "deviceValidation": true
      }
    }
  }
}
```

Output Schema:
```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      },
      "endpoint": {
        "type": "string",
        "description": "The requested endpiont."
      },
      "version": {
        "type": "string",
        "description": "Version of the API"
      },
      "transaction_id": {
        "type": "string",
        "description": "ID issued at the beginning of a transaction to associate all subsequent processes within the transaction until ended."
      },
      "capture_url": {
        "type": "string",
        "description": "A URL address for the capture session."
      },
      "signals": {
        "type": "array",
        "description": "Confirmed list of signals to run."
      },
      "ttl": {
        "type": "string",
        "description": "Minutes user will have to complete the capture process. Defaults to 10 minutes unless overridden."
      },
      "capture_expiration_utc": {
        "type": "string",
        "description": "A UTC date and time when the transaction expires. Format is mm-dd-yyyy hh:mm:ss. It is calculated based on the current date and time plus the ttl value, which is in minutes."
      },
      "challengeId": {
        "type": "string",
        "description": "Maps to InteractionId, which is a unique identifer per flow execution"
      }
    }
  }
}
```

## Get Result Capability
Description: Polling mechanism for obtaining resultes within 10 minutes of end user completing Capture process.

Input Schema:
```
{
  "default": {
    "type": "object",
    "properties": {
      "properties": {
        "type": "object",
        "properties": {
          "transactionId": {
            "type": "string",
            "description": "ID issued at the beginning of a transaction to associate all subsequent processes within the transaction until ended."
          }
        },
        "required": [
          "transactionId"
        ]
      }
    },
    "example": {
      "properties": {
        "transactionId": "3fb21ac1-eb92-4705-8fcb-40eed01cb369"
      }
    }
  }
}
```

Output Schema:
```
{
  "output": {
    "type": "object",
    "properties": {
      "rawResponse": {
        "type": "object"
      },
      "statusCode": {
        "type": "number"
      },
      "headers": {
        "type": "object"
      },
      "idcheck": {
        "type": "object",
        "description": "Barcode check signal (`idcheck`) response.",
        "properties": {
          "data": {
            "type": "object",
            "description": "Contains the idcheck signal elements returned as a JSON object.",
            "properties": {
              "weightPounds": {
                "type": "string",
                "description": "Contains the weight in pounds as specified on the ID."
              },
              "heightFeetInches": {
                "type": "string",
                "description": "Contains the height in feet and inches for areas that use customary units, for example, 5’2”."
              },
              "age": {
                "type": "integer",
                "description": "Contains the age based on the date of birth and the current system date. The age will be  1 if the age is unknown. The age will be  1 if either no date of birth or a partial date of birth is encoded."
              },
              "driverClass": {
                "type": "string",
                "description": "Contains the driver class codes encoded on the document."
              },
              "address1": {
                "type": "string",
                "description": "Contains line one of the residence address."
              },
              "socialSecurity": {
                "type": "string",
                "description": "This field is intentionally blank."
              },
              "city": {
                "type": "string",
                "description": "Contains the city of residence."
              },
              "processResult": {
                "type": "string",
                "description": "Processing result status code. See [ID Verification processResult Definitions](doc:id-verification-processresult-definitions)"
              },
              "eyeColor": {
                "type": "string",
                "description": "Contains the eye color. If the jurisdiction code for eye color is known, the color’s name is returned, for example, brown, blue, hazel. If the code is not recognized, the code that is encoded on the document is returned."
              },
              "hairColor": {
                "type": "string",
                "description": "Contains the hair color. If the jurisdiction code for hair color is known, the color’s name is returned, for example, brown, black, blonde. If the code is not recognized, the code that is encoded on the document is returned."
              },
              "docCategory": {
                "type": "string",
                "description": "Contains the document category acronym from the barcode. The value is typically one of the following: DL (driver license), HC (health card), ID (identification card), MIL (military identification). Rarely, certain other values are possible: WPN (weapon), HCP (handicap), WV (water vehicle), EMP (employee), OID (other). An empty value means the category is not identifiable."
              },
              "stateIssuerMismatch": {
                "type": "string",
                "description": "Contains a status of whether the address state compared to the document issuer are mismatched. Values are Yes, No, or Unknown. Yes means the state and issuer do not match. No means the state and issuer match. Unknown means the match status is not known."
              },
              "heightCentimeters": {
                "type": "string",
                "description": "Contains the height in centimeters for areas that use metric units."
              },
              "dLIDNumberFormatted": {
                "type": "string",
                "description": "Contains the formatted driver license or ID (DL/ID) value. This will contain the formatting characters, such as spaces and hyphens, as it appears on the printed document."
              },
              "state": {
                "type": "string",
                "description": "Contains the jurisdiction of residence."
              },
              "postalCode": {
                "type": "string",
                "description": "Contains the postal code (zip code) of residence."
              },
              "dateOfBirth": {
                "type": "string",
                "description": "Contains the date of birth in MM/DD/YYYY format. When a partial birth date is encoded on the document, the fields that are unknown will be filled in with ? characters. For example: 01/12/???? will be returned for a document that does not encode the birth date year."
              },
              "isRealID": {
                "type": "string",
                "description": "Contains the document REAL ID status. Values are Yes, No, or empty. Yes means the document was issued in compliance with United States Department of Homeland Security (DHS) requirements for the REAL ID Act passed by Congress in 2005. No means it was not. An empty value means the document did not have enough information to determine a result."
              },
              "testCard": {
                "type": "boolean",
                "description": "True if the document is an Intellicheck test card; false otherwise. Intellicheck can provide test cards that produce different responses for system testing and demonstration."
              },
              "weightKilograms": {
                "type": "string",
                "description": "Contains the weight in kilograms as specified on the ID."
              },
              "uniqueID": {
                "type": "number",
                "description": "Contains a unique ID to identify the document format. All jurisdiction document formats are assigned a unique ID by Intellicheck."
              },
              "restrictions": {
                "type": "string",
                "description": "Contains the restriction codes encoded on the document."
              },
              "dLIDNumberRaw": {
                "type": "string",
                "description": "Contains the raw driver license or ID (DL/ID) value. This will not contain any formatting characters, such as spaces and hyphens. It will contain only the alphanumeric characters that make up the DL/ID."
              },
              "endorsements": {
                "type": "string",
                "description": "Contains the endorsement codes encoded on the document."
              },
              "address2": {
                "type": "string",
                "description": "Contains line two of the residence address."
              },
              "organDonor": {
                "type": "string",
                "description": "Contains Yes or No indicating if the document owner is an organ donor."
              },
              "issueDate": {
                "type": "string",
                "description": "Contains the date of issuance of the document in MM/DD/YYYY format."
              },
              "transactionIdentifier": {
                "type": "string",
                "description": "Contains a transaction ID."
              },
              "gender": {
                "type": "string",
                "description": "Contains the gender. Either Male or Female."
              },
              "isDuplicate": {
                "type": "string",
                "description": "Contains the document duplication status. Values are Yes, No, or empty. An empty value means the duplicate status is unknown."
              },
              "firstName": {
                "type": "string",
                "description": "Contains the first name."
              },
              "middleName": {
                "type": "string",
                "description": "Contains the middle name."
              },
              "issuingJurisdictionAbbrv": {
                "type": "string",
                "description": "Contains the name of the issuing jurisdiction as an abbreviation. This value will always be two letters, for example, NY."
              },
              "expired": {
                "type": "string",
                "description": "Contains the expiration status of the document. Values are Yes, No, or Unknown."
              },
              "docType": {
                "type": "string",
                "description": "Contains the type of document (if available) from the barcode, for example, Driver's License, Learner's Permit, Operator License, and so on. Values vary by issuing jurisdiction. An empty value means the type is not identifiable."
              },
              "expirationDate": {
                "type": "string",
                "description": "Contains the expiration date of the processed document in MM/DD/YYYY format or the word NEVER for documents that do not expire. When a partial expiration date is encoded on the document, the fields that are unknown will be filled in with ? characters. For example, 01/12/???? will be returned for a document that does not encode the expiration year."
              },
              "extendedResultCode": {
                "type": "string",
                "description": "Processing result diagnostic code. Values are Y, U, B, IUX, F, 1, UEE. See [Extended Result Codes](doc:id-verification-processresult-definitions#extended-result-codes)."
              },
              "lastName": {
                "type": "string",
                "description": "Contains the last name with suffix if present."
              },
              "duplicateDate": {
                "type": "string",
                "description": "Contains the date the duplicate document was issued in MM/DD/YYYY format."
              },
              "issuingJurisdictionCvt": {
                "type": "string",
                "description": "Contains the full name of the issuing jurisdiction, for example, New York."
              },
              "mediaType": {
                "type": "string",
                "description": "Contains the media type of the processed document. Examples include MAG and 2D."
              }
            }
          },
          "result": {
            "type": "boolean",
            "description": "True if data was returned in the data object; false otherwise."
          },
          "success": {
            "type": "boolean",
            "description": "True if the API call was successful; false otherwise."
          },
          "message": {
            "type": "string",
            "description": "A description of the result output, for example, \"success\" or an error message."
          }
        }
      },
      "document_liveness": {
        "type": "object",
        "description": "Document liveness signal (document_liveness_idrnd) response",
        "properties": {
          "result": {
            "type": "boolean",
            "description": "True if data was returned in the data object; false otherwise."
          },
          "message": {
            "type": "string",
            "description": "A description of the result output, for example, \"success\" or an error message."
          },
          "imageQualityFindings": {
            "type": "array",
            "description": "Array of image quality detection response codes with messages. Each member contains one code and one message."
          },
          "success": {
            "type": "boolean",
            "description": "True if the API call was successful; false otherwise."
          },
          "data": {
            "type": "object",
            "description": "Contains the document_liveness_idrnd signal elements returned as a JSON object.",
            "properties": {
              "front": {
                "type": "object",
                "description": "Results from the front side of the document. Returns null if the front side of the document was not submitted."
              }
            }
          }
        }
      },
      "ocr_scan": {
        "type": "object",
        "description": "Optical character recognition (OCR) signal (`ocr`) response.",
        "properties": {
          "data": {
            "type": "object",
            "properties": {
              "weightKilograms": {
                "type": "string",
                "description": "Contains the weight in kilograms as specified on the ID."
              },
              "errorMessage": {
                "type": "string",
                "description": "Indicates the cause of failed OCR. Either unable to recognize license or unable to parse data from license."
              },
              "countryCode": {
                "type": "string",
                "description": "Three-letter code of the document issuing country (from third to fifth characters in the first MRZ string)."
              },
              "dlClass": {
                "type": "string",
                "description": "Contains the driver class codes encoded on the document."
              },
              "address": {
                "type": "string",
                "description": "Address printed on the front of the identification or driver license document."
              },
              "documentNumber": {
                "type": "string",
                "description": "Identification number printed on the front of the identification or driver license document."
              },
              "eyeColor": {
                "type": "string",
                "description": "Contains the eye color. If the jurisdiction code for eye color is known, the color’s name is returned, for example, brown, blue, hazel. If the code is not recognized, the code that is encoded on the document is returned."
              },
              "dateOfBirth": {
                "type": "string",
                "description": "Contains the date of birth, typically in yyyy-mm-dd format. When a partial birth date is encoded on the document, the fields that are unknown will be filled in with ? characters. For example: ????-01-12 will be returned for a document that does not encode the birth date year."
              },
              "dateOfBirthFormatted": {
                "type": "string",
                "description": "Contains the date of birth in mm/dd/yyyy format. When a partial birth date is encoded on the document, the fields that are unknown will be filled in with ? characters. For example: 01/12/???? will be returned for a document that does not encode the birth date year."
              },
              "dlRestrictions": {
                "type": "string",
                "description": "Contains the restriction codes encoded on the document."
              },
              "isRealID": {
                "type": "string",
                "description": "Contains the document REAL ID status. Values are Yes, No, or empty. Yes means the document was issued in compliance with United States Department of Homeland Security (DHS) requirements for the REAL ID Act passed by Congress in 2005. No means it was not. An empty value means the document did not have enough information to determine a result."
              },
              "sex": {
                "type": "string",
                "description": "Contains the gender. Either Male or Female."
              },
              "dateOfExpiry": {
                "type": "string",
                "description": "Contains the expiration date of the processed document, typically in yyyy-mm-dd format or the word NEVER for documents that do not expire. When a partial expiration date is encoded on the document, the fields that are unknown will be filled in with ? characters. For example: ????-01-12 will be returned for a document that does not encode the expiration year."
              },
              "fullDocumentImageBase64": {
                "type": "string",
                "description": "Deprecated. Currently not populated. Set /start return_images to true, and then see the images object in get-results."
              },
              "age": {
                "type": "string",
                "description": "Contains the age."
              },
              "lastName": {
                "type": "string",
                "description": "Last name printed on the front of the identification or driver license document."
              },
              "nationality": {
                "type": "string",
                "description": "Contains the nationality of the person. Results depend on the document."
              },
              "height": {
                "type": "string",
                "description": "Contains the height in centimeters."
              },
              "firstName": {
                "type": "string",
                "description": "First name printed on the front of the identification or driver license document."
              },
              "dlEndorsement": {
                "type": "string",
                "description": "Contains the endorsement codes encoded on the document."
              },
              "faceImageBase64": {
                "type": "string",
                "description": "Deprecated. Currently not populated. Set /start return_images to true, and then see the images object in get-results."
              },
              "dateOfExpiryFormatted": {
                "type": "string",
                "description": "Contains the expiration date of the processed document in mm/dd/yyyy format or the word NEVER for documents that do not expire. When a partial expiration date is encoded on the document, the fields that are unknown will be filled in with ? characters. For example: 01/12/???? will be returned for a document that does not encode the expiration year."
              },
              "dateOfIssue": {
                "type": "string",
                "description": "Contains the date of issuance of the document, typically in yyyy-mm-dd format."
              },
              "placeOfBirth": {
                "type": "string",
                "description": "Contains the name of the country or state where the person was born. Results depend on the document."
              },
              "dateOfIssueFormatted": {
                "type": "string",
                "description": "Contains the date of issuance of the document in MM/DD/YYYY format."
              },
              "fullName": {
                "type": "string",
                "description": "fullName is derived from the front of the identification or driver license document. Certain documents, such as a Michigan State driver license, may not return values in the firstName and lastName name fields for OCR results. The API instead returns a fullName field, which can be used to process the name. The fullName field is the entire name. This change is required because the OCR scan cannot separate names as they appear on certain IDs (for example, Michigan issued driver licenses)."
              },
              "documentRecognized": {
                "type": "integer",
                "description": "0 = not recognized. 1 = recognized. 2 = not processed."
              },
              "issuerName": {
                "type": "string",
                "description": "Contains the name of the issuing jurisdiction state, for example, New York."
              }
            }
          },
          "success": {
            "type": "boolean",
            "description": "True if the API call was successful; false otherwise."
          },
          "message": {
            "type": "string",
            "description": "A description of the result output. For example, \"success\" or and error message."
          },
          "result": {
            "type": "boolean",
            "description": "True if data was returned in the data object; false otherwise."
          }
        }
      },
      "ocr_match": {
        "type": "object",
        "description": "OCR mismatch signal (ocr_match) response",
        "properties": {
          "data": {
            "type": "object",
            "description": "Contains the ocr_match signal elements returned as a JSON object.",
            "properties": {
              "addressMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "dlRestrictionsMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "documentNumberMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "isIssueDateMatch": {
                "type": "boolean",
                "description": "True if issue date matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "dlEndorsementMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "dlClassMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "expirationDateMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "nameMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "weightMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "sexMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "isDlClassMatch": {
                "type": "boolean",
                "description": "True if driver license class matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "issuerNameMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "isEyeColorMatch": {
                "type": "boolean",
                "description": "True if eye color matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isDobMatch": {
                "type": "boolean",
                "description": "True if date of birth matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "dobMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "isIssuerNameMatch": {
                "type": "boolean",
                "description": "True if issuer name matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "eyeColorMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "isDlRestrictionsMatch": {
                "type": "boolean",
                "description": "True if driver license restrictions matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isNationalityMatch": {
                "type": "boolean",
                "description": "True if nationality matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isRealIdMatch": {
                "type": "boolean",
                "description": "True if real ID matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "realIdMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "heightMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "isHeightMatch": {
                "type": "boolean",
                "description": "True if height matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isDocumentNumberMatch": {
                "type": "boolean",
                "description": "True if document number matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isWeightMatch": {
                "type": "boolean",
                "description": "True if weight matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isSexMatch": {
                "type": "boolean",
                "description": "True if sex matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "issueDateMatchDetails": {
                "type": "object",
                "description": "Contains `details` to explain the match decision along with a `similarityScore` value and a `similarityThreshold` value.",
                "properties": {
                  "details": {
                    "type": "string",
                    "description": "A brief explanation of whether the comparison was a match, a match with a slight discrepancy, a mismatch, or an indeterminate result."
                  },
                  "similarityScore": {
                    "type": "number",
                    "description": "A confidence estimate between 0 and 100 that OCR data matched the barcode or the MRZ data. A null value means this data was not available for the match comparison."
                  },
                  "similarityThreshold": {
                    "type": "number",
                    "description": "A confidence cutoff that applies to `similarityScore`. For the issuer name, this value is 100 because the issuer must be an exact match. Otherwise, this value is typically 70. The `similarityScore` must be greater than or equal to this `similarityThreshold` to produce a match. The match result determines a true or false value for the corollary object. For example, if this object is `nameMatchDetails`, then its corollary object is `isNameMatch`."
                  }
                }
              },
              "isNameMatch": {
                "type": "boolean",
                "description": "True if name matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isAddressMatch": {
                "type": "boolean",
                "description": "True if address matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isCountryCodeMatch": {
                "type": "boolean",
                "description": "True if country code matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isDlEndorsementMatch": {
                "type": "boolean",
                "description": "True if driver license endorsement matched; false otherwise. A null value means this data was not available for the match comparison."
              },
              "isExpirationDateMatch": {
                "type": "boolean",
                "description": "True if expiration date matched; false otherwise. A null value means this data was not available for the match comparison."
              }
            }
          },
          "success": {
            "type": "boolean",
            "description": "True if the API call was successful; false otherwise."
          },
          "message": {
            "type": "string",
            "description": "A description of the result output, for example, \"success\" or an error message."
          },
          "result": {
            "type": "boolean",
            "description": "True if data was returned in the data object; false otherwise."
          }
        }
      },
      "selfie": {
        "type": "object",
        "description": "Facial matching and liveness detection signal (`facial`) response.",
        "properties": {
          "data": {
            "type": "object",
            "description": "Contains the facial signal elements returned as a JSON object.",
            "properties": {
              "photoFace": {
                "type": "string",
                "description": "Deprecated. Refer to [Submitted Images Response](doc:submitted-images-response). Selfie image in base64 format. This is optional and will only be returned if you subscribe to return of selfie image."
              },
              "errorMessage": {
                "type": "string",
                "description": "Indicates the cause of failed liveness detection. Either unable to recognize license or unable to parse data from license."
              },
              "livenessProbability": {
                "type": "number",
                "description": "Likelihood the image is a live person. Value is rounded to two decimal places."
              },
              "matchProbability": {
                "type": "number",
                "description": "Likelihood is selfie matches the document facial image. Value is rounded to two decimal places."
              },
              "matchScore": {
                "type": "number",
                "description": "Numeric representation of the degree to which the selfie matches the document facial image. Based on the comparison between the current facial image (selfie) and the document facial image. Value is rounded to two decimal places."
              },
              "matched": {
                "type": "boolean",
                "description": "Indicates if the current facial image is matched with the document facial image."
              },
              "livenessScore": {
                "type": "number",
                "description": "Numeric representation of the degree to which the selfie image is that of a live person based on livenessProbability. Value is rounded to two decimal places."
              },
              "isLive": {
                "type": "boolean",
                "description": "Whether image is a live person."
              }
            }
          },
          "success": {
            "type": "boolean",
            "description": "True if the API call was successful; false otherwise."
          },
          "result": {
            "type": "boolean",
            "description": "True if data was returned in the data object; false otherwise."
          },
          "message": {
            "type": "string",
            "description": "A description of the result output, for example, \"success\" or an error message."
          }
        }
      },
      "ipqs": {
        "type": "object",
        "description": "Returns device fingerprinting and IP address validation fields if Device Validation field is toggled ON in Start Transaction capability",
        "properties": {
          "addressDetails": {
            "type": "object",
            "description": "JSON object containing address details"
          },
          "fraudDetails": {
            "type": "object",
            "description": "JSON object containing fraud details"
          },
          "phoneDetails": {
            "type": "object",
            "description": "JSON object containing phone details"
          }
        }
      }
    }
  }
}
```

## Webhook Capability

There is no configuration for this capability, however, you will need to download the standard [DaVinci flow](https://support.pingidentity.com/s/marketplace-integration/a7iUJ0000002AEbYAM/intellicheck-flow-snippet) here (Select "Download Integration" on this listing and import it into your DaVinci environment). This flow MUST be used with the Intellicheck connector as it handles the polling and Challenge components for the webhook.
