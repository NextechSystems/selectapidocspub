# Getting Started #

All API requests are performed over HTTPS. Although the [FHIR® standard](https://www.hl7.org/fhir/index.html) supports both JSON and XML, this API currently only supports JSON.  Therefore any type explicitly defined in the request's `Accept` header will be ignored.

Before you can access the Nextech API you must have the proper credentials to authenticate. These credentials will be provided to you by your Nextech representative.  

**API Limitations**  
- Users of the Nextech API are restricted to a limit of 5,000 API calls per day combined across all applications for a single client  
- Nextech is not responsible for the development or maintenance of any third-party application

**API Endpoint**  
`https://select.nextech-api.com/api`

The following values are required in the Header for every request...

| Name | Description | Required? |
| ---- | ----------- | --------- |
| Authorization | Every request requires a Bearer token `Bearer {access_token}` | Yes |
| nx-practice-id | The unique identifier for a practice | Yes |

## Authentication ##

Nextech's implementation of the FHIR® standard is protected by the [OAuth 2.0 standard](https://oauth.net/2/) for authenticating requests.  All API requests are authenticated by passing a Bearer token in the Authorization Header.

```Authorization: Bearer {access_token}```

### Request Access Token ###
Access tokens are used to make API requests on behalf of a user. These tokens are short-lived (1 hour by default) but should be kept confidential in transit and in storage. A `access_token` and `refresh_token` pair is issued when requesting an access token.

**HTTP Request**  
`POST https://login.microsoftonline.com/nextech-api.com/oauth2/token`

| Parameter | Description |
| --------- | ----------- |
| grant_type | Use `password` (Resource owner credentials grant) |
| client_id | Application ID |
| username | Resource owner username |
| password | Resource owner password |
| resource | The app to consume the token |

**Response Parameters**

| Parameter | Description |
| --------- | ----------- |
| token_type | Always `Bearer` |
| scope | Always `user_impersonation` |
| expires_in | The lifetime of the access token, in seconds. Default 3600 |
| access_token | The bearer token used in the `Authorization` header for subsquent requests |
| refresh_token | A long-lived token (14 days) used to renew expired access tokens without providing user credentials |

### Refresh Access Token ###
Refresh tokens are used to renew an expired access token without providing user credentials. A `access_token` and `refresh_token` pair is issued when requesting an access token using the resource owner credentials grant. A new pair is also generated when using the `refresh_token` grant type. 

**HTTP Request**  
`POST https://login.microsoftonline.com/nextech-api.com/oauth2/token`

| Parameter | Description |
| --------- | ----------- |
| grant_type | Always `refresh_token` |
| client_id | Application ID |
| refresh_token | A valid refresh token |

**Response Parameters**

| Parameter | Description |
| --------- | ----------- |
| token_type | Always `Bearer` |
| scope | Always `user_impersonation` |
| expires_in | The lifetime of the access token, in seconds. Default 3600 |
| access_token | The bearer token used in the `Authorization` header for subsquent requests |
| refresh_token | A long-lived token (14 days) used to renew expired access tokens without providing user credentials |

## Using Postman ##
To help you get started, here's a collection of sample API requests in Postman. You can find more information on making API requests using Postman [here](https://www.getpostman.com/docs/postman/sending_api_requests/requests).

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/899edff2cda90cba5159)

<aside class="notice">
You must have been provided API credentials and Practice ID(s) to use these examples.
</aside>

### Authorization ###

Postman makes it easy to acquire OAuth 2.0 access tokens. Use the information listed below for obtaining a token via the `authorization_code` grant type. When requesting a new token, you will be redirected to the _Auth URL_ listed below where you can enter your user credentials to authenticate. 

| Field | Value |
| ----- | ----- |
| Auth URL | `https://login.microsoftonline.com/nextech-api.com/oauth2/authorize?resource=https%3A%2F%2Fselect.nextech-api.com%2Fapi` |
| Access Token URL | `https://login.microsoftonline.com/nextech-api.com/oauth2/token` |
| Callback URL | `https://www.getpostman.com/oauth2/callback` |
| Client ID | Your application ID |
| Grant Type | `Authorization Code` |
| Client Authentication | `Send client credentials in body` |

## Searching ##

Searches may be performed via HTTPS calls to the API where supported. 

A search is executed by performing a `GET` operation in the RESTful framework   
`GET https://select.nextech-api.com/api/[type]?[field1][:modifier1]=[value1]&[field2][:modifier2]=[value2]...`   
where \[type\] refers to a resource such as Patient or Appointment followed by one or more query filters and optional modifiers.

* Matching is always case-insensitive and always ignores whitespace before and after the data.
* The default search attempts to match with just the start of the data.

