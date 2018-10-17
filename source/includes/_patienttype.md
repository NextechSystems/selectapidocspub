# Patient-Type

## Patient-Type

### Overview

The patient type resource contains information about a patient and their relation to the practice. Examples include new patient, prospect, deceased.

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| resourcetype | The declaration of the type of resource this is. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _14.2_ |
| id | The unique value assigned to each patient type which discerns it from all others | [string](https://www.hl7.org/fhir/datatypes.html#string) | _14.2_ |
| extension | The patient type values as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.2_ |


### Sample
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 3,
    "entry": [
        {
            "resource": {
                "resourceType": "patient-type",
                "id": "1",
                "extension": [
                    {
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-type#name",
                        "valueString": "Cosmetic"
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-type",
                "id": "2",
                "extension": [
                    {
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-type#name",
                        "valueString": "Insurance Patient"
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-type",
                "id": "3",
                "extension": [
                    {
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-type#name",
                        "valueString": "Spa patient"
                    }
                ]
            }
        }
    ]
}
</pre>
&nbsp;

### *Search*
Searches for all patient types matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /patient-type?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query | The unique identifier for a single patient type | N | _14.2_ |
| name | query | The name of the patient type | N | _14.2_ |

#### Example: Get all patient types

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-type
</pre>
&nbsp;

#### Example: Get all types whose name contains 'Cosmetic'

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-type?name:contains=cosmetic
</pre>
&nbsp;

#### Example: Get a specific patient type based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-type/5
</pre>
#### Response
<pre>
{
    "resourceType": "patient-type",
    "id": "5",
    "extension": [
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-type#name",
            "valueString": "Moved"
        }
    ]
}
</pre>
&nbsp;