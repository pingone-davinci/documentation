
# Amazon DynamoDB Connector
  


Author: Scott Banducci (scottbanducci@pingidentity.com)


# Introduction

Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. The Amazon DynamoDB Connector enables you to:

1. Create a Table
2. Put Item in a Table (STRING ATTRIBUTES ONLY. Putting item with non-string attributes is pending an update to this connector)
3. Read Item
4. Update Item
5. Delete Item
6. Query Table
# Setup


## Resources

For information and setup help, see the following sections of the Amazon documentation:

* [Amazon DynamoDB SDK Guide](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GettingStarted.html " Overview page for Amazon DynamoDB SDK")

* [Amazon DynamoDB Client - SDK Reference](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-dynamodb/globals.html"Documentation for all calls to SDK and outputs")


## Requirements


To use the connector, you'll need:

* An Amazon DynamoDB Account
* Your DynamoDB Account 'Access ID' and 'Secret Access Key'
	* these can be found by clicking the account username (in the top right of your DynamoDB homepage) -> Security Credentials -> Access Keys
* The 'AWS Region' you are going to be using

## Setting up the connector

  

In Davinci, add a **Amazon DynamoDB** connection via the "Connections" tab. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings
  

Once you've added the connection click on its logo, or click the "**·****·****·**"  button and "Edit".

You will see the connector's details pop-up. On the GENERAL tab, enter in your

1) AWS Access Key
2) AWS Secret Access Key
3) AWS Region

and click apply. This ensures that whenever you use this connector in a flow you will not have to reenter enter this information.


# Using the connector in a flow


The Amazon DynamoDB connector allows you to **Create a Table** ,  **Put (limited to String Only Attributes), Read(Get), Update and Delete an item in a Table** and **Query a Table**.

First, add the Amazon DynamoDB connector via the "Connections" tab (remember to setup your Access tokens and AWS region). In the DaVinci Flow Studio add an Amazon DynamoDB connector. Then choose the capability you'd like to use it for. You will then need to select the parameters from previous nodes in the flow (ex. an HTML form) to populate the fields.


## Create a Table

Simply add the node to your flow and select the Create a Table capability.  You must enter a Table Name. 

Next add the **Attribute Name and Type** fields for your table. These will be your tables attributes. Each **Key** will be an Attribute Name and the corresponding **Value** will be the Type (ex. **Key**: Name, **Value**: S).

Finally, add the **Attribute Name and Key Type** fields for your primary key and sort keys. Put the **Attribute Name** in the **Key** field and the corresponding **Key Type** in the **Value** field (ex. **KEY**: Name, **Value**: HASH).
  

## Put Item in a Table (String Attribute Items ONLY)

**NOTE:** This connector **requires** that all the Attribute Types be String. In a future update expect enablement of multi-typed Attributes for the PutItem capability.

To put an item into a table add the Amazon DynamoDB connector to your flow, choose the **Put Item into Table (String Value Attributes ONLY)** capability and input the **Table Name**. Next select your marhsall and unmarshall options using the **toggle switches** provided. Finally, put the **Key/Attribute Name** in the **Key** field and the corresponding **Initial Value** in the **Value** field (ex. **KEY**: Name, **Value**: John Smith).

## Read Item from Table

To put an item into a table add the Amazon DynamoDB connector to your flow, choose the **Read Item from Table** capability and input the **Table Name**. 

Next select your marhsall and unmarshall options using the **toggle switches** provided.

Finally, create a JSON object in the **Key object** code field. **NOTE: This includes the ENTIRE key schema; Primary and Sort Keys.** 

EXAMPLE: 
{
"Name":  "Phil",   //primary key
"Phone":  "123"   //sort key
}

## Update an Item
  

To Update an item into a table add the Amazon DynamoDB connector to your flow, choose the **Update an Item** capability and input the **Table Name**. 

Next select your marhsall and unmarshall options using the **toggle switches** provided.

Create a JSON object in the **Key object** code field. **NOTE: This includes the ENTIRE key schema; Primary and Sort Keys.** (see example above in Read Item from Table)

Next, add JSON objects fro any substitutions for Attribute Names or Attribute Values using the **Expression Attribute Names** and  **Expression Attribute Values** code fields. 

Example for  **Expression Attribute Names**:
{"#n":  "Name","#e":"Phone"}

Example for  **Expression Attribute Values**:
{":n":  "Scott",":e":"555"}

