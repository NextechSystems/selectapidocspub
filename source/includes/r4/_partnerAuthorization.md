# Partner Authorization

## Partner Authorization Overview ##

Nextech's implementation of the FHIR® standard is protected by the [OAuth 2.0 standard](https://www.rfc-editor.org/rfc/rfc6749) for authenticating requests. All API requests are authenticated by passing a Bearer token in the Authorization Header, which can be obtained via your Nextech-provided credentials (see the "Registration" section below).

### Required Headers ###
The following values are required in the header for every request:

| Name | Description | Required? |
| ---- | ----------- | --------- |
| Authorization | Every request requires a Bearer token `Bearer {access_token}` | Yes |
| nx-practice-id | The unique identifier for a practice | Yes |

### Registration ### 
Before you can start using the Nextech API, you must go through our registration process. If you're interested in API access for your practice, please contact us [here](http://landing.nextech.com/developers-portal-registration-form). Upon completion of the registration process, Nextech will provide you with credentials that are necessary for proper authorization with the Nextech API. **These credentials will expire on your first login and must be reset through Microsoft [here] (http://portal.azure.com/).**

### Request Access Token ###
Access tokens are used to make API requests on behalf of a user. These tokens are short-lived (1 hour by default) but should be kept confidential in transit and in storage. A `access_token` and `refresh_token` pair is issued when requesting an access token.

**HTTP Request**  
`POST https://login.microsoftonline.com/nextech-api.com/oauth2/token`

| Parameter | Description |
| --------- | ----------- |
| grant_type | Use `password` (Resource owner credentials grant) |
| client_id | Application ID |
| username | Resource owner username |

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


### Authorization With Postman ###

Postman makes it easy to acquire OAuth 2.0 access tokens. Use the information listed below for obtaining a token via the `authorization_code` grant type. When requesting a new token, you will be redirected to the _Auth URL_ listed below where you can enter your user credentials to authenticate. 

| Field | Value |
| ----- | ----- |
| Auth URL | `https://login.microsoftonline.com/nextech-api.com/oauth2/authorize?resource=https%3A%2F%2Fselect.nextech-api.com%2Fapi` |
| Access Token URL | `https://login.microsoftonline.com/nextech-api.com/oauth2/token` |
| Callback URL | `https://www.getpostman.com/oauth2/callback` |
| Client ID | Your application ID |
| Grant Type | `Authorization Code` |
| Client Authentication | `Send client credentials in body` |
