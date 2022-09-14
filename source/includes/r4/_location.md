# Location

## Location

[(USCoreOrganizationProfile)](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization.html)

### Overview
A physical location where services are provided. This may or may not be under the practice's management.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each location which discerns it from all others | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.8_ |
| meta.lastUpdated | The last time the location was modified | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | _16.9_ |
| status | The status of the location (ie. active, inactive) | [code](https://www.hl7.org/fhir/datatypes.html#code) | _12.8_ |
| managed | True if this location is under practice management, for example the practice's primary office location. False if this location is not under practice management, but where services are provided, for example a hospital or clinic. | [boolean](https://www.hl7.org/fhir/datatypes.html#boolean) | _14.4_ |
| name | The name of the location | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| telecom | The contact details of communication at the location | [ContactPoint](https://www.hl7.org/fhir/datatypes.html#ContactPoint) | _12.8_ |
| address | The address of the location | [Address](https://www.hl7.org/fhir/datatypes.html#Address) | _12.8_ |
| managingOrganization | The identifier of the location | [Reference](http://hl7.org/fhir/R4/references.html#Reference) [(USCoreOrganizationProfile)](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization.html)  | _16.9_ |

### Example
<pre class="center-column">
{
    "resourceType": "Location",
    "id": "2",
    "meta": 
    {
   	    "lastUpdated": "2022-04-02T14:04:35.9+00:00"
    },
    "extension": [
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/managed",
            "valueBoolean": true
        }
    ],
    "identifier": [
        {
            "use": "official",
            "value": "2"
        }
    ],
    "status": "active",
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
    },
	"managingOrganization": {
		"reference": "Organization/1",
		"display": "Tampa Dermatology"
	}
}
</pre>
&nbsp;

### *Get*
Returns a single Location result based on the Location ID.

#### HTTP Request 
`GET /r4/Location/{LocationID}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| locationID | path | The location unique identifier | Yes | _16.9_ |

#### Example: Get an location with an ID of '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Location/123
</pre>
&nbsp;

### *Search*
Searches for all locations based on the given search criteria.

#### HTTP Requests
- `GET /r4/Location?{parameters}`
- `POST /r4/Location/_search?{parameters}`
- `POST /r4/Location/_search`
  - *application/x-www-form-urlencoded payload:* `{parameters}`
> **_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or payload | The unique value assigned to each location which discerns it from all others |  No | _12.8_ |
| status | query or payload | Searches for locations with a specific kind of status. See [LocationStatus](https://www.hl7.org/fhir/valueset-location-status.html) | No | _12.8_ |
| includeAll | query or payload | By default, or if includeAll is false, then only managed locations are returned, for example the practice's primary office location. If includeAll is true, then all locations will be returned, whether they are under under practice management or not, but where services are provided, such as a hospital or a clinic. | No | _14.4_ |
| name | query or payload | The name of the location | No | _12.8_ |
| address | query or payload | A (part of the) address of the location | No | _12.8_ |
| address-city | query or payload | A city specified in an address | No | _12.8_ |
| address-state | query or payload | A state specified in an address | No | _12.8_ |
| address-postalcode | query or payload | A postal code specified in an address | No | _12.8_ |
| phone | query or payload | Searches for locations based on phone numbers and fax numbers | No | _12.8_ |
| _id | query or payload | The location unique identifier | No | _16.9_ |
| _lastUpdated | query or payload | The last time the location was modified | No | _16.9_ |

#### Example: Get all active locations

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Location/_search?status=active
</pre>
&nbsp;

#### Example: Get all locations, including managed and non-managed locations

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Location/_search?includeAll=true
</pre>
&nbsp;

#### Example: Get all active locations whose city starts with 'Tampa'

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Location/_search?address-city=Tampa&status=active
</pre>
&nbsp;

#### Example: Get all locations whose name contains 'dermatology'

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Location/_search?name:contains=dermatology
</pre>
&nbsp;

#### Example: Get a specific location based on identifier

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Location/_search?identifier=123
</pre>
&nbsp;

#### Example: Get all active locations

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Location?status=active
</pre>
&nbsp;

#### Example: Get all locations, including managed and non-managed locations

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Location?includeAll=true
</pre>
&nbsp;

#### Example: Get all active locations whose city starts with 'Tampa'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Location?address-city=Tampa&status=active
</pre>
&nbsp;

#### Example: Get all locations whose name contains 'dermatology'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Location?name:contains=dermatology
</pre>
&nbsp;

#### Example: Get a specific location based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Location?identifier=123
</pre>
&nbsp;
