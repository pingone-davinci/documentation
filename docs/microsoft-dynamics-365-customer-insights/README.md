# Microsoft Dynamics 365 Customer Insights

# Introduction

The Microsoft Dynamics 365 Customer Insights connector allows users to perform quick and seamless CRUD operations on important contacts and leads. 

In order to achieve this the connector leverages its nine capabilities: <br>

1. Get Contact <br>
2. Create Contact <br>
3. Update Contact <br>
4. Delete Contact <br>
5. Get Lead <br>
6. Create Lead <br>
7. Update Lead <br>
8. Delete Lead <br>
9. Make Custom API Call <br>

# Setup

## Resources

For information and setup help, see the following sections of the Microsoft Dataverse documentation:
* [Microsoft Dynamics 365 Documentation](https://learn.microsoft.com/en-us/dynamics365/)
* [Wep API Reference](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/webapi/reference/about)
* [Contact Entity Reference](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/webapi/reference/contact)
* [Lead Entity Reference](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/webapi/reference/lead)


## Requirements

To use the connector, you will need:
* [Environment Name](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/webapi/compose-http-requests-handle-errors#:~:text=https%3A//-,Environment%20Name,-The%20unique%20name)
* [Base URL](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/webapi/compose-http-requests-handle-errors#:~:text=Region,Datacenter%20regions.)
    * This connector property combines both [Region](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/webapi/compose-http-requests-handle-errors#:~:text=be%20contoso.-,Region,-Your%20environment%20is) + [Base URL](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/webapi/compose-http-requests-handle-errors#:~:text=see%20Datacenter%20regions-,Base%20URL,-This%20is%20usually)
    * E.g. `crm.dynamics.com`
* [Version](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/webapi/compose-http-requests-handle-errors#:~:text=api/data/.-,Version,-The%20version%20is)
* Tenant
* Client ID
* Client Secret
* Grant Type

These properties can be found in your Microsoft Dynamics 365 client application. 

## Setting up the connector

#### Microsoft Dynamics 365 Connector General Settings:
* Navigate to the Microsoft Dynamics 365 connector via the _**Connections**_ tab in DaVinci.
* Select _**New Connection**_ in the upper right-hand corner
* Search for the desired connector (in this case, _**Microsoft Dynamics 365**_ ).
* Click on the Microsoft Dynamics 365 connector and add it to your connector list.
* From here add in the _Environment Name_, _Base URL_, _Version_, _Tenant_, _Client ID_, _Client Secret_, and _Grant Type_ from the Requirements section above.

# Using the connector in a flow

#### You can use the Microsoft Dynamics 365 connector in a variety of use cases, such as:
* Creating a new contact based on an interested party's information
* Removing an inactive contact or lead
* Retrieving important information in regards to a contact or lead
* etc...

## Retrieving Information about a Contact
1. **Add the Microsoft Dynamics 365 Connector**
    * Select the `Get Contact` capability
    * Fill the `Contact Email` text field with the email address of the desired contact
    * Click `Apply`
    <br><br>
2. **Show Microsoft Dynamics 365 Results**
    * Next add the HTTP connector 
    * Select the `Custom HTML Message` capability.
    * Create a new Mesasge Title
    * Inside the Message text area, click the **{}** button and select the output variable from the Microsoft Dynamics 365 connector by clicking **+**.

# Capabilities

