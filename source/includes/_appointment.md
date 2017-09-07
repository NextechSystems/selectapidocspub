# Appointment API

## Appointment
***GET*** 

**Summary:** Get a bundle of appointments

**Description:** RESTful searching for appointments by appointment start date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge.

### HTTP Request 
`***GET*** /` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| identifier | query | The unique identifier acquired from the appointment search | No | array |
| patient | query | The unique identifier acquired from the patient search | No | array |
| date | query | The collection of appointment date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of appointments |
| 400 | No supported search parameters provided |
| 404 | Specified patient or patient appointments do not exist |
| 500 | Internal server error |

/{IDENTIFIER}
***PUT*** 

**Summary:** Update an existing appointment's status

### HTTP Request 
`***PUT*** /{identifier}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| identifier | path | The unique identifier of the appointment to be updated | Yes | string |
| commit | body | The object representing the changes to be made | Yes |  |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns acknowledgement of success |
| 400 | No supported search parameters provided or invalid |
| 404 | Specified appointment does not exist |
| 500 | Internal server error |

/REFERENCE
***GET*** 

### HTTP Request 
`***GET*** /Reference` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

/ERROR
***GET*** 

### HTTP Request 
`***GET*** /Error` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| errorCode | query |  | Yes | string |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | OK |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
