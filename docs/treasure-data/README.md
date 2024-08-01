# Treasure Data Connector


Author: Ryan Schafer


# Introduction

Treasure Data was built to radically simplify customer data management and help brands use all of their customer data to improve campaign performance, achieve operational efficiency, and drive business value with connected customer experiences.

Customer Data Cloud, Treasure Data’s award-winning suite of customer data platform solutions, integrates customer data, connects identities in unified customer profiles, applies privacy, and makes insights and predictions available for Marketing, Service, Sales, and Operations to drive personalized engagement and improve customer acquisition, sales, and retention. The flexible, scalable, and secure platform has a comprehensive connector network that evolves with your existing technology stack to future-proof all customer data initiatives.


# Setup

## Requirements

To use the connector, you'll need:

* Treasure Data tenant access to generate API key and Region
* DaVinci tenant access

## Setting up the connector

In DaVinci, add a Treasure Data connection. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings

The connector has a simple set up regarding the general configuration. After you have added the connector to your library and dropped it onto your flow canvas, click into the connector and select the gear icon next to the connectors name. Paste the API Key into the “API Key” field and select “Apply”.


# Using the connector in a flow

You can use the connector in a variety of use cases, such as:


## Insert a record in Treasure Data

Treasure Data provides an ingest API that allows you to programmatically import rows into existing tables in a TD database. The endpoints you can use for the data ingestion API are
* US Region: https://us01.records.in.treasuredata.com
* EU01 Region:  https://eu01.records.in.treasuredata.com
* Tokyo Region: https://ap01.records.in.treasuredata.com
* Korea Region: https://ap02.records.in.treasuredata.com
* AP03 Region: https://ap03.records.in.treasuredata.com

Choose the endpoint that corresponds to your region.

To make the ingest API call, you need the following data:
* the name of the database that contains the table you want to ingest records into
* the name of the table
* a request object that contains the column names and values you want to import. The information in the request object is specified as key-value pairs in JSON, and each entry in the request object will be entered as a new row in the table. Figure 1 below shows the format for ingesting a single record, and Figure 2 shows the format for ingesting multiple records in a single request.

As you create request objects, be aware of the following API behaviors: 
* The records ingested do not need to match the current table schema; new columns will be added to the table schema on ingest.
* If you specify a time column, the value must be formatted as Unix timestamp in UTC seconds (not milliseconds). If you do not specify a time column, the system will use the current time.
* The API assigns a UUID to each record which is used in the ingest pipeline. This UUID is included in the response object; however, it is not persisted in the table. Consequently, avoid specifying a column named "uuid." The API allows you to specify a value for a "uuid" column if the value is syntactically valid, and it will be returned in the response, but the value will not be stored in the table.



## Token Management

The Profiles API Token enables your ability to increase personalized content based on detailed customer information. This REST API returns customer data in real-time and updates your segment information. The ability to create a Profiles API token is based on your folder permissions.

You can also use Profiles API Token to personalize your customers' experience on your website. You can combine Treasure Data’s personalization feature with A/B Testing tools such as Adobe Target, Optimizely, or Google Optimize, to determine the version of your website that yields results.

When the underlying personalization workflow completes, the personalization data set is refreshed. You can see a current list of the segments to which a specific profile belongs. You can also see a list of attributes associated with the specific profile.

The parent segment must already exist. The parent segment is the basis for all data accessed by Profiles API Tokens.

The use of the Profiles API Token with your tools requires the use of the Treasure Data JavaScript SDK and support or services consultation.


# Capabilities

**Insert a Record**: Insert a single record with the ingestion API. Fields captured are listed below:
  * Region: Select the appropriate region. This is used to define the base URL
  * Database: Database from your Treasure Data account
  * Table: Table from your Treasure Data account
  * Key / Value list: Used to capture specific user attributes for the record

**Create Profiles API Token**: Create a Profiles API token
* Region: Select the appropriate region. This is used to define the base URL
* Token ID: Token to update
* Type: Value = ‘token’
* Attributes: Properly formatted JSON to capture user Attributes
* Relationships: Properly formatted JSON to capture Relationships

**Retrieve List of Profile API Tokens**: Retrieve List of Profile API Tokens associated with a parent segment ID
* Region: Select the appropriate region. This is used to define the base URL
* Audience ID: Master segment ID of the token

**Update Profiles API Token**: Update a profiles API Token
* Token ID: Token to update
* Type: Value = ‘token’
* Attributes: Properly formatted JSON to capture user Attributes
* Relationships: Properly formatted JSON to capture Relationships

**Delete Profiles API Token**: Delete the specified Profiles API token
* Token ID: Token to update

**Make Custom API Call**: Define a custom API call to Treasure Data
* Endpoint: Add the full API URL
* Method: Define the method for the API call (GET, PUT, POST, etc.)
* Query Parameters: Define any query parameters for the API call
* Headers: Define any headers for the API call
* HTTP Body (JSON): Define the the properly formatted JSON body for the API call

# Troubleshooting resources

For information and setup help, see the following sections of the Treasure Data documentation:

* [Tokens API](https://api-docs.treasuredata.com/pages/audience_api_v1/tag/Tokens/)
* [Insert a Record](https://docs.treasuredata.com/articles/#!pd/Importing-Table-Records-Using-the-Data-Ingestion-API?_gl=1*6icwb3*_ga*NjQwMjgxMjE5LjE3MTQ3NTYzMzA.*_ga_6E2G020VBJ*MTcxNjU3MzAzMS4xMS4xLjE3MTY1NzM3MTQuMTAuMC4w&_gl=1*6icwb3*_ga*NjQwMjgxMjE5LjE3MTQ3NTYzMzA.*_ga_6E2G020VBJ*MTcxNjU3MzAzMS4xMS4xLjE3MTY1NzM3MTQuMTAuMC4w)