### Multiple Values on One Field ###

To search for a field that meets at least one of several values, each value should be specified and separated by a comma.

**Example: Get patients who live in several nearby cities**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?address-postalcode=33609,33625,33647
</pre>
&nbsp;

### Multiple Fields ###

To search for multiple fields that all must meet certain criteria, each field should be specified and separated by an ampersand.

**Example: Get booked appointments for one day**
<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?date=2015-03-04&status=booked
</pre>
&nbsp;


### Modifiers ###

A modifier defines how a search match should be performed for a field. A modifier must appear after the field name with a preceeding colon followed by the modifier name.

| Modifier | Description |
| --------- | ----------- |
| exact | The value must match the data exactly |
| contains | The data must contain the value |

**Example: Get all patients whose last name is Smith**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?family:exact=Smith
</pre>
&nbsp;

**Example: Get all patients whose last name contains the text "mit"**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?family:contains=mit
</pre>
&nbsp;

### Operators ###

Numeric and date values can be combined with operators to search on ranges of values. The following operators are supported:

| Operator | Description |
| --------- | ----------- |
| gt | Greater Than |
| ge | Greater Than or Equal to |
| lt | Less Than |
| le | Less Than or Equal to |
| eq | Equals |
| ne | Not Equal to |

**Example: Get the patients with chart numbers between and including 100 and 200**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?identifier=ge100&identifier=le200
</pre>
&nbsp;

**Example: Get appointments for the month of March 2017**
<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?date=ge2017-03-01&date=lt2017-04-01
</pre>
&nbsp;

### Search Parameter Types ###

#### String ####

When matching a simple text string with data, the match is always case-insensitive and always ignores whitespace before and after the data. The default search attempts to match just the start of the data, and you may use a modifier to force an exact match or a match where the data contains the string.

**Example: Get all patients whose last name begins with Smith**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?family=Smith
</pre>
&nbsp;

#### Number ####

By default, exact matches are performed in numeric searches. You may use operators to specify a numeric range.

**Example: Get the patient with chart number 3442**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?identifier=3442
</pre>
&nbsp;

#### Date ####

By default, exact matches are performed in date searches. You may use operators to specify a date range.

**Example: Get appointments for the month of October 2016**
<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?date=ge2016-10-01&date=lt2017-11-01
</pre>
&nbsp;

#### Human Name ####

Some resources have abstract fields which contain a first name, last name, prefix and suffix. When searching on names, each of those fields are searched individually. The way those fields are matched are consistent with how String searches work, and modifiers may be used to change how the matching works.

**Example: Get the patients whose first name, last name, prefix or suffix begins with Doe**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?name=doe
</pre>
&nbsp;

#### Address ####

Some resources have abstract fields which contain an Address 1, Address 2, City, State and Postal Code field. When searching on address, each of these fields are searched individually. The way those fields are matched are consistent with how String searches work, and modifiers may be used to change how the matching works.

**Example: Get the patients whose Address 1, Address 2, City, State or Zip code begins with 1500**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?address=1500
</pre>
&nbsp;

## Writing ##

Data writes may be performed via HTTPS calls to the API where supported. 

A write is executed by performing a `PUT` operation in the RESTful framework
`PUT https://select.nextech-api.com/api/{resource}/{identifier}`
where `{resource}` refers to a resource such as Patient or Appointment, `{identifier}` is the unique identifier of the resource and the body of the request describes a resource and which fields to add or change. This example request path and body would confirm an appointment with the ID 3384:

**Example**
<pre class="center-column">
`PUT https://select.nextech-api.com/api/Appointment/3384`
</pre>
<pre class="center-column">
`{ 
    "status": "booked" 
}`
</pre>
&nbsp;

## Pagination ##

When a search results in multiple matches, the first ten matches ordered by entered date are returned by default. Included in the result are links to the first set of matches, the following set of matches, the previous set of matches and the last set of matches.

You may overide the number of matches returned, up to fifty, by including `_count={number}` in your search. 

`GET http://select.nextech-api.com/api/Appointment?_count=25`

<aside class="notice">
Search results are limited to 50 matches per page.
</aside>

## Response Codes ##

The Nextech Select APIs use the standard HTTP response codes to indicate success or failure of an API request.

| Code | Description |
| ---- | ----------- |
| 200 | OK - Successful request |
| 400 | Bad Request - The request is missing information or is malformed |
| 403 | Forbidden - The request is valid, but the server is refusing action |
| 404 | Not Found - The requested resource cannot be found |
| 429 | Too Many Requests - The user has sent too many requests in a given amount of time |
| 500 | Internal Server Error - We had a problem with our server |
