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

# Connector settings, schema, and mappings 

## Settings 
TBD

## Schema 
TBD

## Mappings 
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
