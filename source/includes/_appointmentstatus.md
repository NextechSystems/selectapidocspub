# Appointment-Status

## Appointment-Status

### Overview

The appointment status resource contains information about a planned meeting between a patient and medical provider. Examples include new patient encounters, scheduled surgeries and and follow-up visits.

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| resourcetype | The declaration of the type of resource this is. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _15.9_ |
| id | The unique value assigned to each appointment status which discerns it from all others | [string](https://www.hl7.org/fhir/datatypes.html#string) | _15.9_ |
| extension | The appointment status values as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _15.9_ |


### Sample
<pre class="center-column">
{
    "resourceType": "appointment-status",
    "id": "10",
    "extension": [
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/appointment-status#name",
            "valueString": "Online Book"
        }
    ]
}
</pre>
&nbsp;

### *Search*
Searches for all appointment statuses matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /appointment-status?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query | The unique identifier for a single appointment status | N | _15.9_ |
| name | query | The name of the appointment status | N | _15.9_ |


### Appointment-Status ID Search
Attempts to find a single appointment status that matches based on the identifier given

`GET /appointment-status/{identifier}`
