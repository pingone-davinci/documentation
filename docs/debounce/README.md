
  
# DeBounce Connector
  


Author: Scott Banducci (scottbanducci@pingidentity.com)


# Introduction

For applications that are in need of real-time email address verification (such as account registration workflows), our real-time lookup API is the perfect tool for the job. It consists of a single endpoint, and its utilization in a production application requires very little effort or resources.

1. Single Validation
2. Bulk Validation
3. Bulk Validation Status
4. Account Balance
5. API Usage History
# Setup


## Resources

For information and setup help, see the following sections of the DeBounce documentation:

* [DeBounce API Documentation](https://developers.debounce.io/reference/overview "Overview page for DeBounce API")

## Requirements


To use the connector, you'll need:

* A DeBounce Account
* Your DeBounce Account 'API Key'
* If you need to create an API key, please log in to your DeBounce account and then navigate to the [API section](https://app.debounce.io/api). 

## Setting up the connector

  

In Davinci, add a **DeBounce** connection via the "Connections" tab. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings
  

Once you've added the connection click on its logo, or click the "**·****·****·**"  button and "Edit".

You will see the connector's details pop-up. On the GENERAL tab, enter in your

1) API Key

and click apply. This ensures that whenever you use this connector in a flow you will not have to reenter enter this information.


# Using the connector in a flow


The DeBounce connector allows you to **Single Validation** ,  **Bulk Validation**, **Bulk Validation Status**, **Account Balance**, **API Usage History**  and **Disposable Email Detector**.

First, add the DeBounce connector via the "Connections" tab (remember to setup your API Key). In the DaVinci Flow Studio add a DeBounce connector. Then choose the capability you'd like to use it for. You will then need to select the parameters from previous nodes in the flow (ex. an HTML form) to populate the fields.


## Single Validation
Simply add the node to your flow and select the Single Validation capability.  You must enter a parameter from a previous node or variable in order to populate the email field. 

NOTE: there's 3 True/False toggle switches that correspond to options in the "Single Validation" API. See documentation for details on what these do but they are not necessary to validate emails.

Single Validation Documentation:
https://developers.debounce.io/reference/single-validation  

## Bulk Validation

(You must provide a URL to a .txt or .csv file containing the emails you'd like to validate. For proper formatting of these files see this link:  https://help.debounce.io/kb/acceptable-files/supported-file-types/ )

Add a DeBounce node and select the Bulk Validation capability. Enter the list's URL or the parameter containing the URL as the "list URL".

Upon success you will receive a success response with a "list_id" field. This is important because this list_id must be used to check the validation status. More importantly it is necessary to download the results of your bulk validation upload.

Bulk Validation Documentation:
https://developers.debounce.io/reference/upload
## Bulk Validation Status
If you'd like to use the API to check the Validation Status and see if your bulk validation upload is ready for download, you can use this capability.

Add a Bulk Validation Status node and enter the "list_id" of the email list you'd like to get an update on. Otherwise use a parameter to populate this field.

Bulk Validation Status Documentation:
https://developers.debounce.io/reference/status

## Account Balance  

Use this capability to check and return the number of credits your DeBounce account has. No parameters are necessary, just your API Key (as is used for every capability for the DeBounce connector).

Account Balance Documentation:
https://developers.debounce.io/reference/account-balance

## API Usage History  

Use this capability to check API usage in a date range. Dates are from "Start Date" to "End Date" (inclusive of both).

Dates must be in the format: "YY-MM-DD". 

A successful response will include the number of calls to your DeBounce account's API.

API Usage History Documentation:
https://developers.debounce.io/reference/api-usage-history

## Disposable Email Detector  

This is an API capability which DeBounce provides free of charge (i.e. it doesn't use up your credits, however it is restricted to a reasonable number of calls per day).

This capability will return true if it's a disposable email, false otherwise.

Disposable Email Detector Documentation:
https://developers.debounce.io/reference/disposable-email-detector

# Capabilities

### Single Validation


Validates a single email.

#### Email `textField`

The email to check.
#### Photo `toggle`


If you require a profile photo along with the validation results, set it true.

#### Append `toggle`


To find the full name and avatar of an email owner, you must set this true.

#### GSuite `toggle`

If you require to detect the validity of G Suite Accept-all emails, set it true.

---

### Bulk Validation

Validate a .txt or .csv list located at the URL you provide. You will receive a list_id parameter back which you must use to check results.

####  URL for email list `textField`

The URL where the file is located. 


---

### Bulk Validation Status

Returns the status of a bulk email validation process. 

#### List ID `textField`


The "list_id" that DeBounce provided to you upon successfully using the Bulk Validation capability. 

---

### Account Balance

Returns the credits your DeBounce has remaining.

---

### API Usage History

Responds with the number of API calls within the given date range.

#### start date `textField`

The start date (inclusive) with the format: YY-MM-DD.


#### start date `textField`


The end date (inclusive) with the format: YY-MM-DD.


---

### Disposable Email Detector

Check if the given email is a "disposable" email.

#### Email `textField`


The email you're checking if disposable or not. 

---


  

# Troubleshooting

**Bulk Validation**  
NOTE: Your list must have a very specific format. See this link for details: https://help.debounce.io/kb/acceptable-files/supported-file-types/
NOTE: You will have to download results via your DeBounce admin portal. 


# Limitations

* This connector (and service) is easy to use and light weight. Most used will likely be Single Validation in web flows for single email validate (ex. during signup flows). If you use Bulk Validation remember that you must record the list_id and download your results separately through your DeBounce admin portal. 
