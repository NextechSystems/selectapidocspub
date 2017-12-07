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
| gender | Gender of the practitioner that are not role specific | [Code](https://www.hl7.org/fhir/valueset-administrative-gender.html) | _12.8_ |


### Example
<pre class="center-column">
{
    "resourceType": "Practitioner",
    "identifier": [
        {
            "use": "official",
            "value": "9219"
        }
    ],
	 "identifier": [
        {
            "use": "http://hl7.org/fhir/sid/us-npi",
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
</pre>
&nbsp;

### *Search*
Searches for all  based on the given search criteria.

#### HTTP Request 
`GET /Practitioner?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or uri | The unique value assigned to each Practitioner which discerns it from all others |  No | _12.8_ |
| active | query | Searches for Practitioners whose record is in active use.| No | _12.8_ |
| name | query | The name of the Practitioner | No | _12.8_ |
| family | query | The family (last) name of the practitioner | No | _12.6_ |
| given | query | The given (first) name of the practitioner | No | _12.6_ |
| address | query | A (part of the) address of the Practitioner | No | _12.8_ |
| address-city | query | A city specified in an address | No | _12.8_ |
| address-state | query | A state specified in an address | No | _12.8_ |
| address-postalcode | query | A postal code specified in an address | No | _12.8_ |
| phone | query | Searches for Practitioners based on phone numbers | No | _12.8_ |
| email | query | Searches for Practitioner based on email address | No | _12.8_ |

#### Example: Get all active Practitioners

<pre class="center-column">
GET https://select.nextech-api.com/api/Practitioner?active=true
</pre>
&nbsp;

#### Example: Get all active Practitioners whose city starts with 'Tampa'

<pre class="center-column">
GET https://select.nextech-api.com/api/Practitioner?address-city=Tampa
</pre>
&nbsp;

#### Example: Get a specific Practitioner(s) based on gender

<pre class="center-column">
GET https://select.nextech-api.com/api/Practitioner?gender=male
</pre>
&nbsp;

#### Example: Get all Practitioners whose name contains 'smith'

<pre class="center-column">
GET https://select.nextech-api.com/api/Practitioner?name:contains=smith
&nbsp;

#### Example: Get a specific Practitioner based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/Practitioner/12
</pre>
&nbsp;

