# Securonix Connector

# Introduction

Securonix connector can be used for retrieving data of users and activities Securonix account. This connector allows you to:

1. Retrieve Geolocation
2. Retrieve Activities
3. Risk Score History
4. Retrieve Incident List
5. Get User Risk Score
6. Get Lookup Data
7. Get Child Incident
8. Get User Details
9. Get Third Party Intel
10. Incident Details

# Setup

## Resources

For information and setup help, see the following sections of the Securonix API documentation:

- [Get Authorization Token](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm)
- [Retrieve Geolocation](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#Geolocation)
- [Retrieve Activities](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#Activity)
- [Risk Score History](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#RiskHistory)
- [Retrieve Incident List](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#IncidentManagement)
- [Get User Risk Score](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#RiskHistory)
- [Get Lookup Data](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#Lookup)
- [Get Child Incident](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#IncidentManagement)
- [Get User Details](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#Users)
- [Get Third Party Intel](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#ThirdPartyIntel)
- [Incident Details](https://documentation.securonix.com/onlinedoc/Content/Cloud/Content/SNYPR%206.3/Web%20Services/6.3_REST%20API%20Categories.htm#IncidentManagement)

## Requirements

To use the connector, you'll need:

- Securonix Admin User Account Access
- Securonix API Domain url

## Setting up the connector

In Davinci, add a Securonix Flow connection via the "Connections" tab in your Davinci Environment. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector Settings

Once you've added the Securonix Flow connection click on it's logo, or click the "···" button and edit. You will see the connector's details pop-up. On the GENERAL tab, enter in your Securonix account details below

1. Securonix API token (Token need to be generated for a longer validity)
2. Securonix Domain url

and click apply. This ensures that whenever you use this connector you will not have to reenter this information and generated Token passed as input to Authorise below connector in flow.

# Using the connector in a flow

## Retrieve Geolocation

To retrieve Geolocation add a Securonix Connector in the flow studio. Then choose the Retrieve Geolocation capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the geolocation details.

![Retrieve Geolocation](../assets/RetrieveGelocation.PNG)

## Retrieve Activities

To retrieve activites add a Securonix Connector in the flow studio. Then choose the Retrieve Activities capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the activities details.

![Retrieve Activities](../assets/RetrieveActivities.PNG)

## Risk Score History

To get risk Score History add a Securonix Connector in the flow studio. Then choose the Risk Score History capability. Provide the parameters from previous nodes in the flow (HTML form) to get risk score history details.

![Risk Score History](../assets/RiskScoreHistory.PNG)

## Retrieve Incident List

To get Retrieve Incident List add a Securonix Connector in the flow studio. Then choose the Retrieve Incident List capability. Provide the parameters from previous nodes in the flow (HTML form) to get Incident List details.

![Retrieve Incident List](../assets/RetrieveIncidentlist.PNG)

## User Risk Score

To retrieve risk scorecard of all users add a Securonix Connector in the flow studio. Then choose the Get User Risk Score capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the Risk scorecard.

![Get User Risk Score](../assets/GetUserRiskScore.PNG)

## Get Lookup Data

To retrieve lookup data information add a Securonix Connector in the flow studio. Then choose the Get Lookup Data capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve lookup data information.

![Get Lookup Data](../assets/GetLookupData.PNG)

## Get Child Incidents

To retrieve Child Incidents associated with Parent Incident add a Securonix Connector in the flow studio. Then choose the Get Child Indidents capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the incident details.

![Get Child Incidents](../assets/GetChildIncident.PNG)

## User Details

To retrieve user details from SNYPR add a Securonix Connector in the flow studio. Then choose the Get User Details capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the user details using a unique identifier.

![Get User Details](../assets/GetUserDetails.PNG)

## Third Party Intel Data

To retrieve Third-Party Intel (TPI) data from sources such as DLP, web gateways, proxies, and firewalls add a Securonix Connector in the flow studio. Then choose the Get Third Party Intel capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the Third Party Intel data.

![Get Third Party Intel](../assets/GetThirdPartyIntel.PNG)

## Incident Details

To retrieve Incident details add a Securonix Connector in the flow studio. Then choose the Get Third Party Intel capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve incident details.

![Incident Details](../assets/IncidentDetails.PNG)

# Capabilities

### Retrieve Activities (retrieveActivities)


Retrieve Activities

#### Event Time From `textField` `required`


Enter the event time start range in format MM/dd/yyyy HH:mm:ss

#### Event Time To `textField` `required`


Enter the event time end range in format MM/dd/yyyy HH:mm:ss

#### Time Zone `textField`


If empty, the application timezone will be selected

#### Pretty JSON `toggleSwitch`


If set to true, sends the REST response in a pretty JSON format else raw format. By default, it is set to False

#### Max `textField`


Enter the number of records you want

#### Query ID `textField`


Used for paginating through the results in the specified duration to get the next set of maximum records.

---

### Retrieve Geolocation (retrieveGeolocation)


Retrieve Geolocation

#### City `textField`


City

#### Country Code `textField`


Country Code

#### Latitude `textField`


Latitude

#### Location `textField`


Location

#### Longitude `textField`


Longitude

#### Region `textField`


Region

#### Source `textField`


Source

#### IP To `textField`


IP To

#### IP From `textField`


IP From

---

### Risk Score History (riskScoreHistory)


Risk Score History

#### Employee ID `textField`


Employee ID

---

### Retrieve Incident List (retrieveIncidentList)


Retrieve Incident List

#### From `textField` `required`


Enter the start time in ms. This parameter is required.

#### To `textField` `required`


Enter the end time in ms. This parameter is required.

#### Offset `textField`


This parameter is optional and used for pagination.

#### Status `toggleSwitch`


Identity Attribute

#### Range Type `textField` `required`


Enter any of the following range types: updated/opened/closed.This parameter is required

#### Allow Child Cases `toggleSwitch`


Enter true to receive the list of child cases associated with a parent case in the response. Otherwise, enter false. This parameter is optional.Enter true to receive the list of child cases associated with a parent case in the response. Otherwise, enter false. This parameter is optional.

#### Max `textField`


Enter the number of records you want

#### Sort `textField`


Enter any of the following sort order in which the records are displayed: desc/asc.This parameter is optional.

---

### Retrieve Incident Details (incidentDetails)


Retrieve Incident Details

#### Incident ID `textField` `required`


Provide incidentId.

---

### Get User Details (getUserDetails)


Get an user details

#### Employee ID `textField`


Employee ID

---

### Get Third Party Intel (getThirdPartyIntel)


Get Third Party Intel

#### TPI Domain `textField`


Provide third party intel domain name.

#### TPI Address `textField`


Provide third party intel address.

#### TPI Category `textField`


Provide third party intel category.

#### TPI Criticality `textField`


Provide third party intel criticality.

#### TPI Date `textField`


Provide third party intel date.

#### TPI SRC `textField`


Provide third party intel SRC.

#### TPI Type `textField`


Provide third party intel type.

---

### Get User Risk Score (getUserRiskScore)


Get User Risk Score

#### Violator `textField`


Violation Attribute

#### Company Code `textField`


Identity Attribute

#### Cost Center Name `textField`


Identity Attribute

#### Country `textField`


Identity Attribute

#### Department `textField`


Identity Attribute

#### Division `textField`


Identity Attribute

#### Employee ID `textField`


Employee ID

#### Employee Type `textField`


Identity Attribute

#### Employee Type Description `textField`


Identity Attribute

#### First Name `textField`


Identity Attribute

#### Hire Date `textField`


Identity Attribute

#### Job Code `textField`


Identity Attribute

#### LAN ID `textField`


Identity Attribute

#### Last Name `textField`


Identity Attribute

#### Location `textField`


Location

#### Manager Employee ID `textField`


Identity Attribute

#### Status `toggleSwitch`


Identity Attribute

#### Status Description `textField`


Identity Attribute

#### Title `textField`


Identity Attribute

#### User ID `textField`


Identity Attribute

#### Work Email `textField`


Identity Attribute

#### Work Phone `textField`


Identity Attribute

---

### Get Look Up Data (getLookUpData)


Get Look Up Data

#### Key `textField` `required`


Provide key.

#### LookUp Name `textField` `required`


Provide lookup name.

#### value_u_customfield11 `textField`


Provide value_u_customfield11.

#### value_u_customfield4 `textField`


Provide value_u_customfield4.

---

### Get Child Incidents (getChildIncidents)


Get Child Incidents

#### Incident ID `textField` `required`


Provide incidentId.

---


# Limitations

Use of connector is limited by the availability of Securonix API and account access.
