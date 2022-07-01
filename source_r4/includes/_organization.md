# Organization

## Organization[(USCoreOrganizationProfile)](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization.html)

### Overview
A physical location where services are provided. This may or may not be under the practice's management.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each location which discerns it from all others | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.8_ |
| meta.lastUpdated | The last time the organization was modified | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | _16.9_ |
| identifier | Identifier for the organization that is used to identify the organization across multiple disparate systems |  [(USCoreOrganizationProfile)](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization-definitions.html#Organization.identifier:NPI) | _16.9_ |
| name | The name of the location | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| telecom | The contact details of communication at the location | [ContactPoint](https://www.hl7.org/fhir/datatypes.html#ContactPoint) | _12.8_ |
| address | The address of the location | [Address](https://www.hl7.org/fhir/datatypes.html#Address) | _12.8_ |
| address.country | The country of the location address | [string](https://www.hl7.org/fhir/datatypes.html#string) | _16.9_ |
| active | Whether the organization's record is still in active use | [boolean](http://hl7.org/fhir/R4/datatypes.html#boolean) | _12.8_ |

### Example
<pre class="center-column">
{
    "resourceType": "Organization",
    "id": "2",
    "meta": 
    {
   	    "lastUpdated": "2022-04-02T14:04:35.9+00:00"
    },
    "identifier": [
        {
            "use": "official",
            "value": "2"
        },
        {
            "system": "http://hl7.org/fhir/sid/us-npi",
            "value": "ABCDE1234"
        }
    ],
    "active": true,
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
    "address": [{
        "use": "work",
        "type": "both",
        "line": [
            "1234 Central Ave., Suite N"
        ],
        "city": "St. Petersburg",
        "state": "FL",
        "postalCode": "11598", 
        "country": "US"
    }]
}
</pre>
&nbsp;

### *Get*
Returns a single Organization result based on the Organization ID.

#### HTTP Request 
`GET /r4/Organization/{OrganizationID}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| OrganizationID | path | The organization unique identifier | Yes | _16.9_ |

#### Example: Get an organization with an ID of '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Organization/123
</pre>
&nbsp;

### *Search*
Searches for all organizations based on the given search criteria.

#### HTTP Requests
- `GET /r4/Organization?{parameters}`
- `POST /r4/Organization/_search?{parameters}`
- `POST /r4/Organization/_search`
  - *application/x-www-form-urlencoded payload:* `{parameters}`
> **_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or payload | The unique value assigned to each organization which discerns it from all others |  No | _12.8_ |
| status | query or payload | Searches for organizations with a specific kind of status. See [OrganizationStatus](https://www.hl7.org/fhir/valueset-location-status.html) | No | _12.8_ |
| includeAll | query or payload | By default, or if includeAll is false, then only managed organizations are returned, for example the practice's primary office location. If includeAll is true, then all organizations will be returned, whether they are under under practice management or not, but where services are provided, such as a hospital or a clinic. | No | _14.4_ |
| name | query or payload | The name of the organization | No | _12.8_ |
| address | query or payload | A (part of the) address of the organization | No | _12.8_ |
| address-city | query or payload | A city specified in an address | No | _12.8_ |
| address-state | query or payload | A state specified in an address | No | _12.8_ |
| address-postalcode | query or payload | A postal code specified in an address | No | _12.8_ |
| phone | query or payload | Searches for locations based on phone numbers and fax numbers | No | _12.8_ |
| _id | query or payload | The organization unique identifier | No | _16.9_ |
| _lastUpdated | query or payload | No | _16.9_ |

#### Example: Get all active organizations

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Organization/_search?status=active
</pre>
&nbsp;

#### Example: Get all organizations, including managed and non-managed organizations

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Organization/_search?includeAll=true
</pre>
&nbsp;

#### Example: Get all active organizations whose city starts with 'Tampa'

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Organization/_search?address-city=Tampa&status=active
</pre>
&nbsp;

#### Example: Get all organizations whose name contains 'dermatology'

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Organization/_search?name:contains=dermatology
</pre>
&nbsp;

#### Example: Get a specific organization based on identifier

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Organization/_search?identifier=123
</pre>
&nbsp;

#### Example: Get all active organizations

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Organization?status=active
</pre>
&nbsp;

#### Example: Get all organizations, including managed and non-managed organizations

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Organization?includeAll=true
</pre>
&nbsp;

#### Example: Get all active organizations whose city starts with 'Tampa'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Organization?address-city=Tampa&status=active
</pre>
&nbsp;

#### Example: Get all organizations whose name contains 'dermatology'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Organization?name:contains=dermatology
</pre>
&nbsp;

#### Example: Get a specific organization based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Organization?identifier=123
</pre>
&nbsp;
