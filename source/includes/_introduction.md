# Introduction

The Nextech Select Open API is a RESTful implementation based on the STU 3 (3.0.1) version of the [FHIR® standard](https://www.hl7.org/fhir/index.html).

All communication is performed over HTTPS. Although the FHIR® standard supports both JSON and XML, this API currently only supports JSON.  Therefore any type explicitly defined in the request's `Accept` header will be ignored.

## Search

Searches may be performed via HTTPS calls to the API where supported. Each request must have the following information in the header: (TODO)

A search is executed by performing a GET operation in the RESTful framework   
`GET https://link-to-the-api/PartnerAPI/[type]?[field1]=[value1]&[field2]=[value2]...`   
where \[type\] refers to a resource such as Patient or Appointment followed by one or more query filters.

### Example   
`GET https://link-to-the-api/PartnerAPI/Patient?identifier=3442`   
`GET https://link-to-the-api/PartnerAPI/Patient?family=Smith`   
`GET https://link-to-the-api/PartnerAPI/Patient?address-city=Tampa&address-state=FL`   

## Writing

Data writes may be performed via HTTPS calls to the API where supported. Each request must have the following information in the header: (TODO)

A write is executed by performing a PUT operation in the RESTful framework
`PUT https://link-to-the-api/PartnerAPI/[type]/[identifier]`
where \[type\] refers to a resource such as Patient or Appointment, \[identifier\] is the unique identifier of the resource and the body of the request describes a resource and which fields to add or change. This example request path and body would confirm an appointment with the ID 3384:   

### Example   
`PUT https://link-to-the-api/PartnerAPI/Appointment/3384`   
`Body: { "status": "fulfilled" }`

## Pagination

_Applies to: Patient API • Appointment API_

When a search results in multiple matches, the first ten matches ordered by entered date are returned by default. Included in the result are links to the first set of matches, the following set of matches, the previous set of matches and the last set of matches.

You may overide the number of matches returned, up to fifty, by including `_count=[number]` in your search. 

`GET http://link-to-the-api/PartnerAPI/Appointment?_count=25`

Search results are limited to fifty matches per page.

## Errors

_Applies to: Patient API • Appointment API_

| Code | Description |
| ---- | ----------- |
| 200 | OK - Successful request |
| 400 | Bad Request - The request is missing information or is malformed |
| 403 | Forbidden - The request is valid, but the server is refusing action |
| 404 | Not Found - The requested resource cannot be found |
| 500 | Internal Server Error - We had a problem with our server |
