# Appointment-Purpose

## Appointment-Purpose

### Overview

The appointment purpose resource provides specific reasons for a planned meeting between a patient and medical provider. Examples include laser skin resurfacing, chemical peel  or microdermabrasion.

Purposes are assigned to meeting types for improved control over appointment availability and scheduling.

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| resourcetype | The declaration of the type of resource this is. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.9_ |
| id | The unique value assigned to each appointment purpose which discerns it from all others | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.9_ |
| extension | The appointment type values that can have this purpose come as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _12.9_ |


### Sample
<pre class="center-column">
{
"resourceType": "appointment-purpose",
        "id": "53",
        "extension": [
            {
                "url": "https://select.nextech-api.com/api/structuredefinition/appointment-purpose",
                "valueString": "Laser Skin Resurfacing"
            },
            {
                "url": "https://select.nextech-api.com/api/structuredefinition/appointment-type",
                "valueReference": {
                    "reference": "appointment-type/13",
                    "display": "Follow Up"
                }
            }
        ]
}
</pre>
&nbsp;

### *Search*
Searches for all appointment purposes matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /appointment-purpose?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query | The unique identifier for a single appointment purpose  | No | _12.9_ |
| name | query | The name of the appointment purpose | No | _12.9_ |

### Appointment-Purpose ID Search
Attempts to find a single appointment purpose that matches based on the identifier given

`GET /appointment-purpose/{identifier}`

