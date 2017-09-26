# Authentication
## Request Access Token
Nextech's implementation of the FHIR® standard is protected by the [OAuth 2.0 standard](https://oauth.net/2/) for authenticating requests.  Every API request requires a Bearer token to be passed in the Authorization Header.

```Authorization: Bearer {access_token}```

### HTTP Request
`POST https://login.microsoftonline.com/a5f8392a-a68f-4d74-a353-aefc87f29848/oauth2/token`

| Parameter | Description |
| --------- | ----------- |
| grant_type | Use `password` (Resource owner credentials grant) |
| client_id | Application ID |
| client_secret | Application secret |
| username | Resource owner username |
| password | Resource owner password |
| resource | The app to consume the token |

### Response Parameters

| Parameter | Description |
| --------- | ----------- |
| token_type | Always `Bearer` |
| scope | Always `user_impersonation` |
| expires_in | The lifetime of the access token, in seconds. Default 3600 |
| access_token | The bearer token used in the `Authorization` header for subsquent requests |
| refresh_token | A long-lived token (14 days) used to renew expired access tokens without providing user credentials |

## Refresh Access Token
Refresh tokens are used to renew an expired access token without providing user credentials. A `access_token` and `refresh_token` pair is issued when requesting an access token using the resource owner credentials grant. A new pair is also generated when using the `refresh_token` grant type. 

### HTTP Request
`POST https://login.microsoftonline.com/a5f8392a-a68f-4d74-a353-aefc87f29848/oauth2/token`

| Parameter | Description |
| --------- | ----------- |
| grant_type | Always `refresh_token` |
| client_id | Application ID |
| client_secret | Application secret |
| refresh_token | A valid refresh token |

### Response Parameters

| Parameter | Description |
| --------- | ----------- |
| token_type | Always `Bearer` |
| scope | Always `user_impersonation` |
| expires_in | The lifetime of the access token, in seconds. Default 3600 |
| access_token | The bearer token used in the `Authorization` header for subsquent requests |
| refresh_token | A long-lived token (14 days) used to renew expired access tokens without providing user credentials |