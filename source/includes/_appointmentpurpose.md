# Appointment-Purpose

## Appointment-Purpose

### Overview

The Appointment Purpose resource contains information about a planned meeting between a patient and medical provider. Examples include new patient encounters, scheduled surgeries and and follow-up visits.


Purposes are assigned to meeting types for improved control over appointment availability and scheduling

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| resourceType | The Declaration of the Type of resource this is. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| id | The unique value assigned to each appointment which discerns it from all others | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| Extension | The Appointment Type values as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _12.8_ |


### Sample
<pre class="center-column">
{
		"resourceType": "appointment-Purpose",
                "id": "53",
                "extension": [
                    {
                        "url": "https://select.nextech-api.com/api/structuredefinition/appointment-Purpose#name",
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
Searches for all Appointment Purposes matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /appointment-Purpose?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query | The unique identifier for a single Appointment Purpose | No | _12.8_ |



