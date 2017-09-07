# Introduction

The Nextech Select Open API is a RESTful implementation based on the STU 3 (3.0.1) version of the [FHIR® standard](https://www.hl7.org/fhir/index.html).

Although the FHIR® standard supports both JSON and XML, this API currently only supports JSON.  Therefore any type explicitly defined in the request's `Accept` header will be ignored.

## Pagination

_Applies to: Patient API • Appointment API_

## Errors

_Applies to: Patient API • Appointment API_

| Code | Description |
| ---- | ----------- |
| 200 | OK - Successful request |
| 400 | Bad Request - The request is missing information or is malformed |
| 403 | Forbidden - The request is valid, but the server is refusing action |
| 404 | Not Found - The requested resource cannot be found |
| 500 | Internal Server Error - We had a problem with our server |