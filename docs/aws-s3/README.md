# Amazon S3 Connector
  

Author: Scott Banducci (scottbanducci@pingidentity.com)


# Introduction

Amazon S3 or Amazon Simple Storage Service is a service offered by Amazon Web Services that provides object storage through a web service interface. Amazon S3 uses the same scalable storage infrastructure that Amazon.com uses to run its e-commerce network. The Amazon S3 Connector enables you to:

1. Create a Bucket
2. Delete a Bucket
3. Store Object
4. Get an Object from a Bucket
5. Delete an Object

# Setup


## Resources

For information and setup help, see the following sections of the Amazon documentation:

* [Amazon S3 API Reference](https://docs.aws.amazon.com/AmazonS3/latest/API/Welcome.html "API Overview page, this connector uses the SDK but this still might be useful")

* [Amazon SDK documentation](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/S3.html"S3 Javascript SDK documentation; good for request parameters and response syntax")


## Requirements


To use the connector, you'll need:

* An Amazon S3 Account
* Your S3 Account 'Access ID' and 'Secret Access Key'
	* these can be found by clicking the account username (in the top right of your S3 homepage) -> Security Credentials -> Access Keys
* The 'AWS Region' you are going to be using

## Setting up the connector

  

In Davinci, add a **Amazon S3** connection via the "Connections" tab. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings
  

Once you've added the connection click on its logo, or click the "**·****·****·**"  button and "Edit".

You will see the connector's details pop-up. On the GENERAL tab, enter in your

1) AWS Access Key
2) AWS Secret Access Key
3) AWS Region
and click apply. This ensures that whenever you use this connector in a flow you will not have to reenter enter this information.


# Using the connector in a flow


The Amazon S3 connector allows you to **Create** and **Delete Buckets**. Also to **Store(Put), Get and Delete an object from a bucket**.

First, add the Amazon S3 connector via the "Connections" tab (remember to setup your Access tokens and AWS region). In the Davinci Flow Studio add an Amazon S3 connector. Then choose the capability you'd like to use it for. You will then need to select the parameters from previous nodes in the flow (ex. an HTML form) to populate the fields.


## Creating/Deleting a Bucket

Simply add the node to your flow and select the Create Bucket or Delete Bucket capability.  The only required field for this capability is the Bucket Name you wish to create or delete. You can use an HTML form or other input method (ex. a Get request that outputs the Bucket Name) earlier in the flow and click the node's "{}" parameters button to use that input as the Bucket Name. 
  

## Store Object (putObject)
If you'd like to store an object to an Amazon S3 bucket, it must first be uploaded in your flow. 

**NOTE:** S3 **requires** that all the object be in a buffer, file stream or similar binary form (see documentation) for any putObject call. **This connector assumes that any Object uploaded into the flow is Base64 encoded when it is passed to Davinci's Amazon S3 connector. If you do not use the method below you must make your own Make Rest API capability found in the HTTP connector for an upload and make sure you pass the connector a Base64 encoded object.**

Preferred method of file upload: you can use the Davinci HTTP connector -> "Custom HTML Template" capability. In the "HTML Template" field, you must use a form tag <form id = "inputForm> < /form>. Within this tag, you must use the "{}" parameters button and click "SK-Component" -> "skinputfile" to allow the user to upload their file. In "Output Fields List" add a field with a "Property Name" matching the skinputfile's ID (click it to reveal). You should also add an SK-> "skbutton" inside your form. Click this and set Event->Button Type to "Form Submit". The upload will make the object available later and the button will push your flow onto the next node.

Use :
* an existing Bucket name, 
* a new and unique Key, 
* the object previously uploaded using "skinputfile" technique above when using

Your object will be stored in the given Bucket with the given Key.    

## Get Object

Simply pass the connector:
* the Bucket name 
* and Key 

of the object you are trying to retrieve and it will be returned in the response's Body which is accessible later in the flow via the "objectData" output in the Amazon S3 'Get Object' node. The object will be downloaded as a file without any extension. 

## Delete Object
  

Simply pass the Amazon S3 'Delete Object' node the Bucket name, Key, and (optional)Version ID of the object you want to delete. The response will come back with code 204 and No Content.

# Capabilities
  

# Troubleshooting

  

NOTE: dealing with the putObject upload restrictions can be difficult. It is highly recommended you use the technique described above.

NOTE: putObject will return  Data: {ETag: "###########################"}. This ETag number can be used to locate your object.

NOTE: Delete Bucket and Delete Object will return empty, status 204 responses.

# Limitations

* This connector has limited capabilities compared to the full extent of the Amazon S3 SDK. If you'd like to see more capabilities added or have other suggestions, please let your Ping contact know.
