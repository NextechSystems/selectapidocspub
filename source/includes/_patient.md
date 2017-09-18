# Patient API

## Allergy Intolerance
Get a bundle of allergies for a single patient   

RESTful searching for allergies by last update date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request
`GET /Patient/{patientUID}/AllergyIntolerance`

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of allergy last update date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## CCDA Summary
Get a CCDA summary document for the specified patient

### HTTP Request 
`GET /Patient/{patientUid}/Binary/$autogen-ccd-if` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUid | path | The patient's unique identifier (can be found by patient ID search method) | Yes | string |
| start | query | The start date for which the CCD should be generated (if not specified then all records              starting with the patient's first visit are included) | No | dateTime |
| end | query | The end date for which the CCD should be generated (if not specified then all records              through the patient's latest visit are included) | No | dateTime |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Care Plan
Get a bundle of care plans for a single patient   

RESTful searching for care plans by visit date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/CarePlan` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of visit date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Clinical Impression
Get a bundle of clinical impressions for a patient   

RESTful searching for clinical impressions by visit date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/ClinicalImpression` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of visit date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

## Condition
Get a bundle of conditions for a single patient   

RESTful searching for conditions by onset date and abatement date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/Condition` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| onset-date | query | The collection of condition onset date filters | No | array |
| abatement-date | query | The collection of condition abatement date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

## Device
Get a bundle of devices for a patient

### HTTP Request 
`GET /Patient/{patientUID}/Device` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of device effective date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

## Encounter
Get a bundle of encounters for a single patient   

RESTful searching for conditions by encounter date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/Encounter` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of encounter date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Goal
Get a bundle of goals for a single patient   

RESTful searching for goals by visit date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/Goal` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of visit date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Immunization
Get a bundle of immunizations for a single patient   

RESTful searching for current immunizations by administration date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/Immunization` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of current immunization administration date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Medication Dispensement
Get a bundle of medication dispensements for a single patient   

RESTful searching for medication dispensements by preparation date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/MedicationDispense` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| whenprepared | query | The collection of preparation date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Medication Statements
Get a bundle of medication statements for a single patient   

RESTful searching for medication statements by effective date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/MedicationStatement` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| effective | query | The collection of effective date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Observation
Get a bundle of diagnostic observations for a single patient   

This request requires a category code to search on. The following category codes are supported:
- laboratory
- social-history
- vital-signs

RESTful searching for observations by date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUid}/Observation` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUid | path | The unique identifier acquired from the patient search | Yes | string |
| category | query | The category of observation to load | Yes | string |
| date | query | The collection of observation obtained date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Patient
Get the demographic information for a patient

### HTTP Request 
`GET /Patient/{patientUID}` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Patient Search
Searches for all patients matching the given search criteria. At least one search parameter is required.   

Note: The search currently has a limit of 500 patients.

### HTTP Request 
`GET /Patient?:parameters` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| family | query | The family (last) name of the patient | No | string |
| given | query | The given (first) name of the patient | No | string |
| birthdate | query | The patient's date of birth formatted as YYYY-MM-DD | No | dateTime |
| phone | query | The patient's phone number which will be matched against any phone number (home, cell, etc.) | No | string |
| email | query | The patient's email address | No | string |
| address-city | query | The city of the patient's address | No | string |
| address-state | query | The state of the patient's address | No | string |
| address-postalcode | query | The postal (zip) code of the patient's address | No | string |
| identifier | query | The patient's Nextech chart number | No | string |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Patient ID Search
Attempts to find a single patient that matches the given search criteria and if
successful returns that patient's unique identifier.   

At least one of query parameters is required to perform a search.

### HTTP Request 
`GET /Patient/ID` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| family | query | The family (last) name of the patient | No | string |
| given | query | The given (first) name of the patient | No | string |
| birthdate | query | The patient's date of birth formatted as YYYY-MM-DD | No | dateTime |
| phone | query | The patient's phone number which will be matched against any phone number (home, cell, etc.) | No | string |
| email | query | The patient's email address | No | string |
| address-city | query | The city of the patient's address | No | string |
| address-state | query | The state of the patient's address | No | string |
| address-postalcode | query | The postal (zip) code of the patient's address | No | string |
| identifier | query | The patient's Nextech chart number | No | string |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |


## Procedure
Get a bundle of procedures for a single patient   

RESTful searching for procedures by performed date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`GET /Patient/{patientUID}/Procedure` 

### Parameters
| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of procedure performed date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |
