# Practitioner

## Practitioner

### Overview
A individual who is engaged in the healthcare process and healthcare-services. In the Nextech Software, these are providers who are linked to users.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each Practitioner which discerns it from all others | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.8_ |
| active | 	Whether this practitioner's record is in active use. | [boolean](https://www.hl7.org/fhir/datatypes.html#boolean) | _12.8_ |
| name |The name(s) associated with the practitioner | [HumanName](https://www.hl7.org/fhir/datatypes.html#HumanName) | _12.8_ |
| telecom | Contact detail(s) for the practitioner (that apply to all roles) | [ContactPoint](https://www.hl7.org/fhir/datatypes.html#ContactPoint) | _12.8_ |
| address | Address(es) of the practitioner that are not role specific | [Address](https://www.hl7.org/fhir/datatypes.html#Address) | _12.8_ |
| gender | Gender of the practitioner | [Code](https://www.hl7.org/fhir/valueset-administrative-gender.html) | _12.8_ |
| birthDate | The date of birth of the practitioner | [date](https://www.hl7.org/fhir/datatypes.html#date) | _12.8_ |


### Example
<pre class="center-column">
{
    "resourceType": "Practitioner",
    "identifier": [
        {
            "use": "official",
            "system": "https://select.nextech-api.com/api/structuredefinition/practitioner-id"
            "value": "9219"
        },
        {
            "system": "http://hl7.org/fhir/sid/us-npi",
            "value": "1245319599"
        }
    ],
    "active": true,
    "name": [
        {
            "text": "Provider, Test",
            "family": "Provider",
            "given": [
                "Test",
                ""
            ]
        }
    ],
    "telecom": [
        {
            "system": "phone",
            "value": "(813) 324-2391",
            "use": "work"
        },
        {
            "system": "email",
            "value": "provider@nextech.com",
            "use": "work"
        }
    ],
    "address": [
        {
            "use": "work",
            "type": "both",
            "line": [
                "550 W N ST"
            ],
            "city": "Tampa",
            "state": "FL",
            "postalCode": "33609"
        }   
    ],
    "gender": "female",
    "birthDate": "1970-09-27"
</pre>
&nbsp;

### *Get*
Returns a single Practitioner result based on the Practitioner ID.

#### HTTP Request 
`GET /r4/Practitioner/{practitionerID}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| practitionerID | path | The unique identifier for the practitioner | Yes | _12.8_ |

#### Example: Get a specific Practitioner based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Practitioner/12
</pre>
&nbsp;

### *Search*
Searches for all  based on the given search criteria.

#### HTTP Request 
`GET /r4/Practitioner?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or uri | The unique value assigned to each Practitioner which discerns it from all others |  No | _12.8_ |
| active | query | Searches for Practitioners whose record is in active use.| No | _12.8_ |
| name | query | The name of the Practitioner | No | _12.8_ |
| family | query | The family (last) name of the practitioner | No | _12.8_ |
| given | query | The given (first) name of the practitioner | No | _12.8_ |
| address | query | A (part of the) address of the Practitioner | No | _12.8_ |
| address-city | query | A city specified in an address | No | _12.8_ |
| address-state | query | A state specified in an address | No | _12.8_ |
| address-postalcode | query | A postal code specified in an address | No | _12.8_ |
| phone | query | Searches for Practitioners based on phone numbers | No | _12.8_ |
| email | query | Searches for Practitioner based on email address | No | _12.8_ |
| gender | query | Searches for Practitioner based on gender | No | _12.8_ |

#### Example: Get all Practitioners

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Practitioner
</pre>
&nbsp;

#### Example: Get all active Practitioners

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Practitioner?active=true
</pre>
&nbsp;

#### Example: Get a specific Practitioner based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Practitioner?identifier=12
</pre>
&nbsp;

#### Example: Get a specific Practitioner based on National Provider Identifier (NPI)

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Practitioner?identifier=http://hl7.org/fhir/sid/us-npi|1245319599
</pre>
&nbsp;

#### Example: Get all active Practitioners whose city starts with 'Tampa'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Practitioner?address-city=Tampa
</pre>
&nbsp;

#### Example: Get a specific Practitioner(s) based on gender

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Practitioner?gender=male
</pre>
&nbsp;

#### Example: Get all Practitioners whose name contains 'smith'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Practitioner?name:contains=smith
</pre>
&nbsp;

### Remarks
* To get a specific Practitioner by the National Provider Identifier (NPI), the system (http://hl7.org/fhir/sid/us-npi) must be included in the query.
* Providers will not show up as Practitioners unless their Contacts module record has the Linked User setting configured.
    * Prior to version 14.1, Practitioners could be returned more than once if multiple users are assigned to use the same provider in their Contacts module User properties.
