---
title: DroneKit-Cloud

language_tabs:
  - shell
  - python
  
toc_footers:
  - <a href='https://cloud.dronekit.io/signup'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>


search: true
---

# Introduction

<aside class="warning">
This document is an un-reviewed draft. It may not accurately reflect the current API or its future direction.
</aside>

Welcome to DroneKit-Cloud, 3D Robotic's cloud API for drone management and control.

This first release of the API (v1) lets you store, share, and access vehicle and flight log information using simple REST APIs. We hope you will use it to build advanced drone tracking web apps like [Droneshare](http://www.droneshare.com/) and as a source of useful drone usage data.

In future releases we hope to extend the API to support live tracking and control of vehicles supporting the MAVLink protocol.

This documentation provides the information you need to get started. It includes the instructions on how to get an API id/key used for authorisation, API reference docs, and code fragments showing how to call many of the endpoints using Python and cURL (displayed in the right-pane relative next to their associated documentation).

If need more help, the best places to ask questions are our [discussion list](https://groups.google.com/forum/#!forum/drone-platform) and [StackOverflow](http://stackoverflow.com/questions/tagged/dronekit-cloud).


# Get Started

> To authorize, use this code:

```python

```

```shell
# TBD Show how done for different requests - this is supposed to be POST, but need to check
curl -d '{"some": "jsondata"}'  https://api.droneshare.com/api/v1/endpoint?api_key=app_id.your_app_key
```

In order to use the API you will need to [sign up for an API key](https://cloud.dronekit.io/signup) with the DroneKit-Cloud service, and also [create an account on DroneShare](http://www.droneshare.com/#create). Joining both services is quick, easy and free. 

After logging into DroneKit you will find your *App ID* and *App Key* [at this link](https://cloud.dronekit.io/). DroneKit expects for the ID and key to be included in all API requests to the server (expressed in the format `app_id.your_app_key`).  

The API base url is `https://api.droneshare.com/api/v1/` and the available endpoints are listed [below](#auth-session-operations).

Examples of how to use the API and authorise requests are shown on the right-pane. Make sure to replace `app_key` with your own id and key.



# Examples

A complete example in CoffeeScript is available in the form of the [DroneShare Website source code](              https://github.com/diydrones/droneshare). The most relevant file is [dapiServices.coffee](https://github.com/diydrones/droneshare/blob/master/src/scripts/services/dapiServices.coffee). 



# API Overview

TBD: 

- Cover privacy settings/privacy control: - (DEFAULT, PRIVATE, PUBLIC, SHARED, RESEARCHER)
- Explain what the main parts of the API do for you
- Explain benefits of login/what APIs it affects
TBD. Need to confirm what exactly ability to login gives you, as currently the default plan doesn't give you login rights.



# auth - Session operations

Session operations (login, logout, etc...) are managed through the ``auth`` endpoint. Some operations (not all) require that a session is set up.

## Create a new user record

```python

```

```shell
curl -d '{"login": "TheNewLogin", "password": "TheNewPassWord", "email": "anEmail@somedomain.com"}' https://api.droneshare.com/api/v1/user?api_key=appid.keyid 
```

> The command returns JSON with this Model Schema:

```json
{
  "login": "",
  "email": "",
  "fullName": "",
  "password": "",
  "tokens": {
    "owner": {},
    "conditions": [
      ""
    ],
    "foreignKey": "",
    "manifest": {},
    "allConditions": [
      ""
    ],
    "hasConstraint": false,
    "relation1": {
      "com$github$aselab$activerecord$inner$Relations$Relation$$_isLoaded": false,
      "com$github$aselab$activerecord$inner$Relations$Relation$$_cache": [
        {}
      ],
      "companion": {},
      "parameters": "Parameters[ActiveRecordBase[Object], Tuple1[ActiveRecordBase[Object]], Object]",
      "queryable": {},
      "manifest": {}
    },
    "associationClass": {},
    "companion": {},
    "source": {
      "com$github$aselab$activerecord$inner$Relations$Relation$$_isLoaded": false,
      "com$github$aselab$activerecord$inner$Relations$Relation$$_cache": [
        {}
      ],
      "companion": {},
      "parameters": "Parameters[ActiveRecordBase[Object], Tuple1[ActiveRecordBase[Object]], Object]",
      "queryable": {},
      "manifest": {}
    }
  },
  "hashedPassword": "",
  "groupId": "",
  "lastLoginDate": "",
  "lastLoginAddr": "",
  "defaultViewPrivacy": 0,
  "defaultControlPrivacy": 0,
  "emailVerified": false,
  "needNewPassword": false,
  "wantEmails": false,
  "passwordResetToken": 0,
  "passwordResetDate": "",
  "numberOfLogins": 0,
  "vehicles": {
    "owner": {},
    "conditions": [
      ""
    ],
    "foreignKey": "",
    "manifest": {},
    "allConditions": [
      ""
    ],
    "hasConstraint": false,
    "relation1": {
      "com$github$aselab$activerecord$inner$Relations$Relation$$_isLoaded": false,
      "com$github$aselab$activerecord$inner$Relations$Relation$$_cache": [
        {}
      ],
      "companion": {},
      "parameters": "Parameters[ActiveRecordBase[Object], Tuple1[ActiveRecordBase[Object]], Object]",
      "queryable": {},
      "manifest": {}
    },
    "associationClass": {},
    "companion": {},
    "source": {
      "com$github$aselab$activerecord$inner$Relations$Relation$$_isLoaded": false,
      "com$github$aselab$activerecord$inner$Relations$Relation$$_cache": [
        {}
      ],
      "companion": {},
      "parameters": "Parameters[ActiveRecordBase[Object], Tuple1[ActiveRecordBase[Object]], Object]",
      "queryable": {},
      "manifest": {}
    }
  },
  "grizzled$slf4j$Logging$$_logger": {}
}
```

This endpoint creates a new login.

Logins [created through droneshare](http://www.droneshare.com/create) can be used with the service.

<aside class="warning">Direct programmatic creation of logins is not supported in DroneKit-Cloud v1 (this operation can only be performed using an "administrator" key that is not publically available).</aside>


### HTTP Request

`POST /auth/create`

### Query Parameters

> The Json Model Schema for the body parameter (`UserJson`) is:

```json
{
  "login": "",
  "password": "",
  "email": "",
  "fullName": "",
  "wantEmails": "",
  "groups": "",
  "oldPassword": "",
  "defaultViewPrivacy": {},
  "defaultControlPrivacy": {}
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
body | [UserJson](#userjson) | body | Y | Json object with new user values






## Login user

```python
import requests

# apikey = appid.appkey
# options.username, options.password are DroneKit-Cloud username and password
# baseurl is http://api.droneshare.com/api/v1/'

def login():
	print "Logging In"
	r = requests.post(baseurl + 'auth/login',
		params = {"api_key": apikey},
		data = {"login": options.username, "password":options.password})
	print r.status_code
	print r.text

login()
```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
  "login": "",
  "password": "",
  "email": "",
  "fullName": "",
  "wantEmails": "",
  "groups": "",
  "oldPassword": "",
  "defaultViewPrivacy": {},
  "defaultControlPrivacy": {}
}
```

This endpoint logs into the service using the specified account parameters. A session is required in order to successfully call some endpoints.

Logins [created through droneshare](http://www.droneshare.com/create) can be used with the service (note that you need to have also confirmed the account using the email sent when you create the login).


### HTTP Request

`POST /auth/login`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
login | string | form | Y | The loginName for the account
password | string | form | Y | The password for the account

### Error codes


HTTP Status Code | Reason
--------- | ------- 
403 | login attempt failed



## Logout current user

```python

```

```shell
curl -d '' https://api.droneshare.com/api/v1/auth/logout?api_key=appid.keyid 
```

> The command returns a string like this:

```json

```

This endpoint logs the user out of the current session.


### HTTP Request

`POST /auth/logout`


### Query Parameters

There are no query parameters.




## Get current logged-in user


```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
  "login": "",
  "password": "",
  "email": "",
  "fullName": "",
  "wantEmails": "",
  "groups": "",
  "oldPassword": "",
  "defaultViewPrivacy": {},
  "defaultControlPrivacy": {}
}
```

This endpoint gets the object for the current logged in user, or an error code if no user is logged in.


### HTTP Request

`GET /auth/user`

### Query Parameters

None

### Error codes


HTTP Status Code | Reason
--------- | ------- 
401 | User is not logged in




# user - User operations

This API exposes operations for browsing and searching lists of users, and retrieving single user. 

TBD: What does privacy mean. What information is available about users? Looks like default is to expose nothing other than userid and full name and gravitar. Also vehicles, but deal with that separately. Can we change the privacy? 


## JSON Objects

### UserJson

> The `UserJson` object has the following Model Schema:

```json
{
  "login": "",
  "password": "",
  "email": "",
  "fullName": "",
  "wantEmails": "",
  "groups": "",
  "oldPassword": "",
  "defaultViewPrivacy": {},
  "defaultControlPrivacy": {}
}
```

The `UserJson` object has the following parameters:

Parameter | Data Type | Required | Description
--------- | ------- | ------- | -----------
login | string | Y | The loginName for the account
password | string |  | The password for the account
email | string |  | Email address for the account
fullName | string |  | Full name for the new user
wantEmails | string |  | Whether or not the user wants to receive update emails
groups | string |  | The user's group membership.
oldPassword | string |  | The old/current password for the account when changing the password
defaultViewPrivacy | EnumVal |  | The view privacy setting
defaultControlPrivacy | EnumVal |  | The control privacy setting





## Show all users

```python
import requests

# apikey = appid.appkey
# options.username, options.password are DroneKit-Cloud username and password
# baseurl is http://api.droneshare.com/api/v1/'


def get_users():
	print "Getting all users info"
	r = requests.get(baseurl + 'auth/user',
		params = {"api_key": apikey})
	print r.status_code
	print r.text

get_users()
```	



```shell

```

> The command returns JSON with this Model Schema:

```json
[
  {
    "login": "",
    "password": "",
    "email": "",
    "fullName": "",
    "wantEmails": "",
    "groups": "",
    "oldPassword": "",
    "defaultViewPrivacy": {},
    "defaultControlPrivacy": {}
  }
]
```

This endpoint lists all users stored by the service.


### HTTP Request

`GET /user`


### Query Parameters

The query parameters are:

Parameter | Parameter type | Data type | Description
--------- | ------- | ------- | -----------
page_offset| query | integer | If paging, the record # to start with (use 0 at start)
page_size| query | integer | If paging, the # of records in the page
order_by| query | string | To get sorted response, the field name to sort on
order_dir| query | string | If sorting, the optional direction. either asc or desc





## Create user with auto-ID

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint creates a new user object with a dynamically constructed ID.

TBD. 
-Do you need to be logged into create this user. HOw does this differ from the auth command version. Do you still need special keys? What is the string returned.
- What is format of wantsEmails
- What is format of groups. How do groups work?
- What are the privacy settings. 
- Above need to suggest what should be set when creating a user.


### HTTP Request

`PUT /user`


### Query Parameters

> The Json Model Schema for the body parameter is:

```json
{
  "login": "",
  "password": "",
  "email": "",
  "fullName": "",
  "wantEmails": "",
  "groups": "",
  "oldPassword": "",
  "defaultViewPrivacy": {},
  "defaultControlPrivacy": {}
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
body | [UserJson](#userjson) | body | Y | Json object with updated user values





## Find user by id

```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
  "login": "",
  "password": "",
  "email": "",
  "fullName": "",
  "wantEmails": "",
  "groups": "",
  "oldPassword": "",
  "defaultViewPrivacy": {},
  "defaultControlPrivacy": {}
}
```

This endpoint returns the user object for a specific id (loginName).


### HTTP Request

`GET /user/{id}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of user that needs to be fetched






## Update user by id

```python

```

```shell

```

> The command returns a string.

This endpoint updates a specified (by loginName) user with new information.


### HTTP Request

`PUT /user/{id}`


### Query Parameters

> The Json Model Schema for the body parameter is:

```json
{
  "login": "",
  "password": "",
  "email": "",
  "fullName": "",
  "wantEmails": "",
  "groups": "",
  "oldPassword": "",
  "defaultViewPrivacy": {},
  "defaultControlPrivacy": {}
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id (loginName) of user that needs to be updated
body | [UserJson](#userjson) | body | Y | Json object with updated user information





## Delete user by id

```python

```

```shell

```

> The command returns a string

```json

```

This endpoint deletes the specified user (by loginName) from the database.

TBD - who can do this? What if this is the currently logged in user?


### HTTP Request

`DELETE /user/{id}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id (loginName) of user that needs to be deleted




## Create user by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint creates a user with the specified id.


### HTTP Request

`POST /api/v1/user/{id}`


### Query Parameters

> The Json Model Schema for the body parameter is:

```json
{
  "login": "",
  "password": "",
  "email": "",
  "fullName": "",
  "wantEmails": "",
  "groups": "",
  "oldPassword": "",
  "defaultViewPrivacy": {},
  "defaultControlPrivacy": {}
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id (loginName) of user that needs to be updated
body | [UserJson](#userjson) | body | Y | Json object with updated user information



## Get specified user value

```python

```

```shell

```

> The command returns the requested value as a JValue:

```json
{
}
```

This endpoint returns the value (`JValue`) of a specified parameter for a given user


### HTTP Request

`GET /user/{id}/{param}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of user that needs to be fetched
param | string | path | Y | The parameter to read from the object









# mission - Mission operations

This command exposes operations for browsing and searching lists of missions, and retrieving a single mission. 

## JSON Objects

### MissionJson

> The `MissionJson` object has the following Model Schema:

```json
{
  "id": 0,
  "notes": "",
  "viewPrivacy": {},
  "vehicleId": 0,
  "maxAlt": 0,
  "maxGroundspeed": 0,
  "maxAirspeed": 0,
  "maxG": 0,
  "flightDuration": 0,
  "latitude": 0,
  "longitude": 0,
  "softwareVersion": "",
  "softwareGit": "",
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "mapThumbnailURL": "",
  "viewURL": "",
  "vehicleText": "",
  "userName": "",
  "userAvatarImage": "",
  "isLive": false
}
```

The `MissionJson` object has the following parameters:

Parameter | Data Type | Required | Description
--------- | ------- | ------- | -----------
id | integer | Y | The id for the mission
notes | string |  | 
viewPrivacy | EnumVal |  | 
vehicleId | integer |  | 
maxAlt | number |  | 
maxGroundspeed | number |  | 
maxAirspeed | number |  | 
maxG | number |  | 
flightDuration | number |  | 
latitude | number |  | 
longitude | number |  | 
softwareVersion | string |  | 
softwareGit | string |  | 
createdOn | string |  | 
updatedOn | string |  | 
summaryText | string |  | 
mapThumbnailURL | string |  | 
viewURL | string |  | 
vehicleText | string |  | 
userName | string |  | 
userAvatarImage | string |  | 
isLive | boolean |  | 




## Show all missions

```python

```

```shell

```

> The command returns JSON with the `MissionJson` Model Schema:

```json
[
  {
    "id": 0,
    "notes": "",
    "viewPrivacy": {},
    "vehicleId": 0,
    "maxAlt": 0,
    "maxGroundspeed": 0,
    "maxAirspeed": 0,
    "maxG": 0,
    "flightDuration": 0,
    "latitude": 0,
    "longitude": 0,
    "softwareVersion": "",
    "softwareGit": "",
    "createdOn": "",
    "updatedOn": "",
    "summaryText": "",
    "mapThumbnailURL": "",
    "viewURL": "",
    "vehicleText": "",
    "userName": "",
    "userAvatarImage": "",
    "isLive": false
  }
]
```

This endpoint lists all missions on the service ([MissionJson](#missionjson)).

TBD - what is the format of the within parameter below.


### HTTP Request

`GET /mission/`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
live | boolean | query |   | Live flights only
completed | boolean | query |   | Completed flights only
within | string | query |   | Flights within a specified GeoJSON polygon
page_offset| integer | query | If paging, the record # to start with (use 0 at start)
page_size| integer | query | If paging, the # of records in the page
order_by| string | query | To get sorted response, the field name to sort on
order_dir| string |query  | If sorting, the optional direction. either asc or desc



## Create new mission with auto-ID

```python

```

```shell

```

> The command returns a string:

```json
{
}
```

This endpoint creates new mission that will be given a dynamically constructed ID.

TBD - if it is dynamically constructed then why is specifying an id in the body mandatory?


### HTTP Request

`PUT /mission/`


### Query Parameters

> The Json Model Schema for the body parameter ([MissionJson](#missionjson)) is:

```json
{
  "id": 0,
  "notes": "",
  "viewPrivacy": {},
  "vehicleId": 0,
  "maxAlt": 0,
  "maxGroundspeed": 0,
  "maxAirspeed": 0,
  "maxG": 0,
  "flightDuration": 0,
  "latitude": 0,
  "longitude": 0,
  "softwareVersion": "",
  "softwareGit": "",
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "mapThumbnailURL": "",
  "viewURL": "",
  "vehicleText": "",
  "userName": "",
  "userAvatarImage": "",
  "isLive": false
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
body | [MissionJson](#missionjson) | body | Y | The mission parameters




## Get live mission updates (GET)

```python

```


```shell

```

> The command returns JSON with this Model Schema:

```json
{}
```

This is an atmosphere endpoint (`AtmosphereClient`) containing an endless stream of mission update messages.

TBD - need more information on how to use this client.

### HTTP Request

`GET /mission/live`



##  Get live mission updates (POST)

```python

```


```shell

```

> The command returns JSON with this Model Schema:

```json
{}
```

This is an atmosphere endpoint (`AtmosphereClient`) containing an endless stream of mission update messages.


### HTTP Request

`POST /mission/live`





## Get recent flights for global map

```python

```


```shell

```

> The command returns JSON with the [MissionJson](#missionjson) Model Schema:

```json
[
  {
    "id": 0,
    "notes": "",
    "viewPrivacy": {},
    "vehicleId": 0,
    "maxAlt": 0,
    "maxGroundspeed": 0,
    "maxAirspeed": 0,
    "maxG": 0,
    "flightDuration": 0,
    "latitude": 0,
    "longitude": 0,
    "softwareVersion": "",
    "softwareGit": "",
    "createdOn": "",
    "updatedOn": "",
    "summaryText": "",
    "mapThumbnailURL": "",
    "viewURL": "",
    "vehicleText": "",
    "userName": "",
    "userAvatarImage": "",
    "isLive": false
  }
]
```

This endpoint gets recent flights suitable for a global map view.


### HTTP Request

`GET /mission/staticMap`




## Add a new mission

```python

```

```shell

```

> The command returns JSON with the [MissionJson](#missionjson) Model Schema:

```json
[
  {
    "id": 0,
    "notes": "",
    "viewPrivacy": {},
    "vehicleId": 0,
    "maxAlt": 0,
    "maxGroundspeed": 0,
    "maxAirspeed": 0,
    "maxG": 0,
    "flightDuration": 0,
    "latitude": 0,
    "longitude": 0,
    "softwareVersion": "",
    "softwareGit": "",
    "createdOn": "",
    "updatedOn": "",
    "summaryText": "",
    "mapThumbnailURL": "",
    "viewURL": "",
    "vehicleText": "",
    "userName": "",
    "userAvatarImage": "",
    "isLive": false
  }
]

```

This endpoint adds a new mission as a tlog, bog or log.

The endpoint is designed to facilitate easy log file uploading from GCS applications. It requires no oauth or other authentication (but you will need to use your application's api_key). You should pass in the user's login and password as query parameters.

You'll also need to pick a UUID to represent the vehicle (if your user interface allows the user to specify particular models you should associate the UUID with the model - alternatively you can open a WebView and use droneshare to let the user pick a model). If the vehicle has not previously been seen it will be created.

If you are taking advantage of the autoCreate feature, you should specify a user email address and name (so we can send them password reset emails if they forget their password).

Both multi-part file POSTs and simple posts of log files as the entire request body are supported. In the latter case the content type must be set appropriately.


### HTTP Request

`POST /mission/upload/{vehicleUUID}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
file | body | file | Y | log file as a standard html form upload POST
vehicleUUID | string | path | Y | UUID of vehicle to be have mission added (the client should pick a stable UUID)
login | string | query | Y | User login (used if not already logged-in via cookie)
password | string | query | Y | User password (used if not already logged-in via cookie)
email | string | query |  | Email address (optional, used if user creation is required)
fullName | string | query |  | User full name (optional, used if user creation is required)
autoCreate | boolean | query |  | If true a new user account will be created if required
privacy | string | query |  | The privacy setting for this flight (DEFAULT, PRIVATE, PUBLIC, SHARED, RESEARCHER)


### Error codes

HTTP Status Code | Reason
--------- | ------- 
200	Success | Payload will be a JSON array of mission objects. You probably want to show the user the viewURL for each file, but the other mission fields might also be interesting.




## Find by id

```python

```

```shell

```

> The command returns JSON with the [MissionJson](#missionjson) Model Schema:

```json
{
  "id": 0,
  "notes": "",
  "viewPrivacy": {},
  "vehicleId": 0,
  "maxAlt": 0,
  "maxGroundspeed": 0,
  "maxAirspeed": 0,
  "maxG": 0,
  "flightDuration": 0,
  "latitude": 0,
  "longitude": 0,
  "softwareVersion": "",
  "softwareGit": "",
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "mapThumbnailURL": "",
  "viewURL": "",
  "vehicleText": "",
  "userName": "",
  "userAvatarImage": "",
  "isLive": false
}
```

This endpoint returns the mission ([MissionJson](#missionjson)) for a specified id.

### HTTP Request

`GET /mission/{id}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission that needs to be fetched





## Update by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint updates a specified mission with new values.


### HTTP Request

`PUT /mission/{id}`


### Query Parameters

> The Json Model Schema for the body parameter (`MissionJson`) is:

```json
{
  "id": 0,
  "notes": "",
  "viewPrivacy": {},
  "vehicleId": 0,
  "maxAlt": 0,
  "maxGroundspeed": 0,
  "maxAirspeed": 0,
  "maxG": 0,
  "flightDuration": 0,
  "latitude": 0,
  "longitude": 0,
  "softwareVersion": "",
  "softwareGit": "",
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "mapThumbnailURL": "",
  "viewURL": "",
  "vehicleText": "",
  "userName": "",
  "userAvatarImage": "",
  "isLive": false
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission that needs to be updated
body | [MissionJson](#missionjson) | body | Y | Json object with mission information




## Delete by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint deletes the mission with the specified id.


### HTTP Request

`DELETE /mission/{id}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission that needs to be deleted




## Create by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint creates a new mission object with a specified id.


### HTTP Request

`POST /mission/{id}`


### Query Parameters

> The Json Model Schema for the body parameter (`MissionJson`) is:

```json
{
  "id": 0,
  "notes": "",
  "viewPrivacy": {},
  "vehicleId": 0,
  "maxAlt": 0,
  "maxGroundspeed": 0,
  "maxAirspeed": 0,
  "maxG": 0,
  "flightDuration": 0,
  "latitude": 0,
  "longitude": 0,
  "softwareVersion": "",
  "softwareGit": "",
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "mapThumbnailURL": "",
  "viewURL": "",
  "vehicleText": "",
  "userName": "",
  "userAvatarImage": "",
  "isLive": false
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission that needs to be created
body | [MissionJson](#missionjson) | body | Y | Json object with mission information




## Get the analysis.json by id

```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
  "obj": [
    {
      "_1": {},
      "_2": {}
    }
  ]
}
```

> And this Model:

```json
JObject {
  obj (array[Tuple2[String, JValue]])
 }

Tuple2[String, JValue] {
  _1 (Object),
  _2 (Object)
}

Object {
}
```

This endpoint gets the **analysis.json** for the specified mission.


### HTTP Request

`GET /mission/{id}/analysis.json`


The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read





## Get the dseries by id

```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
[
  {
    "obj": [
      {
        "_1": {},
        "_2": {}
      }
    ]
  }
]
```

> And this Model:

```json
JObject {
  obj (array[Tuple2[String, JValue]])
 }

Tuple2[String, JValue] {
  _1 (Object),
  _2 (Object)
}
Object {
 }
```

This endpoint gets the dseries for the specified mission.


### HTTP Request

`GET /mission/{id}/dseries`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read




##  Get the messages.geo.json by id


```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
[
  {
    "obj": [
      {
        "_1": {},
        "_2": {}
      }
    ]
  }
]
```

> And this Model:

```json
JObject {
  obj (array[Tuple2[String, JValue]])
 }

Tuple2[String, JValue] {
  _1 (Object),
  _2 (Object)
}
Object {
 }
```

This endpoint gets the **messages.geo.json** for the specified mission.


### HTTP Request

`GET /mission/{id}/messages.geo.json`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read







## Get the messages.gmaps.kmz by id

```python

```

```shell

```

> The command returns an `array[string]`


This endpoint gets the **messages.gmaps.kmz** for the specified mission.


### HTTP Request

`GET /mission/{id}/messages.gmaps.kmz`

### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read





##  Get the messages.json for the specified mission

```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
  "modelType": "",
  "messages": [
    {
      "t": 0,
      "typ": "",
      "fld": [
        ""
      ]
    }
  ]
}
```

> And this Model:

```json
MessageHeader {
  modelType (string),
  messages (array[MessageJson])
}

MessageJson {
  t (integer),
  typ (string),
  fld (array[string])
}
```

This endpoint gets the **messages.json** for the specified mission.


### HTTP Request

`GET /mission/{id}/messages.json`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read





## Get the messages.kml by id

```python

```

```shell

```

> The command returns an `array[string]`


This endpoint gets the **messages.kml** for the specified mission.


### HTTP Request

`GET /mission/{id}/messages.kml`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read





##  Get the messages.kmz by id

```python

```

```shell

```

> The command returns an `array[string]`

This endpoint gets the **messages.kmz** for the specified mission.


### HTTP Request

`GET /mission/{id}/messages.kmz`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read




## Get the messages.tlog by id

```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
  "status": {
    "code": 0,
    "message": ""
  },
  "body": {},
  "headers": [
    ""
  ]
}
```

> With this Model:

```json
ActionResult {
  status (ResponseStatus),
  body (Object),
  headers (array[string])
}

ResponseStatus {
  code (integer),
  message (string)
}

Object {
}
```

This endpoint gets the **messages.tlog** for the specified mission.


### HTTP Request

`GET /mission/{id}/messages.tlog`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read




## Set the openTicket on id.

```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
}
```

This endpoint sets the openTicket on a specified mission.

TBD - What is an openticket?


### HTTP Request

`POST /mission/{id}/openTicket`


### Query Parameters

> The Json Model Schema for the body parameter (`openTicket`) is:

```json
{
  "extraInfo": "",
  "priority": ""
}
```


The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be appended
openTicket | body | openTicket | Y | Id of mission to be read

The `openTicket` data type has the following parameters

Parameter | Data Type | Required | Description
--------- | ------- | ------- | -----------
extraInfo | string | Y | 
priority | string |  | 




## Get the parameters.complete by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint gets the **parameters.complete** for the specified mission.


### HTTP Request

`GET /mission/{id}/parameters.complete`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read





## Get the parameters.json by id

REMOVEME_WHEN_DONE check query parameters and error codes
```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
[
  {
    "id": "",
    "range": [
      {}
    ],
    "value": "",
    "doc": "",
    "rangeOk": false
  }
]
```

> With this model:

```json
ParameterJson {
  id (string),
  range (array[Object], optional),
  value (string),
  doc (string),
  rangeOk (boolean)
}

Object {
}
```

This endpoint gets the **parameters.jso**n for the specified mission.


### HTTP Request

`GET /mission/{id}/parameters.json`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read




## Get the parameters.share by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint gets the **parameters.share** for the specified mission.


### HTTP Request

`GET /mission/{id}/parameters.share`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission to be read




##  Get parameter from a mission

```python

```

```shell

```

> The command returns JSON (`JValue`) with this Model Schema:

```json
{}
```

This endpoint gets a specific parameter from a given mission.


### HTTP Request

`GET /mission/{id}/{param}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of mission that needs to be fetched
param | string | path | Y | The parameter to read from the object









# vehicle - Vehicle operations

This command exposes operations for browsing and searching lists of vehicles, and retrieving single vehicles. 

## JSON Objects

### VehicleJson

> The `VehicleJson` object has the following Model Schema:

```json
{
  "uuid": {
    "mostSigBits": 0,
    "leastSigBits": 0
  },
  "name": "",
  "id": 0,
  "userId": 0,
  "manufacturer": "",
  "vehicleType": "",
  "autopilotType": "",
  "viewPrivacy": {},
  "controlPrivacy": {},
  "missions": [
    {}
  ],
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "userName": ""
}
```

The `VehicleJson` object has the following parameters:

Parameter | Data Type | Required | Description
--------- | ------- | ------- | -----------
uuid | UUID | | 
name | string |  | 
id | integer |  | 
userId | integer |  | 
manufacturer | string |  | 
vehicleType | string |  | 
autopilotType | string |  | 
viewPrivacy | EnumVal |  | 
controlPrivacy | EnumVal |  | 
missions | array[JValue] |  | 
createdOn | string |  | 
updatedOn | string |  | 
summaryText | string |  | 
userName | string |  | 


The `UUID` object has the following parameters:

Parameter | Data Type | Required | Description
--------- | ------- | ------- | -----------
mostSigBits | integer |  | 
leastSigBits | integer |  | 



## Show all vehicles

```python
import requests

url = "http://api.droneshare.com/api/v1/vehicle/"

headers = {'authorization': 'DroneApi apikey="89b511b1.d884d1cb57306e63925fcc07d032f2af"'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```


```shell

```

> The command returns JSON with the [VehicleJson](#vehiclejson) Model Schema:

```json
[
  {
    "uuid": {
      "mostSigBits": 0,
      "leastSigBits": 0
    },
    "name": "",
    "id": 0,
    "userId": 0,
    "manufacturer": "",
    "vehicleType": "",
    "autopilotType": "",
    "viewPrivacy": {},
    "controlPrivacy": {},
    "missions": [
      {}
    ],
    "createdOn": "",
    "updatedOn": "",
    "summaryText": "",
    "userName": ""
  }
]
```

This endpoint retrieves all vehicles.


### HTTP Request

`GET /vehicle/`


Parameter | Parameter type | Data type | Description
--------- | ------- | ------- | -----------
page_offset| query | integer | If paging, the record # to start with (use 0 at start)
page_size| query | integer | If paging, the # of records in the page
order_by| query | string | To get sorted response, the field name to sort on
order_dir| query | string | If sorting, the optional direction. either asc or desc





## Create a new object with auto-ID


```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
}
```

This endpoint creates a new vehicle record with a dynamically constructed ID.


### HTTP Request

`PUT /vehicle/`


### Query Parameters


> The Json Model Schema for the body parameter ([VehicleJson](#vehiclejson)) is:

```json
{
  "uuid": {
    "mostSigBits": 0,
    "leastSigBits": 0
  },
  "name": "",
  "id": 0,
  "userId": 0,
  "manufacturer": "",
  "vehicleType": "",
  "autopilotType": "",
  "viewPrivacy": {},
  "controlPrivacy": {},
  "missions": [
    {}
  ],
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "userName": ""
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
body | [VehicleJson](#vehiclejson) | body | Y | The vehicle parameters





## Find by id

```python

```

```shell

```

> The command returns JSON with this Model Schema:

```json
{
  "uuid": {
    "mostSigBits": 0,
    "leastSigBits": 0
  },
  "name": "",
  "id": 0,
  "userId": 0,
  "manufacturer": "",
  "vehicleType": "",
  "autopilotType": "",
  "viewPrivacy": {},
  "controlPrivacy": {},
  "missions": [
    {}
  ],
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "userName": ""
}
```

This endpoint gets a vehicle with the specified ID.

TBD. Is this vehicle a global id or associated with the particular user?


### HTTP Request

`GET /vehicle/{id}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle that needs to be fetched





## Update by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint updates the information in the vehicle record with the specified id.


### HTTP Request

`PUT /vehicle/{id}`


### Query Parameters

> The Json Model Schema for the body parameter ([VehicleJson](#vehiclejson)) is:

```json
{
  "uuid": {
    "mostSigBits": 0,
    "leastSigBits": 0
  },
  "name": "",
  "id": 0,
  "userId": 0,
  "manufacturer": "",
  "vehicleType": "",
  "autopilotType": "",
  "viewPrivacy": {},
  "controlPrivacy": {},
  "missions": [
    {}
  ],
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "userName": ""
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
body | [VehicleJson](#vehiclejson) | body | Y | The vehicle parameters
id | string | path | Y | Id of vehicle that needs to be updated




## Delete by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint deletes the vehicle with the specified id.


### HTTP Request

`DELETE /vehicle/{id}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle that needs to be deleted.





## Create by id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint creates a new vehicle with the specified id.


### HTTP Request

`POST /api/v1/vehicle/{id}`


### Query Parameters

> The Json Model Schema for the body parameter ([VehicleJson](#vehiclejson)) is:

```json
{
  "uuid": {
    "mostSigBits": 0,
    "leastSigBits": 0
  },
  "name": "",
  "id": 0,
  "userId": 0,
  "manufacturer": "",
  "vehicleType": "",
  "autopilotType": "",
  "viewPrivacy": {},
  "controlPrivacy": {},
  "missions": [
    {}
  ],
  "createdOn": "",
  "updatedOn": "",
  "summaryText": "",
  "userName": ""
}
```

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
body | [VehicleJson](#vehiclejson) | body | Y | The vehicle parameters
id | string | path | Y | Id of vehicle that needs to be created





## Get the airspeed for id

```python

```

```shell

```

> The command returns a number (the airspeed).

This endpoint gets the airspeed for the specified vehicle.

TBD. What are the units?


### HTTP Request

`GET /vehicle/{id}/airspeed`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle to be read.




## Get the batterySOC for id

```python

```

```shell

```

> The command returns a number (the battery soc).


This endpoint gets the batterSOC for the specified vehicle.


### HTTP Request

`GET /vehicle/{id}/batterySOC`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle to be read




## Get the battery voltage for id

```python

```

```shell

```

> The command returns a number (the battery voltage).

This endpoint gets the battery voltage for the specified vehicle.


### HTTP Request

`GET /vehicle/{id}/batteryVolt`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle to be read





##  Get the groundspeed for id

```python

```

```shell

```

> The command returns a number (the groundspeed).

This endpoint gets the groundspeed for the specified vehicle.


### HTTP Request

`GET /vehicle/{id}/groundspeed`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle to be read





## Add a new mission

```python

```

```shell

```

> The command returns JSON with the [VehicleJson](#vehiclejson) Model Schema:

```json
[
  {
    "uuid": {
      "mostSigBits": 0,
      "leastSigBits": 0
    },
    "name": "",
    "id": 0,
    "userId": 0,
    "manufacturer": "",
    "vehicleType": "",
    "autopilotType": "",
    "viewPrivacy": {},
    "controlPrivacy": {},
    "missions": [
      {}
    ],
    "createdOn": "",
    "updatedOn": "",
    "summaryText": "",
    "userName": ""
  }
]
```

This endpoint adds a new mission (as a tlog, bog or log).


### HTTP Request

`POST /vehicle/{id}/missions`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
file | file | body | Y | Log file as a standard html form upload POST
id | string | path | Y | Id of vehicle to be have mission added





## Get the mode for id

```python

```

```shell

```

> The command returns a string for the current mode.

This endpoint gets the mode for the specified vehicle.


### HTTP Request

`GET /vehicle/{id}/mode`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle to be read





##  Set the mode on id

```python

```

```shell

```

> The command returns a string.

```json

```

This endpoint sets the mode on specified vehicle.

TBD 
- What is the description for the body parameters and what needs to be in it?
- What is the string returned


### HTTP Request

`PUT /vehicle/{id}/mode`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle to be changed
body | string | body | Y | 
mode | string | body | Y | New value for the mode



## Get the rcChannels for id

```python

```

```shell

```

> The command returns and `array[integer]` with the channel information.

This endpoint gets the rcChannels for the specified vehicle.


### HTTP Request

`GET /vehicle/{id}/rcChannels`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle to be read





## Set the rcOverrides on id

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint set the rcOverrides on a specified vehicle.

TBD What is the string that is returned.
TBD What is the body here. Could just be the rcOverrides but it is not clear


### HTTP Request

`PUT /vehicle/{id}/rcOverrides`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle to be changed
body | array[integer] | body | Y | 
rcOverrides | array[integer] | body | Y | New value for the rcOverrides





## Get a parameter from a vehicle

```python

```

```shell

```

> The command returns a `JValue` with the value of the parameter:

```json
{}
```

This endpoint gets a specified parameter from a given vehicle.


### HTTP Request

`GET /vehicle/{id}/{param}`


### Query Parameters

The query parameters are:

Parameter | Data Type | Parameter Type | Required | Description
--------- | ------- | ------- | ------- | -----------
id | string | path | Y | Id of vehicle that needs to be fetched
param | string | path | Y | The parameter to read from the object








# admin - Administrator operations

This API performs a number of administrator operations.

## Get debugging information

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint returns debugging information.

TBD - what debugging information? What is in the string.


### HTTP Request

`GET /admin/debugInfo`





## Live stream of server log messages (GET)

```python

```

```shell

```

> The command returns JSON with an `AtmosphereClient` Model Schema:

```json
{}
```

This endpoint returns atmosphere endpoint container (`AtmosphereClient`) server log messages.


### HTTP Request

`GET /admin/log`




## Live stream of server log messages (POST)

```python

```

```shell

```

> The command returns JSON with an `AtmosphereClient` Model Schema:

```json
{}
```

This endpoint returns atmosphere endpoint container (`AtmosphereClient`) server log messages.

### HTTP Request

`POST /admin/log`





## Simulate a flight (full)

```python

```

```shell

```

> The command returns a string.

```json

```

This endpoint simulates a flight.

TBD - what is this all about?
TBD - what is in the returned string


### HTTP Request

`POST /admin/sim/full`




##  Simulate a flight (huge)

```python

```

```shell

```

> The command returns a string.

```json

```

This endpoint simulates a flight.

TBD - what is this all about?
TBD - what is in the returned string


### HTTP Request

`POST /admin/sim/huge`






##  Simulate a flight (stop)

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint simulates a flight.

TBD - what does this really do? Stop the sim?


### HTTP Request

`POST /admin/sim/std/stopAll`






## Simulate a flight (num vehicles/time)

```python

```

```shell

```

> The command returns a string:

```json

```

This endpoint simulates a flight.

TBD - what does this really do? Run a sim with a specified number of vehciles and seconds


### HTTP Request

`POST /admin/sim/std/{numVehicles}/{numSecs}`




