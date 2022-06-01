# IPGeoLocation.io Connector

## Doc draft
Author: arno@pingidentity.com


# Introduction
Free IP API provides country, city, state, province, local currency, latitude and longitude, company detail, ISP lookup, language, zip code, country calling code, time zone, current time, sunset and sunrise time, moonset and moonrise time from any IPv4 and IPv6 address in REST, JSON and XML format over HTTPS.

# Setup
## Resources
For information and setup help, see the following sections of the ipgeolocation.io documentation:
https://ipgeolocation.io/documentation/ip-geolocation-api.html

## Requirements
You will need to obtain an API Key even for the free API.
You may obtain one by signing up at: https://ipgeolocation.io/signup.html

## Setting up the connector
When creating an instance of this connector in DaVinci, you will need to set your API key in the connector settings. That's the only thing you need.

### Connector settings
API Key: you can get the API Key once you have signed up by logging in to your ipgeolocation.io account at https://app.ipgeolocation.io/auth/login

# Using the connector in a flow
TO use the connector in a flow, you can pass it the global.ip variable or another IP address obtained from another connection.

## [Use case]
IP Geolocation is a technique used to find out the geographical location of the user using his IP address. Wherever in the world, you use the internet, you will be assigned an IP address. This IP address contains your network identity and your location information. This information is used by online businesses to recognize their visitors and offer a more local experience such as displaying prices in local currency , calculating shipping cost based on the detected conutry or copmuting time differences with the detected timezone.

# Capabilities
### Single Lookup (singleLookup)


Single IP address lookup

#### IP address `textField` `required`


IP address to lookup

#### Language `dropDown`


Paid plan subscriptions can get the response in languages other than English.


 - English
 - German
 - Russian
 - Japanese
 - French
 - Chinese Simplified
 - Spanish
 - Czech
 - Italian

---


# Limitations
This connector does not implement 
  . the astronomy or timezone APIs that ipgeolocation.io also offers
  . the bulk IP gelocation API
