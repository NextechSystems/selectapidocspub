# Metadata

## Metadata

### Overview
Information about supported server functionality and server's SMART on FHIR configuration.

### Capability Statement

#### Fields
| Name | Description | Type |
| ---- | ----------- | ---- |
| resourceType | The declaration of the type of resource this is. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) |
| status | The status of this capability statement. | [code](https://www.hl7.org/fhir/R4/datatypes.html#code) |
| date |The date (and optionally time) when the capability statement was published.|[dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) |
| publisher | The name of the organization or individual that published the capability statement. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) |
| kind | The way that this statement is intended to be used, to describe an actual running instance of software, a particular product or a class of implementation. | [code](https://www.hl7.org/fhir/R4/datatypes.html#code) |
| implementation.description | Information about the specific installation that this capability statement relates to. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) |
| implementation.url | An absolute base URL for the implementation. | [url](https://www.hl7.org/fhir/R4/datatypes.html#url) |
| fhirVersion | The version of the FHIR specification that this CapabilityStatement describes. | [code](https://www.hl7.org/fhir/R4/datatypes.html#code) |
| format | A list of the formats supported by this implementation using their content types. | [code](https://www.hl7.org/fhir/R4/datatypes.html#code) |
| implementationGuide | A list of implementation guides that the server does (or should) support in their entirety. | [canonical](https://www.hl7.org/fhir/R4/datatypes.html#canonical)([Implementation Guide](https://www.hl7.org/fhir/R4/implementationguide.html)) |
| instantiates | Reference to a canonical URL of another CapabilityStatement that this software implements. | [canonical](https://www.hl7.org/fhir/R4/datatypes.html#canonical)([Capabiliy Statement](https://www.hl7.org/fhir/R4/capabilitystatement.html)) |
| rest.mode | Identifies whether this portion of the statement is describing the ability to initiate or receive restful operations. | [code](https://www.hl7.org/fhir/R4/datatypes.html#code) |
| rest.security.extension | The oauth uris for this server ('authorize' and 'token' endpoints). | [Extension](https://www.hl7.org/fhir/R4/extensibility.html#Extension) |
| rest.security.service | Types of security services that are supported by the system. | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) |
| rest.resource.type | A type of resource exposed via the restful interface. | [code](https://www.hl7.org/fhir/R4/datatypes.html#code) |
| rest.resource.supportedProfile | A list of profiles that represent different use cases supported by the system. | [canonical](https://www.hl7.org/fhir/R4/datatypes.html#canonical)([StructureDefinition](https://www.hl7.org/fhir/R4/structuredefinition.html)) |
| rest.resource.interaction.code | Coded identifier of the operation, supported by the system resource. | [code](https://www.hl7.org/fhir/R4/datatypes.html#code) |
| rest.resource.searchRevInclude | A list of _revinclude (reverse include) values supported by the server. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) |
| rest.resource.searchParam.name | The name of the search parameter used in the interface. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) |
| rest.resource.searchParam.type | The type of value a search parameter refers to, and how the content is interpreted. | [code](https://www.hl7.org/fhir/R4/datatypes.html#code) |
| rest.resource.operation.name | The name of the operation or query. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) |

&nbsp;

#### *Get*
Retrieves the Capability Statement which holds information about supported server functionality.

##### HTTP Request 
`GET /r4/metadata`

##### Example: Get Capability Statement

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/metadata
</pre>
&nbsp;

### SMART Configuration

#### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| capabilities | Array of strings representing SMART capabilities | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | |
| authorization_endpoint | URL to the OAuth2 authorization endpoint | [url](https://www.hl7.org/fhir/R4/datatypes.html#url) | |
| token_endpoint | URL to the OAuth2 token endpoint | [url](https://www.hl7.org/fhir/R4/datatypes.html#url) | |
| token_endpoint_auth_methods_supported | Array of client authentication methods supported by the token endpoint | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | |
| token_endpoint_auth_signing_alg_values_supported | Array containing a list of the JWS signing algorithms supported by the token endpoint. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | |

#### Example
<pre class="center-column">
{
    "capabilities": [
        "launch-ehr",
        "launch-standalone",
        "client-public",
        "client-confidential-symmetric",
        "sso-openid-connect",
        "context-banner",
        "context-style",
        "context-ehr-patient",
        "context-ehr-encounter",
        "context-standalone-patient",
        "context-standalone-encounter",
        "permission-offline",
        "permission-patient",
        "permission-user"
    ],
    "authorization_endpoint": "https://mypatientvisit-sts-dev.azurewebsites.net",
    "token_endpoint": "https://mypatientvisit-sts-dev.azurewebsites.net",
    "token_endpoint_auth_methods_supported": [
        "private_key_jwt"
    ],
    "token_endpoint_auth_signing_alg_values_supported": [
        "RS384",
        "ES384"
    ]
}
</pre>
&nbsp;

#### *Get*
Retrieves server's SMART on FHIR configuration

##### HTTP Request 
`GET /r4/.well-known/smart-configuration`


##### Example: Get SMART on FHIR configuration

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/.well-known/smart-configuration
</pre>
&nbsp;