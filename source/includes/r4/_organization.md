# Organization

### Overview
An [Organization](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization.html) resource represents a physical location where services are provided. This may or may not be under the practice's management.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique value assigned to each location which discerns it from all others | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _12.8_ |
| identifier | The unique value assigned to each location which discerns it from all others | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _12.8_ |
| identifier:NPI | NPI identifier for the organization that is used to identify the organization across multiple disparate systems |  [Identifier](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization-definitions.html#Organization.identifier:NPI) | _16.9_ |
| meta.lastUpdated | The last time the organization was modified | [instant](https://www.hl7.org/fhir/R4/datatypes.html#instant) | _16.9_ |
| name | The name of the location | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _12.8_ |
| telecom | The contact details of communication at the location | [ContactPoint](https://www.hl7.org/fhir/R4/datatypes.html#ContactPoint) | _12.8_ |
| address | The address of the location | [Address](https://www.hl7.org/fhir/R4/datatypes.html#Address) | _12.8_ |
| address.country | The country of the location address | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.9_ |
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
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or body | The unique value assigned to each organization which discerns it from all others |  No | _12.8_ |
| status | query or body | Searches for organizations with a specific kind of status. See [OrganizationStatus](https://www.hl7.org/fhir/R4/valueset-location-status.html) | No | _12.8_ |
| includeAll | query or body | By default, or if includeAll is false, then only managed organizations are returned, for example the practice's primary office location. If includeAll is true, then all organizations will be returned, whether they are under under practice management or not, but where services are provided, such as a hospital or a clinic. | No | _14.4_ |
| name | query or body | The name of the organization | No | _12.8_ |
| address | query or body | A (part of the) address of the organization | No | _12.8_ |
| address-city | query or body | A city specified in an address | No | _12.8_ |
| address-state | query or body | A state specified in an address | No | _12.8_ |
| address-postalcode | query or body | A postal code specified in an address | No | _12.8_ |
| phone | query or body | Searches for locations based on phone numbers and fax numbers | No | _12.8_ |
| _id | query or body | The organization unique identifier | No | _16.9_ |
| _lastUpdated | query or body | The last time the organization was modified | No | _16.9_ |

**_Note:_**  The possible filter values for the `_lastUpdated` parameter are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

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
