# Authentication #

Nextech's implementation of the FHIR® standard is protected by the [OAuth 2.0 standard](https://oauth.net/2/) for authenticating requests.  All API requests are authenticated by passing a Bearer token in the Authorization Header. There are two authentication models we use. We have a Partner Authentication and User Authentication.

```Authorization: Bearer {access_token}```
## Partner Authentication ##

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

## User Authentication ##
User Authentication uses the MyPatientVisit portal to grant access to third party applications. These applications will need to be registered with Nextech.

### Required Parameters ###
| Parameter | Description |
| --------- | ----------- |
| grant_type | Always ` ` |
| client_id | Client ID given by Nextech |
| client_secret | a secret provided by Nextech |
| Scopes | A space delimited list of resources the application requires access to|
| Audience | A URI indicating where the token intends to be used |

### Authenticating With Postman ###
 Postman's authentication makes generating your first token a breeze. 
1. For a given postman collection go to the Authorization tab
1. Set Authorization to Oauth 2.0. This should give you additional fields to fill out
1. Header Prefix should be set to "Bearer"
1. Grant type ahould be set to Authorization code with PKCE
1. Auth URL should be set to https://mypatientvisit-sts-dev.azurewebsites.net/connect/authorize
1. Access Token URL should be set to https://mypatientvisit-sts-dev.azurewebsites.net/connect/token
1. Client ID should be set to the value given to you by Nextech
1. Secret should be set to the value given to you by Nextech. NOTE: This should be stored securely and access to it highly limited
1. Code Challenge Method should be SHA-256
1. Scopes should contain all needed scopes. At a minimum this should be "launch/patient openid fhirUser"
1. Audience can be found under the *Advanced Options* tab and should be set to https://nxpartnerapi-dev.azurewebsites.net/api/r4

Once these fields are filled out and the authentication request is made your browser should open up to a login screen. The user will then login via their MyPatientVisit credentals. They will Select which practice and patient they are granting access to, and then they will verify the scopes. Once this is done you will have a callback to Postman (check browser popup settings and possibly try changing your default browser if that fails). When Postman receives this callback it will populate the access token. 

### Using the Authentication Token ###
To use the authentication token you will need to add an Authorization header, then set the value to "Bearer <token>" where <token> represents your token. No other headers are required and **trying to set headers like nx-practice-id will cause the request to fail even if the token is valid for that practice.**

### Scopes ###
The full list of supported scopes:
launch/patient openid fhirUser offline_access patient/Medication.read patient/AllergyIntolerance.read patient/CarePlan.read patient/CareTeam.read patient/Condition.read patient/Device.read patient/DiagnosticReport.read patient/DocumentReference.read patient/Encounter.read patient/Goal.read patient/Immunization.read patient/Location.read patient/MedicationRequest.read patient/Observation.read patient/Organization.read patient/Patient.read patient/Practitioner.read patient/Procedure.read patient/Provenance.read patient/PractitionerRole.read

Most of the scopes map to a specific endpoint. So for example the patient/DocumentReference.read scope is required to make a GET /DocumentReference request

