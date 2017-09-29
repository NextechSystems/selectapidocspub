# Getting Started #

All API requests are performed over HTTPS. Although the [FHIR® standard](https://www.hl7.org/fhir/index.html) supports both JSON and XML, this API currently only supports JSON.  Therefore any type explicitly defined in the request's `Accept` header will be ignored.

Before you can access the Nextech API you must have the proper credentials to authenticate. These credentials will be provided to you by your Nextech representative.  


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
| client_secret | Application secret |
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
| client_secret | Application secret |
| refresh_token | A valid refresh token |

**Response Parameters**

| Parameter | Description |
| --------- | ----------- |
| token_type | Always `Bearer` |
| scope | Always `user_impersonation` |
| expires_in | The lifetime of the access token, in seconds. Default 3600 |
| access_token | The bearer token used in the `Authorization` header for subsquent requests |
| refresh_token | A long-lived token (14 days) used to renew expired access tokens without providing user credentials |

## Search Parameters ##

Searches may be performed via HTTPS calls to the API where supported. 

A search is executed by performing a `GET` operation in the RESTful framework   
`GET https://select.nextech-api.com/api/[type]?[field1]=[value1]&[field2]=[value2]...`   
where \[type\] refers to a resource such as Patient or Appointment followed by one or more query filters.  

**Example**
<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?identifier=3442
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?family=Smith
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?address-city=Tampa&address-state=FL
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
| 500 | Internal Server Error - We had a problem with our server |

## Using Postman ##
To help you get started, here's a collection of sample API requests in Postman.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/899edff2cda90cba5159)

<aside class="notice">
You must have been provided API credentials and Practice ID(s) to use these examples.
</aside>