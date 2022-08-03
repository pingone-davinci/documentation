# AWS Lambda Connector

## Doc draft

Author:

# Introduction

AWS Lambda connector can be used to invoke a Lambda function from Ping Connector. This connector allows you to:

1. Invoking a Lambda function from Ping Connector

# Setup

## Resources

For information and setup help, see the following sections of the AWS Lambda connector API documentation:

- [Invoke a Lambda function](https://docs.aws.amazon.com/lambda/latest/dg/API_Reference.html)

## Requirements

To use the connector, you'll need:

1. Access Key
2. Secret Key
3. AWS Region

## Setting up the connector

In Davinci, add a **AWS Lambda Flow** connection via the "Connections" tab in your Davinci Environment. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector Settings

Once you've added the AWS Lambda Flow connection click on it's logo, or click the "···" button and edit. You will see the connector's details pop-up. On the GENERAL tab, enter the Lambda function name

1. Lambda function name

and click apply. This ensures that whenever you use this connector you will not have to reenter this information is used for generated Token passed as input to Authorise below connector in flow.

# Using the connector in a flow

## Invoking a Lambda function

To invoke a Lambda function add a **AWS Lambda** Connector in the flow studio. Then choose the **AWS Lambda** capability. Provide the parameters from previous nodes in the flow (HTML form) to invoke a Lambda function.

![Invoke a Lambda function](../assets/InvokeLambda.PNG)

# Capabilities

### AWS Lambda Invocation (AWSLambdaInvocation)


Capability to Invoke AWS Lambda

#### Lambda Function Name `textField`


AWS Lambda Function Name to Invoke

---


# Limitations

Use of connector is limited to function name of AWS Lambda API and account access.
