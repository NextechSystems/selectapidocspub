# Authentication
Nextech's implementation of the FHIR® standard is protected by the [OAuth 2.0 standard](https://oauth.net/2/) for authenticating requests.  Every API request requires a Bearer token to be passed in the Authorization Header.

```Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng...```

### Request Authorization
To obtain a Bearer token, the user must first request authorization using a registered app's client identifier.

```https://login.microsoftonline.com/mdintellesys.com/oauth2/authorize?response_type=code&resource=https%3A%2F%2Fmdintellesys.com%2FPartnerAPI&client_id=[client_id] ```

The user will be asked to log in using their credentials.  Upon first login, they will be asked to authorize the use of the application.  If they don't have credentials, they will need to create an account which will verify their identity. 

Upon successful authentication, an authorization code will be included as the value of the `code` parameter in the redirect URL.  This code, along with the client secret will be included in the request to get an access token.

### Request Access Token
```POST https://login.microsoftonline.com/mdintellesys.com/oauth2/token ```

Add the following parameters as a `x-www-form-urlencoded` query string to the request body:
```
grant_type: authorization_code
client_id: [client_id]
code: [authorization_code]
client_secret: [client_secret]
```

The response includes the `access_token` which should be included in the Authorization header when making an API request.
```
{
  "token_type": "Bearer",
  "scope": "user_impersonation",
  "expires_in": "3599",
  "ext_expires_in": "0",
  "expires_on": "1495481979",
  "not_before": "1495478079",
  "resource": "https://mdintellesys.com/PartnerAPI",
  "access_token": "eyJ0eXAiOiJKV1QiLC..."
  "refresh_token": "AQABAAAAAABnfiG-m..."
  "id_token": "eyJ0eXAiOiJKV1QiLCJh..."
}
  ``` 