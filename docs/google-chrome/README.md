# Google Chrome Device Trust Connector

Author: Peter Holko (peterholko@pingidentity.com)

# Introduction

The Google Chrome Device Trust connector can be used to include operating system device signals collected by Google Chrome in a PingOne DaVinci flow.  


# Setup

## Resources

#### For information and additional help, see the following sections of the Google Chrome Device Trust documentation:

- [Google Chrome Device Trust Documentation](https://www.google.com/search?q=google+todo)

## Requirements

#### To use the Google Chrome Device Trust connector:

- You must have access create a Google Cloud Project
  - Ability to add “Chrome Verified Access API” to the project
  - Ability to create an API Key
  - Ability to create a Service Account
- You must have access Chrome Browser Management Console
  - Ability to set policies for enrolled browsers



## Setting up the connector

#### Google Chrome Device Trust Connector General Settings:

- Navigate to the Google Chrome Device Trust connector via the _**Connections**_ tab in DaVinci.
- Select _**New Connection**_ in the upper right-hand corner.
- Search for the desired connector (in this case, Google Chrome).
- Select the Google Chrome Device Trust connector.
- Once the Google Chrome Device Trust connector has been added the _**Your Connections**_ list, click on the connector.
- From here you will see three text fields labeled **API Key**, **Credentials Clients Email**, and **Private Key**.
  - **API Key**:
    - This text field is for your Google Cloud Project API Key.    
  - **Credentials Clients Email**:
    - The Google Cloud service account’s email address from the service account key.
  - **Private Key**:
    - The Google Cloud service account private key from the service account key.  

# Using the connector in a flow

### Google Chrome Device Trust use case:

- Retrieve operating systems signals from Google Chrome such as serial number, mac addresses and OS version.  


### Simple Use Case - retrieve device serial number:

- Navigate to the flow studio and in the upper right-hand corner select _**Create New Flow**_
- Select `Blank Flow`.
- Insert the desired name and description and click `Create`.
- Once inside the flow sandbox add the Google Chrome Device Trust connector and select the `Verify Access` capability.
- The `Verify Access` capability returns the Google Chrome Device Trust signals in the connector output if Device Trust is enabled within the Chrome browser policy. 
- To see the output of the Google Chrome Device Trust connector you can do the following:
    - Attach an HTTP block after your Mailgun connector.
    - Click on the Custom HTML Message capability.
    - In the _**Message**_ text area select the circular angel bracket button ( **{}** )
      - From the dropdown, select the Google Chrome Device Trust connector option with the `Verify Access` capability listed.
      - Choose the `output (object)` by clicking `(+)`.
    - Click `Apply`
- In the upper right hand corner click Save, Deploy, and Run.

---

---

# Capabilities

### Verify Access (initializeAuthorizationRequest)


Authenticate against Verified Access API

---

#### Output object

- output `object`
  - rawResponse `object`
  - statusCode `number`
  - headers `object`
  - deviceTrustEnabled boolean
  - devicePermanentId string
  - virtualDeviceId string
  - customerId string
  - keyTrustLevel string
deviceSignal object
browserVersion string
builtInDnsClientEnabled boolean
chromeCleanupEnabled boolean
chromeRemoteDesktopAppBlocked boolean
deviceAffiliationIds array
deviceEnrollmentDomain string
deviceHostName string
deviceManufacturer string
diskEncrypted number
displayName string
macAddresses array
os string
osFirewall number
osVersion string
passwordPotectionWarningTrigger number
profileAffiliationIds array
realtimeUrlCheckMode number
safeBrowsingProtectionLevel number
screenLockSecured number
secureBootEnabled number
serialNumber string
siteIsolationEnabled boolean
systemDnsServers array
thirdPartyBlockingEnabled boolean
