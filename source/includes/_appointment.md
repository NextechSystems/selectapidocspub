# Appointment API

## Appointment
### Search
Searches for all appointments matching the given search criteria.

_RESTful searching for appointments by appointment start date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge._

### HTTP Request 
`GET /Appointment?{parameters}`

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| identifier | query | The unique identifier acquired from the appointment search | No | array |
| patient | query | The unique identifier acquired from the patient search | No | array |
| date | query | The collection of appointment date filters | No | array |


### Confirm Appointment
Confirm a scheduled appointment.

### HTTP Request 
`PUT /Appointment/{identifier}` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| identifier | path | The unique identifier of the appointment to be updated | Yes | string |
| commit | body | The object representing the changes to be made | Yes |  |

### Example
`{ "status": "booked" }`