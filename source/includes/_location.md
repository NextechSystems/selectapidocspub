# Location

## Location

### Overview
A physical location where services are provided. These locations specifically include managed locations configured in the Nextech software.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each location which discerns it from all others | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.8_ |
| status | The status of the location (ie. active, inactive) | [code](https://www.hl7.org/fhir/datatypes.html#code) | _12.8_ |
| name | The name of the location | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| telecom | The contact details of communication at the location | [ContactPoint](https://www.hl7.org/fhir/datatypes.html#ContactPoint) | _12.8_ |
| address | The address of the location | [Address](https://www.hl7.org/fhir/datatypes.html#Address) | _12.8_ |

### Example
<pre class="center-column">
{
    "resource": {
        "resourceType": "Location",
        "id": "2",
        "identifier": [
            {
                "use": "official",
                "value": "2"
            }
        ],
        "name": "South Dermatology",
        "telecom": [
            {
                "system": "phone",
                "value": "(727) 623-6100",
                "use": "work"
            },
            {
                "system": "other",
                "value": "(727) 718-9884",
                "use": "work"
            },
            {
                "system": "fax",
                "value": "(727) 623-6187",
                "use": "work"
            }
        ],
        "address": {
            "use": "work",
            "type": "both",
            "line": [
                "1234 Central Ave., Suite N"
            ],
            "city": "St. Petersburg",
            "state": "FL",
            "postalCode": "11598"
        }
    }
}
</pre>
&nbsp;

### *Search*
Searches for all locations based on the given search criteria.

#### HTTP Request 
`GET /Location?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or uri | The unique value assigned to each location which discerns it from all others |  No | _12.8_ |
| status | query | Searches for locations with a specific kind of status. See [LocationStatus](https://www.hl7.org/fhir/valueset-location-status.html) | No | _12.8_ |
| name | query | The name of the location | No | _12.8_ |
| address | query | A (part of the) address of the location | No | _12.8_ |
| address-city | query | A city specified in an address | No | _12.8_ |
| address-state | query | A state specified in an address | No | _12.8_ |
| address-postalcode | query | A postal code specified in an address | No | _12.8_ |
| phone | query | Searches for locations based on phone numbers and fax numbers | No | _12.8_ |

#### Example: Get all active locations

<pre class="center-column">
GET https://select.nextech-api.com/api/Location?status=active
</pre>
&nbsp;

#### Example: Get all active locations whose city starts with 'Tampa'

<pre class="center-column">
GET https://select.nextech-api.com/api/Location?address-city=Tampa&status=active
</pre>
&nbsp;

#### Example: Get all locations whose name contains 'dermatology'

<pre class="center-column">
GET https://select.nextech-api.com/api/Location?name:contains=dermatology
</pre>
&nbsp;

#### Example: Get a specific location based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/Location/12
</pre>
&nbsp;
