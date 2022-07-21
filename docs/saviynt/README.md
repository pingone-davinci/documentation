# Saviynt Connector

Author: Ping Identity

# Introduction

Saviynt connector can be used for account creation and provisioning for users created in Saviynt account. This connector allows you to:

1. Create User
2. Update User
3. Get Account Details
4. Update User Request
5. Fetch Request History
6. Approve-Reject Request
7. Get Request Approval Details
8. Get Pending Requests
9. Create user request with approval
10. Remove Role
11. Get Role Details
12. Add Role
13. Inactive user
14. Get User Details

# Setup

## Resources

For information and setup help, see the following sections of the Saviynt API documentation:

- [Get Authorization Token](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#2117ad42-4129-47bb-8268-04b463da32db)
- [Create User](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#2ee1eb47-d65a-4b82-b25c-adc7e91d1b1b)
- [Update User](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#33026188-3e79-4612-a76c-c1455c5b81a9)
- [Get Account Details](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#03c67f69-ab92-4528-8c29-8d0024503245)
- [Update User Request](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#4ef1a6b5-a2c0-468b-9293-20568a0c3f8f)
- [Fetch Request History](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#179c7142-675e-4f50-a8c8-4be699e539e3)

* [Approve-Reject request](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#c1518440-2f00-430b-aed4-4bb9a61ea56d)
* [Get Request approval details](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#27a9d653-7ae8-4a13-99a1-27914dbb8416)
* [Get Pending Requests](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#e9aaa65a-bf5c-4d74-80b2-e89b51506b29)
* [Create User request](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#2ee1eb47-d65a-4b82-b25c-adc7e91d1b1b)

- [Remove Role](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#b3b548e1-4e84-4289-aa04-ae809f7efc0f)
- [Get Role Details](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#98691765-9b0b-4907-9c43-9d22331e4f93)
- [Add Role](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#140feb81-cc65-4090-baf0-66af64b0c895)
- [Inactive User](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#33026188-3e79-4612-a76c-c1455c5b81a9)
- [Get User Details](https://documenter.getpostman.com/view/1797923/RWaLwo21?version=latest#1eee7b3c-d581-412f-9049-d9bbb70fb3f4)

## Requirements

To use the connector, you'll need:

- Saviynt Admin User Account Access
- Saviynt API Domain url and path

## Setting up the connector

In Davinci, add a **Saviynt User Non-Approval Flow** connection via the "Connections" tab in your Davinci Environment. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector Settings

Once you've added the Saviynt User Non-Approval Flow connection click on it's logo, or click the "···" button and edit. You will see the connector's details pop-up. On the GENERAL tab, enter in your Saviynt account details below to get Authorization Token

1. Saviynt Domain url
2. Saviynt Path
3. Saviynt Admin Username
4. Saviynt Admin Password

and click apply. This ensures that whenever you use this connector you will not have to reenter this information and username and password is used for generated Token passed as input to Authorise below connector in flow.

# Using the connector in a flow

## Create User

To create user in the savinyt add a Saviynt connector in the flow studio. Then choose the Create User capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.

![Create User Flow](../assets/Createuser.PNG)

## Update user details

To update user attributes saved in the savinyt add a Saviynt connector in the flow studio. Then choose the Update User capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.

![Update User Attributes](../assets/UpdateUser.PNG)

## Get Account Details

To get account details of user in the savinyt add a Saviynt connector in the flow studio. Then choose the Get account details capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.

![Get Account Details](../assets/GetAccountDetails.PNG)

## Update User Request

To update user request in the savinyt add a Saviynt connector in the flow studio. Then choose the Update User Request capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.

![Update User Request](../assets/UpdateUserRequest.PNG)

## Fetch Request History

To fetch request history in the savinyt add a Saviynt connector in the flow studio. Then choose the Fetch Request History capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.

![Fetch Request History](../assets/FetchRequestHistory.PNG)

## Approve-Reject Request

To get the lists the existing user details based on search parameter provided add a Saviynt connector in the flow studio. Then choose the userdetails capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the list of users based on filter criteria/username submitted.

![Approve Reject](../assets/Approve-RejectRequest.PNG)

## Get Request Approval Details

To Get Request Approval Details saved in the savinyt add a Saviynt User Approval Flow connector in the flow studio. Then choose the Get Request Approval Details capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.
![Get Request Approval details](../assets/GetRequestApprovalDetails.PNG)

## Get Pending Requests

To inactivate the exsting savinyt user add a Saviynt connector in the flow studio. Then choose the Inactivate User capability. Provide the username parameters from previous nodes in the flow (HTML form) to modify the user status.
![Get Pending Request](../assets/GetPendingRequests.PNG)

## Create User with approval

To create user in the savinyt add a Saviynt User Approval Flow connector in the flow studio. Then choose the Create User capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.
![Create User request](../assets/Createuserrequestwithapproval.PNG)

## Remove Role

To remove role added for an existing saviynt user add a Saviynt connector in the flow studio. Then choose the Remove Role capability. Provide the input parameters(username & rolename) from previous nodes in the flow (HTML form) and submit the details.

![Remove Role Flow](../assets/RemoveRole.PNG)

## Get Role Details

To get role details saved add a Saviynt connector in the flow studio. Then choose the Get Role Details For User capability. Provide the input parameters from previous nodes in the flow (HTML form) and submit the details.

![Get Role Details Flow](../assets/GetRoleDetails.PNG)

## Add Role

To add role to the existing saviynt user add a Saviynt connector in the flow studio. Then choose the Add role to an user capability. Provide the input parameters(username & rolename) from previous nodes in the flow (HTML form) and submit the details.

![Add Role Flow](../assets/AddRole.PNG)

## Inactive user

To inactivate the exsting savinyt user add a Saviynt connector in the flow studio. Then choose the Inactivate User capability. Provide the username parameters from previous nodes in the flow (HTML form) to modify the user status.

![Inactivate User Flow](../assets/Inactiveuser.PNG)

## Get User Details

To get the lists the existing user details based on search parameter provided add a Saviynt connector in the flow studio. Then choose the userdetails capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the list of users based on filter criteria/username submitted.

![Get User Details Flow](../assets/GetUserDetails.PNG)

# Capabilities

### Create User (createUser)


Create an user in saviynt

#### First Name `textField` `required`


First Name of the user

#### Middle Name `textField`


Provide your middle name

#### Username `textField` `required`


username for the create user

#### Last Name `textField` `required`


Last Name of the user

#### Email `textField` `required`


Email of the user

#### Employee Type `dropdownWithCreate`


Select any employee type


 - Tester
 - Manager
 - TeamLead
 - Developer

#### Start Date `textField` `required`


Start Date of the user

#### End Date `textField` `required`


Provide last date of the user

#### City `textField`


Provide your city name

#### State `textField`


Provide your state name

#### Phone Number `textField`


Provide your phone number

#### Country `textField`


Provide your country name

#### Company Name `textField`


Provide your company name

#### Other Attributes `variableInputList`


Add other attributes and their values.

---

### Update User (updateUser)


Update an user in saviynt

#### First Name `textField` `required`


First Name of the user

#### Middle Name `textField`


Provide your middle name

#### Username `textField` `required`


username for the create user

#### Last Name `textField` `required`


Last Name of the user

#### StatusKey `toggleSwitch`


Statuskey of the user

#### Email `textField` `required`


Email of the user

#### Employee Type `dropdownWithCreate`


Select any employee type


 - Tester
 - Manager
 - TeamLead
 - Developer

#### Start Date `textField` `required`


Start Date of the user

#### End Date `textField` `required`


Provide last date of the user

#### City `textField`


Provide your city name

#### State `textField`


Provide your state name

#### Phone Number `textField`


Provide your phone number

#### Country `textField`


Provide your country name

#### Company Name `textField`


Provide your company name

#### Other Attributes `variableInputList`


Add other attributes and their values.

---

### Inactivate User (inactivateUser)


Inactivate an user in saviynt

#### Username `textField` `required`


username for the create user

---

### Get User Details (getUserDetails)


Get an user details from saviynt

#### Username `textField` `required`


username for the create user

#### Response Fields `textField`


User attributes which you want to see in the response

#### Filter Criteria `textField`


User fields based on which you want to get the user attribute details(including userkey)

#### Search Criteria `textField`


search for a user based on the string passed (eg - “*ab*” or “*ab” or “ab*”) in their firstname, lastname, displayname and username only, example - "ab*" - This will return all users with firstname or lastname or username starting with "ab"

#### Advance Search Criteria `textField`


search for a user based on the string passed (eg - “*ab*” or “*ab” or “ab*”), example - {"username":"a*", "firstname":"*b"} - This will return all users with username starting with "a" AND firstname ending with "b". Exact match search is applicable for types boolean, users, customer. Date can be entered in format - yyyy-MM-dd.

#### Maximum number of requests `textField`


Maximum number of requests

#### Offset `textField`


Offset

#### Sort `textField`


Sort

#### Order `textField`


 asc/desc

#### Manager `textField` `required`


Manager of the user

#### Show Security Answers `textField`


"0"/"1" to display encrypted security answers for the user

---

### Add Role To User (addRoleToUser)


This will add existing role to an user

#### Username `textField` `required`


username for the create user

#### Role Name `textField` `required`


Provide a role name

---

### Get Role Details Of User (getRoleDetailsOfUser)


This will fetch all roles of an user

#### Username `textField` `required`


username for the create user

---

### Remove Role From User (removeRoleFromUser)


This will remove role from an user

#### Username `textField` `required`


username for the create user

#### Role Name `textField` `required`


Provide a role name

---

### Create User With Approval (createUserWithApproval)


Create User

#### First Name `textField` `required`


First Name of the user

#### Last Name `textField` `required`


Last Name of the user

#### Roles `textField` `required`


Roles of the user

#### Employee Type `dropdownWithCreate`


Select any employee type


 - Tester
 - Manager
 - TeamLead
 - Developer

#### Start Date `textField` `required`


Start Date of the user

#### Status `toggleSwitch` `required`


Status of the user

#### StatusKey `toggleSwitch`


Statuskey of the user

#### Manager `textField` `required`


Manager of the user

#### Email `textField` `required`


Email of the user

#### System Username `textField` `required`


System username of the user

#### Enabled `textField` `required`


To enable disable the user

#### Username `textField` `required`


username for the create user

---

### Get Pending Requests (getPendingRequests)


Get Pending Requests

#### Maximum number of requests `textField`


Maximum number of requests

#### Request Key `textField` `required`


Request Key of the pending request

---

### Get Request Approval Details (getRequestApprovalDetails)


Get Request Approval Details

#### Request Key `textField` `required`


Request Key of the pending request

---

### Approve-Reject Request (approveRejectRequest)


Approve-Reject Request

#### Request Key `textField` `required`


Request Key of the pending request

#### Request ID `textField` `required`


Request ID of pending request to approve/reject

#### Request Action `textField` `required`


it will take the value either 1 or 2 for approve/reject respectively

#### Comments `textField`


Comments by approver for particular request

---

### Fetch Request History (fetchRequestHistory)


Fetch Request History

#### Status `toggleSwitch` `required`


Status of the user

#### Maximum number of requests `textField`


Maximum number of requests

---

### Update User Request (updateUserRequest)


Update User Request

#### Username `textField` `required`


username for the create user

#### First Name `textField` `required`


First Name of the user

#### Last Name `textField` `required`


Last Name of the user

#### Designation `textField`


Provide designation

#### Manager `textField` `required`


Manager of the user

---

### Get Account Details (getAccountDetails)


Get Account Details

#### Status `toggleSwitch` `required`


Status of the user

#### Name `textField`


Provide your name

#### Type `textField` `required`


Provide type

#### Value `textField`


Provide value

#### Rank `textField`


Provide rank

---


# Limitations

Use of connector is limited by the availability of Saviynt API and account access.
