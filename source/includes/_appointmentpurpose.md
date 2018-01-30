# Appointment-Purpose

## Appointment-Purpose

### Overview

The Appointment Purpose resource provides specific reasons for that a planned meeting between a patient and medical provider. Examples include new patient encounters, scheduled surgeries and and follow-up visits.


Purposes are assigned to meeting types for improved control over appointment availability and scheduling

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| resourceType | The declaration of the Type of resource this is. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| id | The unique value assigned to each appointment purpose which discerns it from all others | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| Extension | The Appointment Type values as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _12.8_ |


### Sample
<pre class="center-column">
{
"resourceType": "appointment-Purpose",
        "id": "53",
        "extension": [
            {
                "url": "https://select.nextech-api.com/api/structuredefinition/appointment-purpose",
                "valueString": "Other"
            },
            {
                "url": "https://select.nextech-api.com/api/structuredefinition/appointment-type",
                "valueReference": {
                    "reference": "appointment-type/13",
                    "display": "Misc"
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
| id | query | The unique identifier for a single appointment purpose  | No | _12.8_ |
| name | query | The name of the appointment purpose | No | _12.8_ |



