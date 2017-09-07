# Patient API

## Allergy Intolerance
Get a bundle of allergies for a single patient

```GET /{patientUID}/AllergyIntolerance```

**Description:** RESTful searching for allergies by last update date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of allergy last update date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of allergies for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## CCDA Summary
***GET*** 

**Summary:** Get a CCDA summary document for the specified patient

### HTTP Request 
`***GET*** /{patientUid}/Binary/$autogen-ccd-if` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUid | path | The patient's unique identifier (can be found by patient ID search method) | Yes | string |
| start | query | The start date for which the CCD should be generated (if not specified then all records              starting with the patient's first visit are included) | No | dateTime |
| end | query | The end date for which the CCD should be generated (if not specified then all records              through the patient's latest visit are included) | No | dateTime |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a FHIR Binary object containting the base64-ecoded CCDA summary document              https://www.hl7.org/fhir/binary.html |
| 400 | Invalid patient ID provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Care Plan
 ***GET*** 

**Summary:** Get a bundle of care plans for a single patient

**Description:** RESTful searching for care plans by visit date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/CarePlan` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of visit date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of care plans for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Clinical Impression
***GET*** 

**Summary:** Get a bundle of clinical impressions for a patient

**Description:** RESTful searching for clinical impressions by visit date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/ClinicalImpression` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of visit date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of clinical impressions for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Condition
***GET*** 

**Summary:** Get a bundle of conditions for a single patient

**Description:** RESTful searching for conditions by onset date and abatement date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/Condition` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| onset-date | query | The collection of condition onset date filters | No | array |
| abatement-date | query | The collection of condition abatement date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of conditions for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Device
***GET*** 

**Summary:** Get a bundle of devices for a patient

### HTTP Request 
`***GET*** /{patientUID}/Device` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of device effective date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of devices for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Encounter
***GET*** 

**Summary:** Get a bundle of encounters for a single patient

**Description:** RESTful searching for conditions by encounter date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/Encounter` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of encounter date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of encounters for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Reference
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

## Goal
***GET*** 

**Summary:** Get a bundle of goals for a single patient

**Description:** RESTful searching for goals by visit date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/Goal` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of visit date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of goals for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Immunization
***GET*** 

**Summary:** Get a bundle of immunizations for a single patient

**Description:** RESTful searching for current immunizations by administration date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/Immunization` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of current immunization administration date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of immunizations for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Medication Dispensement
***GET*** 

**Summary:** Get a bundle of medication dispensements for a single patient

**Description:** RESTful searching for medication dispensements by preparation date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/MedicationDispense` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| whenprepared | query | The collection of preparation date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of medications for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Medication Statements
***GET*** 

**Summary:** Get a bundle of medication statements for a single patient

**Description:** RESTful searching for medication statements by effective date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/MedicationStatement` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| effective | query | The collection of effective date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of medications for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Observation
***GET*** 

**Summary:** Get a bundle of diagnostic observations for a single patient

**Description:** This request requires a category code to search on. The following category codes are supported:
- laboratory
- social-history
- vital-signs

RESTful searching for observations by date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUid}/Observation` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUid | path | The unique identifier acquired from the patient search | Yes | string |
| category | query | The category of observation to load | Yes | string |
| date | query | The collection of observation obtained date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of diagnostic observations for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Patient
***GET*** 

**Summary:** Get the demographic information for a patient

### HTTP Request 
`***GET*** /{patientUID}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns patient information |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |

## Patient ID Search
 ***GET*** 

**Summary:** Attempts to find a single patient that matches the given search criteria and if
successful returns that patient's unique identifier.

At least one of query parameters is required to perform a search.

### HTTP Request 
`***GET*** /ID` 

**Parameters**

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

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns the patient's unique identifier |
| 400 | No search parameters were specified or the search is not specific enough |
| 404 | No patients met the search criteria |
| 500 | Internal server error |

## Patient Search
 ***GET*** 

**Summary:** Searches for all patients matching the given search criteria. At least one search parameter is required.

Note: The search currently has a limit of 500 patients.

### HTTP Request 
`***GET*** /` 

**Parameters**

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

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns patient objects for the matching patients |
| 400 | No search parameters were specified |
| 404 | No patients met the search criteria |
| 500 | Internal server error |

## Procedure
 ***GET*** 

**Summary:** Get a bundle of procedures for a single patient

**Description:** RESTful searching for procedures by performed date is supported. See https://www.hl7.org/fhir/search.html for instructions on formatting search criteria. The following search prefixes are supported: lt, gt, eq, le, ge, ne.

### HTTP Request 
`***GET*** /{patientUID}/Procedure` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| patientUID | path | The unique identifier acquired from the patient search | Yes | string |
| date | query | The collection of procedure performed date filters | No | array |
| nx-practice-id | header | The unique identifier for a practice | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | Returns a bundle of diagnostic observations for a patient |
| 400 | No supported search parameters provided |
| 404 | Specified patient does not exist |
| 500 | Internal server error |