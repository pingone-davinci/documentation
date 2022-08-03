# Zscaler User Flow Connector


# Introduction

Zscaler User Flow Davinci connector can be used to create and manage user details. This connector allows you to:

1. Create User
2. Update User
3. Get User Details
4. Delete User
5. Get Group by ID
6. Get All Groups
7. Get Department by ID
8. Get All Departments

# Setup

## Resources

For information and setup help, see the following sections of the Zscaler documentation:

- [Pre-requisite to Access API](https://help.zscaler.com/zia/getting-started-zia-api)
- [User Management API](https://help.zscaler.com/zia/user-management#)

## Requirements

To use the connector, you'll need:

- ZIA Admin Portal Access

## Setting up the connector

In Davinci, add a **Zscaler User Flow** connection via the "Connections" tab in your Davinci Environment. For help, see [Adding a connection](https://docs.google.com/document/d/1Sc9tD5tn9dl79qOWup0k3eKk5hrNVI8lZPAdm8loeiA/edit#).

### Connector Settings

Once you've added the Zscaler User Flow connection click on it's logo, or click the "···" button and edit. You will see the connector's details pop-up. On the GENERAL tab, enter in your Zscaler admin account details below:

1. Zscaler Domain url
2. Zscaler Base path
3. API Key
4. Admin Username
5. Admin Password

and click apply. This ensures that whenever you use this connector you will not have to reenter this information and generate the cookie to be used in flow to authenticate and create API sessions.

# Using the connector in a flow

## Create User Flow

To create user add a Zscaler User Flow Connector in the flow studio. Then choose the Create User - Zscaler capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.

![Create User Flow](../assets/ZscalerCreateUserFlow.png)

## Update User Flow

To update user attributes saved add a Zscaler User Flow Connector in the flow studio. Then choose the Update User - Zscaler capability. Provide the input parameters to be updated from previous nodes in the flow (HTML form) and submit the details.

![Update User Flow](../assets/ZscalerUpdateUserFlow.png)

## Delete User Flow

To inactivate the exsting user add a Zscaler User Flow Connector in the flow studio. Then choose the Update User - Zscaler capability. Provide the username parameters from previous nodes in the flow (HTML form) to delete the existing user.

![Delete User Flow](../assets/ZscalerDeleteUserFlow.png)

## Get User Flow

To get the lists the existing user details based on search parameter provided add a Zscaler User Flow Connector in the flow studio. Then choose the Get User capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the list of users based on filter criteria submitted.

![Get User Flow](../assets/ZscalerGetUserFlow.png)

## Get All Groups

To get list of Groups add a Zscaler User Flow Connector in the flow studio. Then choose the Get All Groups - Zscaler capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the list of Groups available based on search query submitted.

![Get All Groups](../assets/ZscalerGetAllGroupsFlow.png)

## Get Group By ID

To get groups by user ID add a Zscaler User Flow Connector in the flow studio. Then choose the Get Group by ID - Zscaler capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the Group details based on Group ID.

![Get Group By ID](../assets/ZscalerGetGroupByIDFlow.png)

## Get All Departments

To get list of Departments add a Zscaler User Flow Connector in the flow studio. Then choose the Get All Departments - Zscaler capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the list of Departments available based on search query submitted.

![Get All Departments](../assets/ZscalerGetAllDepartmentsFlow.png)

## Get Department by ID

To get Department by user ID add a Zscaler User Flow Connector in the flow studio. Then choose the Get Department by ID - Zscaler capability. Provide the parameters from previous nodes in the flow (HTML form) to retrieve the Department details based on Department ID.

![Get Department By ID](../assets/ZscalerGetDepartmentByIDFlow.png)

# Capabilities

### Create User (createUser)


Adds a new user

#### User Name `textField` `required`


User Name

#### Email `textField`


User email consists of a user name and domain name

#### Groups ID `textField` `required`


Unique identfier for the group

#### Groups Name `textField` `required`


Group name

#### Groups IDPID `textField`


Unique identfier for the identity provider

#### Groups Comments `textField`


Additional information about the group

#### Department ID `textField` `required`


Department ID

#### Department Name `textField` `required`


Department name

#### Department IDPID `textField`


Identity provider (IdP) ID

#### Department Comments `textField`


Additional information about this department

#### Department Deleted `toggleSwitch`


default: false

#### Comments `textField`


Additional information about this user

#### Temporary Authentication Email `textField`


If you enabled one-time tokens or links, enter the email address to which the Zscaler service sends the tokens or links. If this is empty, the service will send the email to the User email.

#### User Password `textField` `required`


User password. Applicable only when authentication type is Hosted DB. Password strength must follow what is defined in the auth settings

#### adminUser `toggleSwitch`


default: false

#### type `dropDown`


type


 - SUPERADMIN
 - ADMIN
 - AUDITOR
 - GUEST
 - REPORT_USER
 - UNAUTH_TRAFFIC_DEFAULT

---

### Update User (updateUser)


Updates the user information for the specified ID

#### userID `textField` `required`


userID

#### User Name `textField` `required`


User Name

#### Email `textField`


User email consists of a user name and domain name

#### Groups ID `textField` `required`


Unique identfier for the group

#### Groups Name `textField` `required`


Group name

#### Groups IDPID `textField`


Unique identfier for the identity provider

#### Groups Comments `textField`


Additional information about the group

#### Department ID `textField` `required`


Department ID

#### Department Name `textField` `required`


Department name

#### Department IDPID `textField`


Identity provider (IdP) ID

#### Department Comments `textField`


Additional information about this department

#### Department Deleted `toggleSwitch`


default: false

#### Comments `textField`


Additional information about this user

#### Temporary Authentication Email `textField`


If you enabled one-time tokens or links, enter the email address to which the Zscaler service sends the tokens or links. If this is empty, the service will send the email to the User email.

#### User Password `textField` `required`


User password. Applicable only when authentication type is Hosted DB. Password strength must follow what is defined in the auth settings

#### adminUser `toggleSwitch`


default: false

#### type `dropDown`


type


 - SUPERADMIN
 - ADMIN
 - AUDITOR
 - GUEST
 - REPORT_USER
 - UNAUTH_TRAFFIC_DEFAULT

---

### Get User (getUser)


Gets a list of all users and allows user filtering by name, department, or group

#### User Name `textField` `required`


User Name

#### Groups Name `textField` `required`


Group name

#### Department Name `textField` `required`


Department name

#### Page `textField`


Specifies the page offset

#### Page Size `textField`


Specifies the page size

---

### Delete User (deleteUser)


Delete User

#### userID `textField` `required`


userID

---

### Get All Department (getAllDepartments)


Gets a list of departments

#### Page `textField`


Specifies the page offset

#### Page Size `textField`


Specifies the page size

#### Search `textField`


The search string used to match against a  name or comments

#### Limit Search `textField`


Limits the search to match against the department name only

---

### Get Department By ID (getDepartmentByID)


Gets the department for the specified ID

#### Department ID `textField` `required`


Department ID

---

### Get All groups (getAllGroups)


Gets a list of groups

#### Search `textField`


The search string used to match against a  name or comments

#### Page `textField`


Specifies the page offset

#### Page Size `textField`


Specifies the page size

---

### Get Groups By ID (getGroupByID)


Gets the group for the specified ID

#### Groups ID `textField` `required`


Unique identfier for the group

---


# Limitations

- Use of Zscaler User Flow Connector is limited by the availability of Zscaler API and account access.
