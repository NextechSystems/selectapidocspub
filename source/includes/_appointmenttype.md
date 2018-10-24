# Appointment-Type

## Appointment-Type

### Overview

The appointment type resource contains information about a planned meeting between a patient and medical provider. Examples include new patient encounters, scheduled surgeries and and follow-up visits.

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| resourcetype | The declaration of the type of resource this is. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| id | The unique value assigned to each appointment type which discerns it from all others | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| extension | The appointment type values as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _12.8_ |


### Sample
<pre class="center-column">
{
    "resourceType": "appointment-type",
    "id": "9",
    "extension": [
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/appointment-type#name",
            "valueString": "Surgery Cosmetic"
        }
    ]
}
</pre>
&nbsp;

### *Search*
Searches for all appointment types matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /appointment-type?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query | The unique identifier for a single appointment type | N | _12.8_ |
| name | query | The name of the appointment type | N | _12.8_ |


### Appointment-Type ID Search
Attempts to find a single appointment type that matches based on the identifier given

`GET /appointment-type/{identifier}`
