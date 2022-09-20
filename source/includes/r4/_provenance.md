# Provenance

### Overview
The [provenance](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) of a resource is a record that describes entities and processes involved in producing and delivering or otherwise influencing that resource.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique value assigned to each provenance which discerns it from all others | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _17.0_ |
| meta.lastUpdated | The last time the provenance was modified | [instant](https://hl7.org/fhir/R4/datatypes.html#instant) | _17.0_ |
| target | The resource(s) the provenance supports | [Reference](http://hl7.org/fhir/R4/references.html#Reference) ([Resource](http://hl7.org/fhir/R4/resource.html)) | _17.0_ |
| recorded | Timestamp of when the activity was recorded |  [instant](http://hl7.org/fhir/R4/datatypes.html#instant) | _17.0_ |
| agent | Actor involved | [slice](http://hl7.org/fhir/R4/profiling.html#slicing) | _17.0_ |
| agent.type | How the agent participated | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _17.0_ |
| agent.who | Who participated | [Reference](http://hl7.org/fhir/R4/references.html#Reference) ([US Core Practitioner Profile](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-practitioner.html) or [US Core Organization Profile](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization.html) or [US Core Patient Profile](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _17.0_ |
| agent.onBehalfOf | Who the agent is representing | [Reference](http://hl7.org/fhir/R4/references.html#Reference) ([US Core Organization Profile](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization.html)) | _17.0_ |

### Example
<pre class="center-column">
{
    "resourceType": "Provenance",
    "id": "4",
    "meta": {
        "lastUpdated": "2022-08-05T14:29:08.217-04:00"
    },
    "target": [
        {
            "reference": "Immunization/145"
        },
        {
            "reference": "DocumentReference/history-131816"
        }
    ],
    "recorded": "2022-08-05T14:29:08.217-04:00",
    "agent": [
        {
            "type": {
                "coding": [
                    {
                        "system": "http://terminology.hl7.org/CodeSystem/provenance-participant-type",
                        "code": "author",
                        "display": "Author"
                    }
                ],
                "text": "Author"
            },
            "who": {
                "reference": "Practitioner/26546",
                "display": "PortalProvider, PortalProvider"
            },
            "onBehalfOf": {
                "reference": "Organization/47",
                "display": "Pawtucket Plastic Surgeons"
            }
        },
        {
            "type": {
                "coding": [
                    {
                        "system": "http://hl7.org/fhir/us/core/CodeSystem/us-core-provenance-participant-type",
                        "code": "transmitter",
                        "display": "Transmitter"
                    }
                ],
                "text": "Transmitter"
            },
            "who": {
                "reference": "Practitioner/26546",
                "display": "PortalProvider, PortalProvider"
            },
            "onBehalfOf": {
                "reference": "Organization/47",
                "display": "Pawtucket Plastic Surgeons"
            }
        }
    ]
}
</pre>
&nbsp;

### *Get*
Returns a single Provenance result based on the Provenance ID.

#### HTTP Request 
`GET /r4/Provenance/{ProvenanceID}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| ProvenanceID | path | The provenance unique identifier | Yes | _17.0_ |

#### Example: Get a specific provenance based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Provenance/123
</pre>
&nbsp;

### *Search*
Searches for all provenance info based on the given search criteria.

#### HTTP Requests
- `GET /r4/Provenance?{parameters}`
- `POST /r4/Provenance/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _id | query or body | The unique value assigned to each provenance which discerns it from all others |  No | _17.0_ |
| identifier | query or body | The unique value assigned to each provenance which discerns it from all others |  No | _17.0_ |
| _lastUpdated | query or body | The last time the provenance was modified | No | _17.0_ |

**_Note:_**  The possible filter values for the `_lastUpdated` parameter are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

#### Example: Get all provenance info

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Provenance
</pre>
&nbsp;

#### Example: Get a specific provenance based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Provenance?_id=123
</pre>
&nbsp;