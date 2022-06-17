# Shopify Connector


## Doc draft

Author: Scott Banducci (scottbanducci@pingidentity.com)


# Introduction

Shopify is an e-commerce platform for online stores. The Shopify platform offers online retailers a suite of services including payments, marketing, shipping and customer engagement tools. The Shopify Connector for Davinci allows you to:

1. Create a customer
2. Read a customer
3. Update a customer
4. Delete a customer
5. List customers (with some filters)

# Setup


## Resources

For information and setup help, see the following sections of the Shopify documentation:

* Shopify
	* [Create,  Read, Update, List customer(s)](https://shopify.dev/api/admin-rest/2022-04/resources/customer#post-customers "Shopify docs")
	* [Delete customer](https://shopify.dev/api/admin-graphql/2022-04/mutations/customerDelete "Shopify doc")

## Requirements

To use the connector, you'll need:



* A Shopify store
* Your store's [Access Token](https://www.shopify.ca/partners/blog/17056443-how-to-generate-a-shopify-api-token "Shopify doc")
* An API Version Number (as of June 15, 2022 we recommend "2022-04")
	* [Shopify versioning documentation](https://shopify.dev/api/usage/versioning "Shopify doc")
* Your Shopify store name (as appears in your {{storename}}.myshopify.com domain)
	* [Shopify Domains documentation](https://help.shopify.com/en/manual/domains "Shopify doc")



## Setting up the connector

In Davinci, add a **Shopify** connection via the "Connections" tab in your Davinci Environment. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


### Connector settings

[List and explain the connector settings that appear when the connection is opened from the **Connections** page. If you did not cover it earlier in the **Setup** section, tell the user how to complete each configuration field or where to get the information they need.

These typically on the **General** tab, but some connectors have a different name or multiple configuration tabs. Don't document **Capabilities**, or **In Flows**.]

Once you've added the connection click on it's logo, or click the "**·****·****·**"  button and edit. 
You will see the connector's details pop-up. On the GENERAL tab, enter in your 
1) API Version number 
2) Store Name
3) Access Token

and click apply. This ensures that whenever you use this connector you will not have to reenter enter this information.

# Using the connector in a flow

The Shopify connector allows you to create, read, modify, list and delete customers in your Shopify store as part of your flow. 

In the flow studio add a Shopify connector. Then choose the capability you'd like to use it for (create, read, update, delete, list). You will then need to select the parameters you need from previous nodes in the flow (ex. an HTML form) to populate the fields. 

## Creating a customer on your Shopify store

If your business also sells branded merchandise via a Shopify store, you can enable your customers to make a purchase without the hassle of signing up to your Shopify store and entering information they've already provided to you. 


## Changing customer details

If a customer of yours changes their address or deletes their account, you can use a Davinci flow and the Shopify connector to automatically cascade those changes to your Shopify store.


## Generate a list of customers

Lastly, should you wish to extract customer information you can use the connector to retrieve a list of customer objects (in JSON) from Shopify to use as you see fit.

Current list filters available via connector:

* Created Before / Created After
 * Updated Before / Updated After
 * Limit (#of results returned, max 250)

Filters NOT available via connector yet can be added as parameters to a GET HTTP request for a list of customers can be found [here](https://shopify.dev/api/admin-rest/2022-04/resources/customer#get-customers "Shopify doc").


# Capabilities

Leave this section blank: it will be generated automatically


# Troubleshooting

Note that the Shopify API call will respond with either:

1)  "customer" object (create, read, update),
2)  "customers" object (list), 
3) "customerDelete" object (delete)

See previously linked Shopify Documentation for details on these objects.



### Testing capabilities

You can test each capability individually. For help, see [Testing capabilities](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).


# Limitations

* filtering parameters for the List Customers capability on this connector is not exhaustive compared to what the Shopify's API allows
* Unable to create, delete, update **batches** of customers
