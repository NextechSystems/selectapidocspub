# SMART App Authorization

## SMART on FHIR Technology Overview ##
- [OAuth 2.0 standard](https://www.rfc-editor.org/rfc/rfc6749)
- [OpenID Connect](https://openid.net/connect/)
- [FHIR R4](https://hl7.org/fhir/R4/)

## SMART on FHIR Authorization Overview ##

SMART applications are able to access through SMART on FHIR authorization standards.

* For an individual patient or practitioner's data, the application can follow the [SMART App Launch 1.0.0 specification](https://www.hl7.org/fhir/smart-app-launch/1.0.0/index.html#smart-authorization--fhir-access-overview).
* For the information from an entire practice via background system apps, authorization is granted  via the [SMART Backend Services Authorization (STU 1.0.1) specification](http://hl7.org/fhir/uv/bulkdata/STU1.0.1/authorization/index.html).
	* Additionally, if a System-level application needs to access Bulk FHIR export functionality, follow the client-specific guidance in the [FHIR Bulk Data Access (Flat FHIR, STU 1.0.1) specification](http://hl7.org/fhir/uv/bulkdata/STU1.0.1/) specification and the [System apps](#system-apps) section of this page's documentation for guidance.

### Registration ###
In order create a SMART application that can access FHIR resources from the Nextech API, the application must first be registered with Nextech, and issued required authentication information. Visit [here](http://landing.nextech.com/developers-portal-registration-form) to fill out a registration form for your app.
There are a few different pieces of information that will need to be provided to Nextech upon app registration, which vary depending on the SMART app's use case:
- The name of the practice that utilizes Nextech software that you would like your app to integrate with
- The name of your app
- A brief description of your app
- Whether or not your app is capable of securely storing a secret
- Whether your app is web-based
- Whether your app going to be used by patients, practitioners, or if it's instead a secure background service with no user interaction
  - If the app is going to be used by practitioners, you will need to specify whether the app needs to provide the practitioner access to all patient data, or just a single patient at a time
  - Additionally, practitioner apps will need to provide a "launch URL" (see [here](https://www.hl7.org/fhir/smart-app-launch/1.0.0/index.html#ehr-launch-sequence) for more details) that the app can be launched from

If your app is capable of securely storing a secret, it is considered to be a **confidential** client, and will be issued a client secret, along with a client ID, after the Nextech app registration process has completed, both of which must be used to authenticate with the Nextech authorization server. If your app is not capable of securely storing a secret, then it is considered to be a **public** client, and will only be issued a client ID after the Nextech app registration process has completed. **NOTE:** Since Nextech requires the use of [PKCE](https://tools.ietf.org/html/rfc7636) (see the "PKCE" section of this documentation below, or the provided RFC link, for more details), native apps CAN store refresh tokens, despite being "public" clients, but such apps must still take other available additional security precautions (secure on-device storage, for example) when storing refresh tokens.

If your app is browser based you will need to include an allowed origin address, representing the origin that the app will be making calls from, in your registration form, so that your app does not encounter [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) issues when it tries to talk to the Nextech authorization server.

Finally, if your app is a system/backend service app that requires no user interaction then it **must** be a confidential client, and you must provide a TLS 1.2 protected URL to the public JWK (JSON Web Key) Set utilized by the system app for JWT credential signing. See [here](http://hl7.org/fhir/uv/bulkdata/STU1.0.1/authorization/index.html#registering-a-smart-backend-service-communicating-public-keys) for more details.

Examples of public clients include:
- Native mobile apps where the app is installed on a user's device and does not have a separate secure backend server (aside from the FHIR server that it calls into). If a client secret were stored on a device like this, a malicious user could theoretically decompile the application and retrieve it
- Single page web apps. Users have access to the source code of such an app, so a client secret cannot be securely stored

Examples of confidential clients include:
- Web apps where a secure backend server exists, and this server is what is used handle the code exchange with the Nextech authorization server
- Mobile apps where a secure backend server exists, and this server is what is used handle the code exchange with the Nextech authorization server

## Supported SMART on FHIR app types ##
There are three different types of SMART apps that Nextech supports for communicating with the Nextech API:

* [Patient-facing apps](#patient-facing-apps)
* [Practitioner-facing apps](#practitioner-facing-apps)
* [System apps](#system-apps)

## Patient-facing apps ##
SMART apps of this type are intended for use by a single patient, and require that the patient (and their associated practice) be setup with a [myPatientVisit](https://www.mypatientvisit.com) patient portal user account. Once setup, patient apps must follow the [standlone launch (1.0.0) sequence](https://www.hl7.org/fhir/smart-app-launch/1.0.0/index.html#standalone-launch-sequence), as defined by the SMART app framework specification, which uses the authorization code flow (described further below).

Patient-facing apps must request, at a minimum, the below scopes in their authentication request to the Nextech authorization server, in addition to whatever other access scopes are required by the application:

* `openid`
* `launch/patient`

## Practitioner-facing apps ##
SMART apps of this type are for use by a practitioner within a practice, and can be allowed to access all patient information in the practice, or can instead be focused on a single patient at a time. The practice that the practitioner is associated with must be setup with [myPatientVisit](https://www.mypatientvisit.com). Once setup, practitioner apps may follow either the [standlone launch sequence (1.0.0)](https://www.hl7.org/fhir/smart-app-launch/1.0.0/index.html#standalone-launch-sequence) or the [EHR launch sequence (1.0.0)](https://www.hl7.org/fhir/smart-app-launch/1.0.0/index.html#ehr-launch-sequence) as defined by the SMART app framework specification, both of which use the authorization code flow (described further below).

For practitioner apps following the EHR launch sequence, the app that resides at the launch URL provided to Nextech upon client registration must use the provided `iss` URL parameter, which should always point to the Nextech API URL ( `https://select.nextech-api.com/api/r4`) to query either the Nextech API 's metadata endpoint (`https://select.nextech-api.com/api/r4/metadata`) or SMART configuration endpoint (`https://select.nextech-api.com/api/r4/.well-known/smart-configuration`), both of which contain in their responses OAuth `authorize` and `token` endpoint URLs for use in requesting authorization to access the Nextech API via the Nextech authorization server.

Practitioner-facing apps must request, at a minimum, the below scopes in their authorization request to the Nextech authorization server, in addition to whatever other access scopes are required by the application:

* `openid`
* `launch/patient` (if doing a standalone launch that requires patient context)
* `launch` (if doing an EHR launch with patient context already provided as a URL parameter to the app's registered launch URL)

### Authorization code flow ###
The authorization code workflow, which must be used by both patient- and practitioner-facing SMART apps, follows the below steps, and **must use [PKCE](#PKCE) with a SHA-256 code challenge hashing scheme** :

**Step 1.** The SMART Application redirects the user to the Authorization Server (or in the case of a native application, opens a web browser) at a URL similar to the following:
<pre class="center-column">
https://mypatientvisit-sts-experimental.azurewebsites.net/connect/authorize?aud=https://select.nextech-api.com/api/r4&response_type=code&client_id={appClientID}&scope=openid%20offline_access%20fhirUser%20launch%2Fpatient%20patient%2FAllergyIntolerance.read&redirect_uri=https%3A%2F%2FmySmartApp.com%2Fcallback&code_challenge={sha256HashOfRandomString}0&code_challenge_method=S256&state={someUnpredictableValue}
</pre>

*URL parameter notes:*

| Name | Description |
| ---- | ----------- |
| aud |  This is the base URL to the Nextech API that the app is requesting access to pull FHIR resources from, and will always be `https://select.nextech-api.com/api/r4` |
| response_type |  This is always set to `code` for the authorization flow |
| client_id |  This is the unique identifier for your SMART app, issued to you by Nextech |
| scope |  indicates the space-delimited set of scopes that your SMART app is requesting |
| redirect_uri |  This is the URI that belongs to your SMART app, which the app user will be redirected to, once the authorization flow completes |
| code_challenge |  This is the Base64-encoded SHA-256 hash of the random string generated for the request (as part of [PKCE](#PKCE)) |
| code_challenge_method |  This should always be `S256`, to indicate the hashing method of the `code_challenge` value that is supplied, for use with [PKCE](#PKCE) |
| state |  An unpredictable value with at least 122 bits of entropy (e.g., a properly configured random UUID is suitable) that is tied to the user's current session, and can be verified at the end of the authorization code flow to make sure that no replay attacks have occurred |

**Step 2**: The Nextech authorization server presents the user with a login screen. For patient-facing SMART apps, patients will need to sign in using their myPatientVisit user account, select a patient, and then consent to the scopes that they want to allow the app to use to request information on their behalf. For practitioner-facing SMART apps, the practitioner will be prompted to login using their Nextech software's user credentials (and, if the `launch/patient` scope is requested for a standalone launch sequence, select a patient context to use for the app), and then consent to the scopes that they want to allow the app to use to request information on their behalf.

**Step 3**: The Nextech authorization server redirects the user back the the `redirect_uri` that was provided in step 1, and adds a `code` parameter onto the URL, which is a temporary authorization code provided by the Nextech authorization server that the SMART app now must exchange in order to get a back an access token that can be used to access the Nextech API's FHIR resources. Additionally, the `state` parameter should be verified to be the same state token provided in the request in step 1. Example:
<pre class="center-column">
https://mySmartApp.com/callback?code=aded553gr3g7dggakG&state={someUnpredictableValue}
</pre>


**Step 4**: The SMART app now must call the Nextech authorization server to exchange its authorization code for an access token, which it must do via a request like below:
<pre class="center-column">
POST /connect/token
Content-Type: application/x-www-form-urlencoded
Authorization: Basic [client ID and secret]

client_id={appClientID}&grant_type=authorization_code&code=aded553gr3g7dggakG&redirect_uri=https://mySmartApp.com/callback&scope=openid%20offline_access%20fhirUser%20launch%2Fpatient%20patient%2FAllergyIntolerance.read&aud=https://select.nextech-api.com/api/r4&code_verifier={someRandomString}
</pre>

*Header notes:*

| Name | Description |
| ---- | ----------- |
| Content-Type | must be set to `application/x-www-form-urlencoded` |
| Authorization | This header is optional, and must only be used if your SMART app client is a confidential client (i.e. it has a client secret configured that it is capable of securely storing). This header uses Basic auth, which will have the string `Basic`, followed by a space, followed by the Base-64 encoding of the string in the form `[client ID]:[client secret]`. |

*Parameter notes:*

| Name | Description |
| ---- | ----------- |
| client_id | This is the same Nextech-issued client ID that was used in step 1 above |
| grant_type | This is always set to `authorization_code` |
| code | This is code received from the Nextech authorization server in step 3 above |
| redirect_uri | This must match the URI used in step 1 above |
| scope | This must match the scopes used in step 1 above |
| code_verifier | This is the original (unhashed) random string that was provided in a hashed format in the `code_challenge` parameter in step 1 above |

The Nextech authorization server will then respond to with a response similar to below, which includes an access token that can now be used by the SMART app to access FHIR resources within the Nextech API:
<pre class="center-column">
{
   "access_token":"eyJraWQiOiJ1.eyJhenAiOiJteS1jbGllb.Bv42OB0f",
   "id_token":"eyJra33ed8dofh.doh3ohfeisgdOiJteS1jbGllb.u44hdhB0p",
   "token_type":"bearer",
   "expires_in":900,
   "scope":"openid fhirUser launch/patient patient/AllergyIntolerance.read",
   "patient":"123",
   "encounter":null,
   "smart_style_url":"https://mypatientvisit-sts-dev.azurewebsites.net/css/smart-style.json?v=133092895520000000",
   "need_patient_banner": false
}
</pre>

*Response body notes:*

| Name | Description |
| ---- | ----------- |
| id_token | returned if the `openid` and/or `fhirUser` scopes are approved by the SMART app user. Contains information about the user. The `fhirUser` claim within this token can be used to retrieve information about the user via a FHIR resource endpoint |
| patient | Patient ID indicating that the app launched in the context of a patient with this ID. Any patient-level scopes will be scoped to this particular patient |
| encounter | Encounter ID, indicating that the app launched in the context of a particular encounter. **Currently returned, but not supported** |
| need_patient_banner | Used in EHR launches for practitioner apps. Indicates whether or not the app was launched in a context that requires a patient banner be displayed |
| smart_style_url | Used in EHR launches for practitioner apps. URL where styling information can be found, for apps that support styling |

Additionally, if the `offline_access` scope is requested by the app (recommended, or else the app will have to frequently re-authenticate with the Nextech authorization server), and consented to by the SMART app user, then the response body will contain a `refresh_token` member containing a refresh token that can be used to acquire a new `access_token` once the one received in the response expires (in the amount of time, in seconds, indicated by the `expires_in` response body member).

### PKCE ###
[PKCE](https://tools.ietf.org/html/rfc7636), using a SHA-256 hashing method for its code challenge values, must be used with all SMART apps following the authorization code flow (so any apps that require user interaction), so that potential interception attacks can be mitigated. PKCE requires that the SMART app add an additional token to the initial authorization request, and then requires the SMART app to submit a verifier during the code exchange step that can be used as additional proof that no "man in the middle" has intercepted the authorization code and is trying to maliciously redeem it.

In order to use PKCE, the SMART app must first generate a random string to use as a challenge value. The SMART app must make sure to generate a new random string each time PKCE is used. Once the random string is generated, a SHA-256 hash of the random string must be generated, and the resulting hash then Base64-encoded, for use as the `code_challenge` URL parameter in the authorization server's authorize request, which is made in the first step of the authorization code flow. 

## System apps ##
SMART apps of this type have no need for user interaction, can run autonomously (or semi-autonomously), and are capable of protecting a private key. System apps must follow the [SMART Backend Services Authorization (STU 1.0.1) specification](http://hl7.org/fhir/uv/bulkdata/STU1.0.1/authorization/index.html) for authentication/authorization, which requires that SMART apps follow the client credentials flow, with JWT credentials, which is described below. The practice that the system app wishes to access must be setup with [myPatientVisit](https://www.mypatientvisit.com), and established at app registration time.

### Client credentials flow with JWT credentials ###
System apps follow a variation of the client credentials flow, one that uses a cryptographically secure, signed JWT (JSON Web Token) that it presents to the Nextech authorization server, instead of a client secret. This flow is fully defined in [RFC 7526](https://datatracker.ietf.org/doc/rfc7523/).

In order to authenticate, the SMART app must first create a JWT resembling the following, and digitally sign it using the SMART app's private key (which must be either an `RS384` or `ES384` signature):
<pre class="center-column">
{
  "jti":"random-non-reusable-jwt-id-12",
  "sub":"my-client-id",
  "iss":"my-client-id",
  "aud":"http:\/\/example.com\/issuer\/oauth\/token",
  "kid":"some-key-id",
  "exp":1623019405,
  "iat":1623019345
}
</pre>

*Important to note:*

* The `sub` and `iss` claims within the JWT must be the Nextech-issued client ID of your application, and must be exactly the same
* The `aud` claim is the token endpoint of the Nextech authorization server

After the JWT is digitally signed, it must be sent to the Nextech authorization server with a request like below:
<pre class="center-column">
POST /connect/token
Accept: application/json
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials
&client_assertion_type=urn:ietf:params:oauth:client-assertion-type:jwt-bearer
&client_assertion=[signed JWT]
&scope=[spaceDelimitedDesiredScopes]
</pre>

The Nextech authorization server will then respond with a response like below, containing an access token that the system app can use to access FHIR resources from the Nextech API:
<pre class="center-column">
{
   "access_token":"eyJraWQiOiJ1bml0dG.eyJhenAiOiJteS1j.THbNnfuX7Ly4g",
   "token_type":"bearer",
   "expires_in":900,
   "scope":"[spaceDelimitedDesiredScopes]"
}
</pre>

## Scopes ##
Nextech currently only supports scopes that adhere to the format defined in version 1.0.0 of the SMART app specification, as indicated [here](https://www.hl7.org/fhir/smart-app-launch/1.0.0/scopes-and-launch-context/index.html). The full list of scopes supported by the Nextech API for SMART apps (depending on the type of SMART app) are as follows:

#### For patient or practitioner-facing apps: ####
* `openid`
* `fhirUser`
* `offline_access` (needed in order to receive a refresh token)

#### For patient-facing apps (standalone patient apps, or practitioner apps acting in a patient context): ####
* `launch/patient`
* `patient/*.read`
* `patient/Account.read`
* `patient/AllergyIntolerance.read`
* `patient/CarePlan.read`
* `patient/CareTeam.read`
* `patient/Condition.read`
* `patient/Device.read`
* `patient/Binary.read`
* `patient/DiagnosticReport.read`
* `patient/DocumentReference.read`
* `patient/DocumentReference.write`
* `patient/Encounter.read`
* `patient/Goal.read`
* `patient/Immunization.read`
* `patient/Location.read`
* `patient/MedicationRequest.read`
* `patient/Observation.read`
* `patient/Organization.read`
* `patient/Patient.read`
* `patient/Practitioner.read`
* `patient/Procedure.read`
* `patient/Provenance.read`

#### For practitioner-facing apps: ####
* `launch`
* `user/*.read`
* `user/Account.read`
* `user/AllergyIntolerance.read`
* `user/CarePlan.read`
* `user/CareTeam.read`
* `user/Condition.read`
* `user/Device.read`
* `user/Binary.read`
* `user/DiagnosticReport.read`
* `user/DocumentReference.read`
* `user/DocumentReference.write`
* `user/Encounter.read`
* `user/Goal.read`
* `user/Immunization.read`
* `user/Location.read`
* `user/MedicationRequest.read`
* `user/Observation.read`
* `user/Organization.read`
* `user/Patient.read`
* `user/Practitioner.read`
* `user/Procedure.read`
* `user/Provenance.read`

#### For secure, system apps that require no user interaction: ####
* `system/*.read`
* `system/Account.read`
* `system/AllergyIntolerance.read`
* `system/CarePlan.read`
* `system/CareTeam.read`
* `system/Condition.read`
* `system/Device.read`
* `system/Binary.read`
* `system/DiagnosticReport.read`
* `system/DocumentReference.read`
* `system/DocumentReference.write`
* `system/Encounter.read`
* `system/Goal.read`
* `system/Immunization.read`
* `system/Location.read`
* `system/MedicationRequest.read`
* `system/Observation.read`
* `system/Organization.read`
* `system/Patient.read`
* `system/Practitioner.read`
* `system/Procedure.read`
* `system/Provenance.read`


All scope names map to the FHIR resource endpoint that they can be used against. For example, a SMART app using an access token that has been granted the `patient/Encounter.read`, `user/Encounter.read`, or `system/Encounter.read` scopes can use that token against the `GET https://select.nextech-api.com/api/r4/Encounter/{someEncounterID}` endpoint to grab information about a particular encounter. 

**Important note:** With the exception of the `DocumentReference.write` scopes, writing-related scopes are currently **not supported**. Additionally, SMART apps must only request the bare minimum scopes that are required for their app to function.

### Example of SMART App Authorization With Postman ###
 Once you have been issued a client ID (and client secret, if capable of securing one) from Nextech, you can use Postman to test grabbing an access token using your app credentials:
1. For a given Postman collection go to the `Authorization` tab
1. Set `Authorization` to `Oauth 2.0`. This should give you additional fields to fill out
1. `Header Prefix` should be set to `Bearer`
1. Grant type ahould be set to `Authorization Code (With PKCE)`
1. `Auth URL` should be set to `https://mypatientvisit-sts-dev.azurewebsites.net/connect/authorize?aud=https://select.nextech-api.com/api/r4`
1. `Access Token URL` should be set to `https://mypatientvisit-sts-dev.azurewebsites.net/connect/token`
1. `Client ID` should be set to the value given to you by Nextech
1. `Secret` should be set to the value given to you by Nextech, if any
1. `Code Challenge Method` should be `SHA-256`
1. `Scopes` should contain all needed scopes, space-delimited. At a minimum this should be `launch/patient openid`

Once these fields are filled out and the authorization request is made, your browser should open up to the Nextech authorization server's login screen. MyPatientVisit user credentials, for patient-facing apps, or Nextech software user credentials, for practitioner-facing apps, will have to be used to login. After logging in, the user will select which practice and patient they are granting access to, and then they will consent (or not) to the requested scopes. Once this is done, there will be a callback to Postman (check browser pop-up settings and try changing your default browser if that fails). When Postman receives this callback, it will pop up a dialog containing the response information from the Nextech authorization server, including the access token. 

## Using the Access Token ##
Once your app has gone through the above steps to acquire an access token, that access token needs to be placed in an `Authorization` header, using the `Bearer` scheme:`Bearer {token}` where `{token}` represents your token, for all requests made from the app to the Nextech API's FHIR resource endpoints.

### Refresh Access Token ###
Refresh tokens are used to renew an expired access token without providing user credentials. An `access_token` and `refresh_token` pair is issued when requesting an access token using the authorization code flow (see above) for patient or practitioner-facing SMART apps (system apps are not issued refresh tokens, and so must always request a new access token upon previous access token expiration), as long as the SMART app requests the `offline_access` scope, and the user consents to that scope. When the `access_token` expires, your SMART app can call into the Nextech authorization server's `connect/token` endpoint to be issued a new access token (and refresh token), as shown below:

<pre class="center-column">
POST /connect/token
Content-Type: application/x-www-form-urlencoded
Authorization: Basic [client ID and secret]

grant_type=refresh_token&refresh_token=<{refreshToken}
</pre>

*Header notes:*

| Name | Description |
| ---- | ----------- |
| Content-Type | must be set to `application/x-www-form-urlencoded`|
| Authorization | This header is optional, and must only be used if your SMART app client is a confidential client (i.e. it has a client secret configured that it is capable of securely storing). This header uses Basic auth, which will have the string `Basic`, followed by a space, followed by the Base-64 encoding of the string in the form `[client ID]:[client secret]`.|

*Parameter notes:*

| Name | Description |
| ---- | ----------- |
| grant_type | This is always set to `refresh_token`|
| refresh_token | This is the refresh token that was returned alongside the `access_token` in the previous response from the Nextech authorization server, when the SMART app first acquired an access token|

### Revoking Refresh Tokens ###
If a SMART app wishes to revoke a refresh token that it has been issued, then it can do so by making a call like below to the Nextech authorization server:

<pre class="center-column">
POST /connect/revocation
Content-Type: application/x-www-form-urlencoded
Authorization: Basic [client ID and secret]

token={refreshToken}
</pre>

*Header notes:*

| Name | Description |
| ---- | ----------- |
| Content-Type | must be set to `application/x-www-form-urlencoded`|
| Authorization | This header is optional, and must only be used if your SMART app client is a confidential client (i.e. it has a client secret configured that it is capable of securely storing). This header uses Basic auth, which will have the string `Basic`, followed by a space, followed by the Base-64 encoding of the string in the form `[client ID]:[client secret]`.|

*Parameter notes:*

* `token` - This is the refresh token that was returned alongside the `access_token` in the previous response from the Nextech authorization server, when the SMART app first acquired an access token

Revoking the refresh token will make it so that the SMART app will need to have the user re-authorize the SMART app's required scopes, once the access token that accompanied the refresh token expires.

## Nextech Authorization Server Metadata Endpoint ##
SMART apps can call the Nextech authorization server's OpenID Connect metadata endpoint in order to find out information about the available endpoints, scopes, and response types supported by the Nextech authorization server, for use by SMART apps: 
<pre class="center-column">
GET .well-known/openid-configuration
</pre>

This endpoint requires no authentication.

### Nextech Authorization Server UserInfo Endpoint ###
SMART apps can call the Nextech authorization server's `UserInfo` endpoint to learn more about the user associated with a given access token: 
<pre class="center-column">
GET connect/userinfo
Authorization: Bearer [access token]
</pre>

Header notes:

* `Authorization` - This header must contain the `access_token` prevously acquired from the Nextech authorization server in the previous response from the Nextech authorization server, when the SMART first acquired an access token, following the `Bearer` text in the header value

### Nextech Authorization Server Session Lifetime ###
All browser sessions that a SMART app opens with the Nextech authorization server are only good for the lifetime of the browser window/tab. No persisted web authorization session is kept between a given SMART app and the Nextech authorization server after the app has successfully been authorized (or just exited the Nextech authorization server web page), so, if a SMART app redirects to the Nextech authorization server not long after being issued an access and/or refresh token then the Nextech authorization server will once more prompt the user of the app to login again, no matter how much time has passed since the SMART app's previous authorization request. Since there is no persistent authorization web session maintained between the SMART app and the Nextech authorization server, there is no need for the SMART app to logout of the Nextech authorization server session: once the refresh token (if any was obtained, otherwise just the access token) expires the SMART app will need to re-authorize with the Nextech authorization server.