Finally, use the **Update Expression Clause** field to update the desired fields. Do not use any quotation marks. (ex.  **set #c = :c** ).

## Delete Item
  

To Delete an item into a table add the Amazon DynamoDB connector to your flow, choose the **Delete Item** capability and input the **Table Name**. 

Create a JSON object in the **Key object** code field for the Item you wish to Delete. **NOTE: This includes the ENTIRE key schema; Primary and Sort Keys.** (see example above in Read Item from Table)

## Query a Table  

To query a table add the Amazon DynamoDB connector to your flow, choose the **Query a Table** capability and input the **Table Name**. 

Next select your marhsall and unmarshall options using the **toggle switches** provided.

You may enter an **Index Name**, **Filter Expression**, **Projection Expression** and **Limit** if required. See [Query documentation](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-dynamodb/modules/queryinput.html "Documentation for Query's inputs") for details.

Next, add JSON objects fro any substitutions for Attribute Names or Attribute Values using the **Expression Attribute Names** and  **Expression Attribute Values** code fields. 

Example for  **Expression Attribute Names**:
{"#n":  "Name","#e":"Phone"}

Example for  **Expression Attribute Values**:
{":n":  "Scott",":e":"555"}

Finally, use the **Key Condition Expression** field to query the desired fields. Do not use any quotation marks. (ex.  **#n = :n and #e = :e** ).


# Capabilities

### Put Item (putItem)


Writes an Item into a DynamoDB Table

#### Table Name `textField`


The name of the Table.

#### Items Key/Value List `keyValueList`


A key-value list of the Attribute-Value pairs of the item. NOTE: All values must be strings.

#### Items (JSON format) `codeEditor`


A code field to enter JSON object. 

---

### Get Item (getItem)


Gets an Item from a DynamoDB Table

#### Table Name `textField`


The name of the Table.

#### Key of Item `keyValueList`


A key-value list of the Attribute-Value pairs of the item. NOTE: All values must be strings.

#### Key of Item (JSON format) `codeEditor`


A code field to enter JSON object. 

---

### Delete Item (deleteItem)


Deletes an Item in a DynamoDB table.

#### Table Name `textField`


The name of the Table.

#### Key of Item `keyValueList`


A key-value list of the Attribute-Value pairs of the item. NOTE: All values must be strings.

#### Key of Item (JSON format) `codeEditor`


A code field to enter JSON object. 

---

### Scan a Table (scanTable)


Scans a DynamoDB table.

#### Table Name `textField`


The name of the Table.

#### Filter Expression `textArea`


Conditions applied after a Query but before the data is returned. (See connector documentation for further info on FilterExpression).

#### Expression Attribute Values `codeEditor`


One or more values that can be substituted in an expression.

---

### Query a Table (queryTable)


Queries a DynamoDB table.

#### Table Name `textField`


The name of the Table.

#### Key Condition Expression `textField`


The condition that specifies the key values for items to be retrieved by the Query action.

#### Expression Attribute Values `codeEditor`


One or more values that can be substituted in an expression.

---

### Make Custom S3 SDK Call (makeCustomSDKCall)


Make your own SDK call by passing an S3 SDK command and parameters.

#### SDK Custom Call Command Name `textField`


The name of the SDK command you want to call (ex. getObject, createBucket)

#### SDK Custom Call Parameters `keyValueList`


A key value list that will create a JSON object that will be passed as the arguments for your custom command

---


  

# Troubleshooting

**Create a Table:**  
NOTE: Key fields for **List of Attribute Name and Key Type** must have a corresponding Key field in **List of Attribute Name and Type**. 

**Put Item into Table (String Value Attributes ONLY):**
NOTE:  This capability is intended to be expanded upon in a future update to allow Put Item commands for Items with any type of Attributes (such as Number, List, etc.). Currently, all Attributes (which will have the Attribute Name entered in the **Key** field) must be of type String. 

**Read Item from Table:**
NOTE: A JSON object should be entered into the **Key object** code field. This means you should include { } at start and end. 
NOTE: Your **Key object** should contain all Primary and Sorting keys.

**Update an Item:**
NOTE:  **Read Item from Table** troubleshooting NOTEs apply here as well.
NOTE: **Expression Attribute Names** and **Expression Attribute Values** code fields should include { } at start and end. 
NOTE: **Update Expression Clause** should have no quotation marks ( neither " nor ' ).

**Delete Item:**
NOTE: A JSON object should be entered into the **Key object** code field. This means you should include { } at start and end. 

**Query a Table:**
NOTE: A JSON object should be entered into the **Key object** code field. This means you should include { } at start and end. 
NOTE: **Expression Attribute Names** and **Expression Attribute Values** code fields should include { } at start and end. 
NOTE: Technically only **Table Name** is required but it is HIGHLY RECOMMENDED you include a **Key Condition Expression** such as: **#n = :n and #e = :e**. DO NOT INCLUDE QUOTATIONS.

# Limitations

* This connector has limited capabilities compared to the full extent of the Amazon DynamoDB SDK. Most Notably, this connector does not allow Put commands for items that have non-string attributes. This functionality is intended to be added at a future date. If you'd like to see more capabilities added or have other suggestions, please let your Ping contact know.
