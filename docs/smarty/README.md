## Smarty Address Validator

Author: Ryan Schafer


# Introduction

The Smarty Address Validator is used to validate both US and International Addresses.


# Setup
To set up the Smarty connector, you will need access to a Smarty tenant. Please reference the below documentation 


## Resources

For information and setup help, see the following sections of the Smarty documentation:
- US Address Cloud API Documentation: https://www.smarty.com/docs/cloud/us-street-api
- International Address Cloud API Documentation: https://www.smarty.com/docs/cloud/international-street-api

## Requirements

To use the connector, you'll need:

Access to a Smarty tenant to grab the below:
* Auth ID
* Auth Token
* License


## Setting up Smarty Tenant

1. Go to https://www.smarty.com/ and register for an account if you do not already have one
2. Locate the Auth ID and Auth Token on the "Api Keys" tab and the License on the "Subscriptions" tab

## Setting up the Connector in DaVinci

1. In your DaVinci tenant, navigate to the the Connections tab and select "New Connection". Search for the **Smarty Address Validator** connection and click "+" to add the connector to your library
2. On the connections tab, select the newly added connector. A configuration pane will appear where you will need to enter the Auth ID, Auth Token and License from your Smarty tenant
3. With the **Smarty Address Validator** connector added to your library and configured, you can now add it to a flow in the "Flow Studio" tab. In the flow, click the black "+" in the bottom left hand corner and search for the connector to add it to the canvas
4. Once on the canvas, add it to the flow where you would like to validate an address. Click on the node for the connector, and chose either "Verify Single US Address" or "Verify Single International Address" for the capability
5. Most likely this connector will be used with user input values. Select the "{}" button on the "General" tab when setting up the connector in the flow. Select which connector in the corresponding dropdown where the user will be entering their address, and then choose the input field from the "output" dropdown. Repeat for all address fields on the Smarty connector node
6. Apply your changes then Save and Deply the flow

# Using the connector in a flow

You can use the connector in a couple of use cases:
1. Verify a single US Address
2. Verify a single International Address

# Capabilities

### Verify Single US Address (getSingleAddress)


Verifies a single US address - requires Street, City, State

#### Street `textField`


Street value (EX: 123 Main Street, Unit A)

#### City `textField`


City value (EX: New York)

#### State `textField`


State value (EX: NY)

#### Candidates `textField`


The maximum number of addresses returned when the input is ambiguous (EX: 10)

#### Match Type `dropDown` `required`


The match output strategy to be employed for this lookup


 - strict
 - invalid
 - enhanced

---

### Verify Single International Address (getInternationalAddress)


Verifies a single international address - requires Country, Address1, Locality and Adminsitrative Area

#### Address Line 1 `textField`


Address Line 1 value (EX: Rua Padre Antonio Angelo 121)

#### Address Line 2 `textField`


Address Line 2 value (EX: Casa Verde)

#### Locality `textField`


Locality value (EX: Sao Paulo)

#### Administrative Area `textField`


Administrative Area value (EX: SP)

#### Postal Code `textField`


Postal Code value (EX: 02516-040)

#### Country `textField`


Country value (Brazil)

---



### Resource description

Please visit the Methodology page on Smarty's website for additional definitions: https://www.smarty.com/docs/methodology

# Limitations

The connector can only validate one address at a time. Set up multiple instances of the connector in your flow if you need to validate more than one address.
