
# Patient

### Overview
The [patient](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html) resource contains information about the demographics of a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique identifier of the patient | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| identifier | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number. <br/><br/> As a convenience for some use cases, in version 14.1 and above, the patient's masked social security number (last four only) is also returned in this field if available. | [Identifier](http://hl7.org/fhir/R4/datatypes.html#Identifier) | _12.6_ |
| extension:race | The race of the patient | [Extension](http://hl7.org/fhir/R4/extensibility.html#Extension) ([US Core Race Extension](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-race.html)) | _12.6_ |
| extension:ethnicity | The ethnicity of the patient | [Extension](http://hl7.org/fhir/R4/extensibility.html#Extension) ([US Core Ethnicity Extension](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-ethnicity.html)) | _12.6_ |
| extension:birthsex | The patient's sex assigned at birth | [Extension](http://hl7.org/fhir/R4/extensibility.html#Extension) ([US Core Birth Sex Extension](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-birthsex.html)) | |
| name | Names of the patient, additional information including prefix and nickname added in version 12.9.20. Other patient names are also returned here starting in 16.9 | [HumanName](http://hl7.org/fhir/R4/datatypes.html#HumanName) | _12.6_ |
| telecom | Contact details for the patient, fax, preferred contact, and other phone added 12.9.20 | [ContactPoint](http://hl7.org/fhir/R4/datatypes.html#ContactPoint) | _12.6_ |
| gender | The gender of the patient | [code](http://hl7.org/fhir/R4/datatypes.html#code) | _12.6_ |
| birthDate | The date of birth of the patient | [date](http://hl7.org/fhir/R4/datatypes.html#date) | _12.6_ |
| address | Addresses associated with the patient. Previous patient addresses are also returned here starting in 16.9 | [Address](http://hl7.org/fhir/R4/datatypes.html#Address) | _12.6_ |
| communication | A list of Languages which may be used to communicate with the patient about his or her health | [BackboneElement](http://hl7.org/fhir/R4/datatypes.html#BackboneElement) | _12.6_ |


### Example
<pre class="center-column">
{
    "resourceType": "Patient",
    "id": "b664fd37-ff5f-4022-9d71-2e476d42f316",
    "extension": [
        {
            "extension": [
                {
                    "url": "ombCategory",
                    "valueCoding": {
                        "system": "urn:oid:2.16.840.1.113883.6.238",
                        "code": "2054-5",
                        "display": "Black or African American"
                    }
                },
                {
                    "url": "text",
                    "valueString": "Black or African American"
                }
            ],
            "url": "http://hl7.org/fhir/us/core/StructureDefinition/us-core-race"
        },
        {
            "extension": [
                {
                    "url": "detailed",
                    "valueCoding": {
                        "system": "urn:oid:2.16.840.1.113883.6.238",
                        "code": "2072-7",
                        "display": "Jamaican"
                    }
                },
                {
                    "url": "text",
                    "valueString": "Jamaican"
                }
            ],
            "url": "http://hl7.org/fhir/us/core/StructureDefinition/us-core-race"
        },
        {
            "extension": [
                {
                    "url": "ombCategory",
                    "valueCoding": {
                        "system": "urn:oid:2.16.840.1.113883.6.238",
                        "code": "2186-5",
                        "display": "Not Hispanic or Latino"
                    }
                },
                {
                    "url": "text",
                    "valueString": "Not Hispanic or Latino"
                }
            ],
            "url": "http://hl7.org/fhir/us/core/StructureDefinition/us-core-ethnicity"
        },
        {
            "url": "http://hl7.org/fhir/us/core/StructureDefinition/us-core-birthsex",
            "valueCode": "M"
        }
    ],
    "identifier": [
        {
            "use": "official",
            "system": "",
            "value": "b664fd37-ff5f-4022-9d71-2e476d42f316"
        },
        {
            "use": "usual",
            "system": "",
            "value": "112334"
        }
    ],
    "name": [
        {
            "use": "official",
            "text": "John Jacob Smith",
            "family": "Smith",
            "given": [
                "John",
                "Jacob"
            ],
            "suffix": [
                ""
            ]
        }
    ],
    "telecom": [
        {
            "system": "email",
            "value": "example@nextech.com"
        },
        {
            "system": "phone",
            "value": "(763) 560-8033",
            "use": "home"
        }
    ],
    "gender": "male",
    "birthDate": "1952-06-13",
    "address": [
        {
            "use": "home",
            "type": "both",
            "line": [
                "4807 89th Ave N"
            ],
            "city": "Brooklyn Park",
            "state": "MN",
            "postalCode": "55443",
            "country": "USA"
        }
    ],
    "communication": [
        {
            "language": {
                "coding": [
                    {
                        "system": "urn:ietf:bcp:47",
                        "code": "en",
                        "display": "English"
                    }
                ],
                "text": "English"
            },
            "preferred": true
        }
    ]
}
</pre>
&nbsp;

### Contact Information and Privacy
The telecom section contains the contact information for the patient. The example above shows the complete response based on what information is on file and which privacy settings
are set. If the Privacy setting is checked then the checked fields will not be sent over the API even though the contact information is on file.

i.e The patient's **work** number is on file, but marked private then the telecom section will not contain the **work** field.


The preferred contact is also available from the API. If a preferred contact is set then it will contain a "rank":1 member in the telecom object indicating it is the preferred method.

### *Search*
Searches for all patients matching the given search criteria. See [https://www.hl7.org/fhir/R4/search.html](https://www.hl7.org/fhir/R4/search.html) for instructions on formatting search criteria.

#### HTTP Request 
- `GET /r4/Patient?{parameters}`
- `POST /r4/Patient/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Type | Initial Version |
| ---- | ---------- | ----------- | -------- | ---- | --------------- |
| _lastUpdated | query or body| The date the patient was last modified formatted as yyyy-MM-dd. As of version 14.3, we also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] | No | [dateTime](https://hl7.org/fhir/R4/datatypes.html#dateTime) | _12.8_ |
| family | query or body| The family (last) name of the patient | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| given | query or body| The given (first) name of the patient | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| birthdate | query or body| The patient's date of birth formatted as YYYY-MM-DD | No | [dateTime](https://hl7.org/fhir/R4/datatypes.html#dateTime) | _12.6_ |
| phone | query or body| The patient's phone number which will be matched against any phone number (home, cell, etc.) | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| email | query or body| The patient's email address | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| address-city | query or body| The city of the patient's address | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| address-state | query or body| The state of the patient's address | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| address-postalcode | query or body| The postal (zip) code of the patient's address | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| name | query or body| The given(first) name, middle name, family(last) name, prefix or title of the patient | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | 12.6 |
| identifier | query or body| The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| _id | query or body| The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| gender | query or body| The gender of the patient | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| group-id | query or body| The letter writing group of the patient | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | 16.8 |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that relate to each patient | No | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _17.0_ |

#### Retrieve Provenance with patients
The `_revinclude` parameter allows support for including Provenance references that match the returned patient.
This value must be `Provenance:target`, otherwise the request will result in an error.
These will be in additional bundle entry components, which have a `Provenance.Target` entry that identifies the relative link to the patient.

#### Example: Get the patient of a specific chart number

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient/12345
</pre>
&nbsp;

#### Example: Get all patients

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient
</pre>
&nbsp;

#### Example: Get all patients with identifier '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?identifier=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>body:</small></i> identifier=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?_id=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>body:</small></i> _id=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

#### Example: Get all patients with identifier '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192' with provenance

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?identifier=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&_revinclude=Provenance:target
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>body:</small></i> identifier=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&_revinclude=Provenance:target
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?_id=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&_revinclude=Provenance:target
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>body:</small></i> _id=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&_revinclude=Provenance:target
</pre>

#### Example: Get all patients who live within '12345' zip code

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?address-postalcode=12345
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>body:</small></i> address-postalcode=12345
</pre>

#### Example: Get all patients with birth dates between and including 1/1/1981 through 5/31/1981

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?birthdate=ge1981-01-01&birthdate=lt1981-05-31
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>body:</small></i> birthdate=ge1981-01-01&birthdate=lt1981-05-31
</pre>

### Patient ID Search
Attempts to find patient IDs that match the given search criteria and, if
successful, returns those patients' unique identifiers.   

### HTTP Request 
`GET /r4/Patient/ID?{parameters}` 

### Parameters
| Name | Located in | Description | Required | Type | Initial Version |
| ---- | ---------- | ----------- | -------- | ---- | --------------- |
| group-id | query | The letter writing group of the patient | No | string | 16.8 |

#### Example: Get the unique identifiers of all patients that are in a letter writing group with an ID of 20

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient/ID?group-id=20
</pre>
&nbsp;


## Allergy Intolerance

### Overview
The [allergy intolerance](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-allergyintolerance.html) resource describes the risk of undesirable responses of exposure to a substance.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The logical id of the resource, as used in the URL for the resource. | [string](http://hl7.org/fhir/R4/datatypes.html#string) | 12.6 |
| identifier | The unique value assigned to each allergy intolerance record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _12.6_ |
| clinicalStatus | Describes whether the allergy or intolerance is active, inactive or resolved | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) |  12.6 |
| verificationStatus | Assertion about certainty associated with the propensity, or potential risk, of a reaction to the identified substance (including pharmaceutical product). | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | 12.6 |
| code | The clinical code that identifies the allergy or intolerance | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _12.6_ |
| patient | The patient who the allergy or intolerance is for | [Reference](http://hl7.org/fhir/R4/references.html#Reference) [(US Core Patient Profile)](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html) | _12.6_ |
| reaction | Details about each adverse reaction event linked to exposure to the identified substance. | [BackboneElement](http://hl7.org/fhir/R4/datatypes.html#BackboneElement) | 12.6 |
| reaction.manifestation | Clinical symptoms and/or signs that are observed or associated with the adverse reaction event. |  [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | 12.6 |

### Example
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 1,
    "entry": [
        {
            "resource": {
                "resourceType": "AllergyIntolerance",
                "id": "21",
                "identifier": [
                    {
                        "use": "official",
                        "value": "21"
                    }
                ],
                "clinicalStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/allergyintolerance-clinical",
                            "code": "active"
                        }
                    ]
                },
                "verificationStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/allergyintolerance-verification",
                            "code": "unconfirmed"
                        }
                    ]
                },
                "code": {
                    "coding": [
                        {
                            "system": "http://www.nlm.nih.gov/research/umls/rxnorm",
                            "code": "852519",
                            "display": "house dust"
                        }
                    ],
                    "text": "house dust"
                },
                "patient": {
                    "reference": "Patient/b664fd37-ff5f-4022-9d71-2e476d42f316",
                    "display": "Smith, John Jacob"
                },
                "reaction": [
                    {
                        "manifestation": [
                            {
                                "coding": [
                                    {
                                        "system": "http://snomed.info/sct",
                                        "code": "25064002",
                                        "display": "Headache"
                                    }
                                ],
                                "text": "Headache"
                            }
                        ]
                    }
                ]
            }
        }
    ]
}
</pre>
&nbsp;
### *Search*
Searches for allergy intolerances for a single patient

#### HTTP Requests
- `GET /r4/Patient/{patientUid}/AllergyIntolerance?{parameters}`
- `GET /r4/AllergyIntolerance?{parameters}`
- `POST /r4/Patient/AllergyIntolerance/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`




#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or body | The unique identifier of the allergy intolerance | No | 16.7 |
| _id | query or body | The unique identifier of the allergy intolerance | No | 16.7 |
| patientUid | path | The official patient identifier acquired from a patient search | No | _12.6_ |
| patient | query or body | The patient who the allergy or intolerance is for | No | 12.6
| _lastUpdated | query or body | The date the allergy intolerance was last modified, formatted as OOXXXXX where OO is an operator and XXXXX is a date in the form YYYY-MM-DD  | No | _12.6_ |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional `Provenance` resources that relate to each document reference | No | _17.0_ |
**_Note:_**  The possible filter values for _lastUpdated parameter are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

&nbsp;
#### Examples: 

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient/b664fd37-ff5f-4022-9d71-2e476d42f316/AllergyIntolerance?_lastUpdated=ge2022-01-01
</pre>
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/AllergyIntolerance?patient=b664fd37-ff5f-4022-9d71-2e476d42f316
</pre>
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/AllergyIntolerance?patient=Patient/b664fd37-ff5f-4022-9d71-2e476d42f316
</pre>
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/AllergyIntolerance/_search
<i><small>body:</small></i> patient=b664fd37-ff5f-4022-9d71-2e476d42f316
</pre>
&nbsp;

### *Get*
Returns single Allergy result based on the Allergy ID.

#### HTTP Request

- `GET /r4/AllergyIntolerance/{allergyID}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| allergyID | path | The allergy unique identifier | Yes | 16.7 |

&nbsp;
#### Example: 
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/AllergyIntolerance/21
</pre>

&nbsp;

## Care Plan

### Overview
A [Care Plan](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-careplan.html) contains patient diet, procedure, lab work and counseling and other care information for a single patient.   

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique value assigned to each care plan which discerns them from all others. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.9_ |
| subject | The patient pertaining to the care plan. | [Reference](https://www.hl7.org/fhir/R4/references.html)([US Core Patient Profile](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.9_ |
| text | A human-readable narrative that contains a summary of the resource. | [Narrative](http://hl7.org/fhir/R4/datatypes.html#Narrative) | _16.9_ |
| text.div | The actual narrative content of the patient care plan. | [xhtml](http://hl7.org/fhir/R4/narrative.html#xhtml) | _16.9_ |
| text.status | The text status for the resource narrative. | [code](http://hl7.org/fhir/R4/datatypes.html#code) | _16.9_ |
| category | The type of the care plan. | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| status | Indicates whether the plan is currently being acted upon, represents future intentions or is now a historical record. | [code](http://hl7.org/fhir/R4/datatypes.html#code)  | _16.9_ |
| intent | Indicates the level of intentionality associated with the care plan (proposal, plan, order, option). | [code](http://hl7.org/fhir/R4/datatypes.html#code)  | _16.9_ |

### Example
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 4,
    "entry": [
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "672",
                "text": {
                    "status": "additional",
                    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">Get an EKG done on 6/23/2015.</div>"
                },
                "status": "active",
                "intent": "order",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://hl7.org/fhir/us/core/CodeSystem/careplan-category",
                                "code": "assess-plan"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
                    "display": "Newman, Alice Jones"
                }
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "674",
                "text": {
                    "status": "additional",
                    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">Get a Chest X-ray done on 6/23/2015 showing the Lower Respiratory Tract Structure.</div>"
                },
                "status": "active",
                "intent": "plan",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://hl7.org/fhir/us/core/CodeSystem/careplan-category",
                                "code": "assess-plan"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
                    "display": "Newman, Alice Jones"
                }
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "678",
                "text": {
                    "status": "additional",
                    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">Take Clindamycin 300mg three times a day as needed if pain does not subside/</div>"
                },
                "status": "active",
                "intent": "proposal",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://hl7.org/fhir/us/core/CodeSystem/careplan-category",
                                "code": "assess-plan"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
                    "display": "Newman, Alice Jones"
                }
            }
        },
        {
            "resource": {
                "resourceType": "CarePlan",
                "id": "676",
                "text": {
                    "status": "additional",
                    "div": "<div xmlns=\"http://www.w3.org/1999/xhtml\">Schedule follow on visit with Neighborhood Physicians Practice on 7/1/2015.</div>"
                },
                "status": "active",
                "intent": "plan",
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://hl7.org/fhir/us/core/CodeSystem/careplan-category",
                                "code": "assess-plan"
                            }
                        ]
                    }
                ],
                "subject": {
                    "reference": "Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
                    "display": "Newman, Alice Jones"
                }
            }
        }
    ]
}
</pre>
&nbsp;

### *Get*
Returns a single Care Plan result based on the Care Plan ID.

#### HTTP Request 
`GET /r4/CarePlan/{carePlanId}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| carePlanId | path | The unique identifier for the care plan | Yes | _16.9_ |

#### Example: Get the care plan with an ID of '676'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CarePlan/676
</pre>
&nbsp;

### *Search*
Searches for care plans for a single patient

#### HTTP Requests

- `GET /r4/CarePlan?{parameters}`
- `POST /r4/CarePlan/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patient | query or body | The official patient identifier acquired from a patient search | No | _16.9_ |
| _id | query or body | The unique identifier for the care plan | No | _16.9_ |
| identifier | query or body | The unique identifier for the care plan | No | _16.9_ |
| category | query or body | The type of the care plan. Ex.: 'assess-plan' | No | _16.9_ |
| _lastUpdated | query or body | The date the care plan was last modified, formatted as OOXXXXX where OO is an operator and XXXXX is a date in the form YYYY-MM-DD. | No | _16.9_ |
| _revinclude | query or body | Must be `Provenance:target`. This enables requesting additional `Provenance` resources that relate to each care plan | No | _16.9_ |

**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

#### Retrieve Provenance with care plans
The `_revinclude` parameter allows support for including Provenance references that match the returned care plans.
This value must be `Provenance:target`, otherwise the request will result in an error.
These will be in additional bundle entry components, which have a `Provenance.Target` entry that identifies the relative link to the care plan.

#### Example: Get all care plans for a single patient with id 'c27e5be0-4b44-4ec5-a284-4308d6ac2b1a' and category 'assess-plan'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CarePlan?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&category=assess-plan
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CarePlan?patient=Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&category=assess-plan
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CarePlan?patient=Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&category=http://hl7.org/fhir/us/core/CodeSystem/careplan-category|assess-plan
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/CarePlan/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&category=assess-plan
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/CarePlan/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&category=http://hl7.org/fhir/us/core/CodeSystem/careplan-category|assess-plan
</pre>
&nbsp;

#### Example: Get all care plans for a single patient that were modified as of 5/5/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CarePlan?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_lastUpdated=ge2022-05-05
</pre>
&nbsp;

#### Example: Get all care plans that were modified by 5/5/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CarePlan?_lastUpdated=le2022-05-05
</pre>
&nbsp;


## Care Team

### Oveview
The [CareTeam](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-careteam.html) resource includes all the people and organizations who plan to participate in the coordination and delivery of care for a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique value assigned to each care team which discerns them from all others. | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _16.9_ |
| status | Indicates the current state of the care team. | [code](http://hl7.org/fhir/R4/datatypes.html#code) | _16.9_ |
| subject | Identifies the patient or group whose intended care is handled by the team. | [Reference](http://hl7.org/fhir/R4/references.html#Reference)[(US Core Patient Profile)](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html) | _16.9_ |
| participant.role | Indicates specific responsibility of an individual within the care team, such as "Primary care physician", "Caregiver", etc. | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| participant.member | The specific person or organization who is participating/expected to participate in the care team. |	[Reference](http://hl7.org/fhir/R4/references.html#Reference) ([US Core Patient Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html) or [US Core Practitioner Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-practitioner.html) or [US Core Organization Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization.html))| _16.9_ |


### Example
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 1,
    "link": [
        {
            "relation": "self",
            "url": "https://localhost:44304/api/r4/CareTeam?patient=C27E5BE0-4B44-4EC5-A284-4308D6AC2B1A"
        },
        {
            "relation": "previous",
            "url": "https://localhost:44304/api/r4/CareTeam?patient=C27E5BE0-4B44-4EC5-A284-4308D6AC2B1A&_getpagesoffset=0&_count=10"
        },
        {
            "relation": "next",
            "url": "https://localhost:44304/api/r4/CareTeam?patient=C27E5BE0-4B44-4EC5-A284-4308D6AC2B1A&_getpagesoffset=0&_count=10"
        },
        {
            "relation": "first",
            "url": "https://localhost:44304/api/r4/CareTeam?patient=C27E5BE0-4B44-4EC5-A284-4308D6AC2B1A&_getpagesoffset=0&_count=10"
        },
        {
            "relation": "last",
            "url": "https://localhost:44304/api/r4/CareTeam?patient=C27E5BE0-4B44-4EC5-A284-4308D6AC2B1A&_getpagesoffset=0&_count=10"
        }
    ],
    "entry": [
        {
            "resource": {
                "resourceType": "CareTeam",
                "id": "3",
                "status": "active",
                "subject": {
                    "reference": "Patient/3",
                    "display": "Newman,  Alice Jones"
                },
                "participant": [
                    {
                        "role": [
                            {
                                "coding": [
                                    {
                                        "system": "http://nucc.org/provider-taxonomy",
                                        "code": "2086S0122X"
                                    }
                                ]
                            }
                        ],
                        "member": {
                            "reference": "Practitioner/5",
                            "display": "Davis, Albert"
                        }
                    },
                    {
                        "role": [
                            {
                                "coding": [
                                    {
                                        "system": "http://hl7.org/fhir/StructureDefinition/data-absent-reason",
                                        "code": "unknown"
                                    }
                                ]
                            }
                        ],
                        "member": {
                            "reference": "Practitioner/77",
                            "display": "Davis, Tracy"
                        }
                    },
                    {
                        "role": [
                            {
                                "coding": [
                                    {
                                        "system": "http://snomed.info/sct",
                                        "code": "116154003"
                                    }
                                ]
                            }
                        ],
                        "member": {
                            "reference": "Patient/3",
                            "display": "Newman,  Alice Jones"
                        }
                    }
                ]
            }
        }
    ]
}
</pre>
&nbsp;

### *Get*
Returns a single Care Team result based on the Care Team ID.

#### HTTP Request 
`GET /r4/CareTeam/{careTeamId}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| careTeamId | path | The unique identifier for the care team | Yes | _16.9_ |

#### Example: Get the care team with an ID of '3'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CareTeam/3
</pre>
&nbsp;

### *Search*
Searches for care teams for a single patient

#### HTTP Requests

- `GET /r4/CareTeam?{parameters}`
- `POST /r4/CareTeam/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patient | query or body | The official patient identifier acquired from a patient search | No | _16.9_ |
| _id | query or body | The unique identifier for the care team | No | _16.9_ |
| identifier | query or body | The unique identifier for the care team | No | _16.9_ |
| status | query or body | Indicates the current state of the care team. Ex.: 'active' | No | _16.9_ |
| _lastUpdated | query or body | The date the care team was last modified, formatted as OOXXXXX where OO is an operator and XXXXX is a date in the form YYYY-MM-DD. | No | _16.9_ |

**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 


#### Example: Get all care teams for a single patient with id 'c27e5be0-4b44-4ec5-a284-4308d6ac2b1a' and status 'active'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CareTeam?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&status=active
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CareTeam?patient=Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&status=active
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CareTeam?patient=Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&status=http://hl7.org/fhir/ValueSet/care-team-status|active
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/CareTeam/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&status=active
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/CareTeam/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&status=http://hl7.org/fhir/ValueSet/care-team-status|active
</pre>
&nbsp;

#### Example: Get all care teams for a single patient that were modified as of 5/5/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CareTeam?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_lastUpdated=ge2022-05-05
</pre>
&nbsp;

#### Example: Get all care teams that were modified by 5/5/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/CareTeam?_lastUpdated=le2022-05-05
</pre>
&nbsp;

## Condition

### Overview
The [condition](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-condition.html) resource describes a certain state of health of a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique value assigned to each condition record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _16.8_ |
| clinicalStatus | The condition status | [Condition Clinical Status Code](https://www.hl7.org/fhir/R4/valueset-condition-clinical.html) | _16.8_ |
| verificationStatus | The condition verification status | [Condition Verification Status](https://www.hl7.org/fhir/R4/valueset-condition-ver-status.html) | _16.8_ |
| category | A category assigned to the condition | [Condition Category Code](http://hl7.org/fhir/us/core/STU3.1.1/ValueSet/us-core-condition-category) | _16.8_ |
| code | Identification of the condition, problem or diagnosis | [Condition/Problem/Diagnosis Code](https://www.hl7.org/fhir/R4/valueset-condition-code.html) | _16.8_ |
| subject | The patient pertaining to the condition | [Reference](https://www.hl7.org/fhir/R4/references.html)([US Core Patient Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.8_ |

### Example
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 3,
    "link": [
        {
            "relation": "self",
            "url": "https://localhost:44304/api/r4/Condition?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a"
        },
        {
            "relation": "previous",
            "url": "https://localhost:44304/api/r4/Condition?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_getpagesoffset=0&_count=10"
        },
        {
            "relation": "next",
            "url": "https://localhost:44304/api/r4/Condition?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_getpagesoffset=0&_count=10"
        },
        {
            "relation": "first",
            "url": "https://localhost:44304/api/r4/Condition?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_getpagesoffset=0&_count=10"
        },
        {
            "relation": "last",
            "url": "https://localhost:44304/api/r4/Condition?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_getpagesoffset=0&_count=10"
        }
    ],
    "entry": [
        {
            "resource": {
                "resourceType": "Condition",
                "id": "prb-12",
                "clinicalStatus": {
                    "coding": [
                        {
                            "system": "http://hl7.org/fhir/ValueSet/condition-clinical",
                            "code": "resolved",
                            "display": "Resolved"
                        }
                    ],
                    "text": "Resolved"
                },
                "verificationStatus": {
                    "coding": [
                        {
                            "system": "http://hl7.org/fhir/ValueSet/condition-ver-status",
                            "code": "confirmed",
                            "display": "Confirmed"
                        }
                    ],
                    "text": "Confirmed"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://hl7.org/fhir/us/core/ValueSet/us-core-condition-category",
                                "code": "problem-list-item",
                                "display": "Problem List Item"
                            }
                        ],
                        "text": "Problem List Item"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "238131007",
                            "display": "Overweight"
                        }
                    ],
                    "text": "Overweight"
                },
                "subject": {
                    "reference": "Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
                    "display": "Newman, Alice Jones"
                }
            }
        },
        {
            "resource": {
                "resourceType": "Condition",
                "id": "prb-10",
                "clinicalStatus": {
                    "coding": [
                        {
                            "system": "http://hl7.org/fhir/ValueSet/condition-clinical",
                            "code": "active",
                            "display": "Active"
                        }
                    ],
                    "text": "Active"
                },
                "verificationStatus": {
                    "coding": [
                        {
                            "system": "http://hl7.org/fhir/ValueSet/condition-ver-status",
                            "code": "confirmed",
                            "display": "Confirmed"
                        }
                    ],
                    "text": "Confirmed"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://hl7.org/fhir/us/core/ValueSet/us-core-condition-category",
                                "code": "problem-list-item",
                                "display": "Problem List Item"
                            }
                        ],
                        "text": "Problem List Item"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "83986005",
                            "display": "Severe hypothyroidism"
                        }
                    ],
                    "text": "Severe hypothyroidism"
                },
                "subject": {
                    "reference": "Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
                    "display": "Newman, Alice Jones"
                }
            }
        },
        {
            "resource": {
                "resourceType": "Condition",
                "id": "hc-616",
                "clinicalStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/condition-clinical",
                            "code": "active",
                            "display": "Active"
                        }
                    ],
                    "text": "Active"
                },
                "verificationStatus": {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/condition-ver-status",
                            "code": "confirmed",
                            "display": "Confirmed"
                        }
                    ],
                    "text": "Confirmed"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://hl7.org/fhir/us/core/CodeSystem/condition-category",
                                "code": "health-concern",
                                "display": "Health Concern"
                            }
                        ],
                        "text": "Health Concern"
                    }
                ],
                "code": {
                    "coding": [
                        {
                            "system": "http://snomed.info/sct",
                            "code": "236578006",
                            "display": "Chronic rejection of renal transplant"
                        }
                    ],
                    "text": "Chronic rejection of renal transplant"
                },
                "subject": {
                    "reference": "Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
                    "display": "Newman, Alice Jones"
                }
            }
        }
    ]
}
</pre>
&nbsp;

### *Get*
Returns a single Condition result based on the Condition ID.

#### HTTP Request 
`GET /r4/Condition/{conditionId}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| conditionId | path | The unique identifier for the condition | Yes | _16.8_ |

#### Example: Get the condition problem with an ID of 'prb-12'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Condition/prb-12
</pre>
&nbsp;


### *Search*
Searches for conditions for a single patient

#### HTTP Requests

- `GET /r4/Condition?{parameters}`
- `POST /r4/Condition/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patient | query or body | The official patient identifier acquired from a patient search | Yes | _16.8_ |
| _id | query or body | The unique identifier for the condition | No | _16.8_ |
| identifier | query or body | The unique identifier for the condition | No | _16.8_ |   
| _lastUpdated | query or body | The date the condition was last modified, formatted as OOXXXXX where OO is an operator and XXXXX is a date in the form YYYY-MM-DD. | No | _16.8_ |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that relate to each condition | No | string | _17.0_ |

**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

#### Retrieve Provenance with conditions
The `_revinclude` parameter allows support for including Provenance references that match the returned condition.
This value must be `Provenance:target`, otherwise the request will result in an error.
These will be in additional bundle entry components, which have a `Provenance.Target` entry that identifies the relative link to the condition.

#### Example: Get all conditions for a single patient 

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Condition?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Condition/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a
</pre>
&nbsp;

#### Example: Get the condition problem with id of 'prb-12'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Condition?_id=prb-12
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Condition?identifier=prb-12
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Condition/_search
<i><small>body:</small></i> _id=prb-12
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Condition/_search
<i><small>body:</small></i> identifier=prb-12
</pre>
&nbsp;

#### Example: Get all conditions for a single patient that were modified as of 5/5/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Condition?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_lastUpdated=ge2022-05-05
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Condition/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_lastUpdated=ge2022-05-05
</pre>
&nbsp;

## Device

### Overview
The [implantable device](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-implantable-device.html) resource identifies an instance or type of manufactured item used in the provision of healthcare.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique identifier for the device | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _16.8_ |
| udiCarrier | Unique Device Identifier (UDI) Barcode string | [BackboneElement](https://www.hl7.org/fhir/R4/backboneelement.html) | _16.8_ |
| distinctIdentifier | The distinct identification string | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.8_ |
| lotNumber | Lot number of manufacturer | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.8_ |
| serialNumber | Serial number assigned by the manufacturer | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.8_ |
| manufactureDate | Date when the device was made | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.8_ |
| expirationDate | Date and time of expiry of this device | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.8_ |
| type | The kind or type of device | [CodeableConcept](https://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.8_ |
| patient | The patient pertaining to the device | [Reference](https://www.hl7.org/fhir/R4/references.html)([US Core Patient Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.8_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "type": "searchset",
  "total": 1,
  "entry": [
    {
      "resource": {
        "resourceType": "Device",
        "id": "123",
        "udiCarrier": [
          {
            "deviceIdentifier": "43069338026389",
            "carrierHRF": "(01)43069338026389(11)000302(17)250317(10)1134(21)842026117977"
          }
        ],
        "distinctIdentifier": "A9971312345600",
        "lotNumber": "000000000000XYZ123",
        "serialNumber": "842026117977"
        "manufactureDate": "2013-02-01T00:00:00Z",
        "expirationDate": "2014-02-01T00:00:00Z",
         "type": {
          "coding": [
            {
              "system": "http://snomed.info/sct",
              "code": "714549006",
              "display": "Synthetic bone graft (physical object)"
            }
          ],
          "text": "Synthetic bone graft (physical object)"
        },
        "patient": {
          "reference": "Patient/ad2085b5-b974-401d-bfcb-3b865109fd35",
          "display": "Smith, John"
        }
      }
    }
  ]
}
</pre>
&nbsp;

### *Get*
Returns a single Device result based on the Device ID.

#### HTTP Request 
`GET /r4/Device/{deviceId}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| deviceId | path | The unique identifier for the device | Yes | _16.8_ |

#### Example: Get the device with an ID of '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Device/123
</pre>
&nbsp;


### *Search*
Searches for devices for a single patient

#### HTTP Request 
- `GET /r4/Device?{parameters}`
- `POST /r4/Device/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _lastUpdated | query or body | The date the device was last modified, formatted as yyyy-MM-dd. We also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] . Note that the + character must be URL encoded. (i.e. `%2B`) | No | _16.8_ |
| patient | query or body | The official patient identifier acquired from a patient search | No | _16.8_ |
| date | query or body | The device last update date in the form YYYY-MM-DD | No | _16.8_ |
| identifier | query or body | The unique identifier for the device | No | _16.8_ |
| _id | query or body | The unique identifier for the device | No | _16.8_ |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional `Provenance` resources that relate to each document reference | No | _17.0_ |
**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

#### Example: Get all devices for a single patient with id 'ad2085b5-b974-401d-bfcb-3b865109fd35'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Device?patient=ad2085b5-b974-401d-bfcb-3b865109fd35
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Device?patient=Patient/ad2085b5-b974-401d-bfcb-3b865109fd35
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Device/_search
<i><small>body:</small></i> patient=ad2085b5-b974-401d-bfcb-3b865109fd35
</pre>
&nbsp;

#### Example: Get all devices for a single patient with id 'ad2085b5-b974-401d-bfcb-3b865109fd35' that were recorded as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Device?patient=ad2085b5-b974-401d-bfcb-3b865109fd35&date=ge2017-01-01
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Device?patient=Patient/ad2085b5-b974-401d-bfcb-3b865109fd35&date=ge2017-01-01
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Device/_search
<i><small>body:</small></i> patient=ad2085b5-b974-401d-bfcb-3b865109fd35&date=ge2017-01-01
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Device?patient=ad2085b5-b974-401d-bfcb-3b865109fd35&_lastUpdated=ge2017-01-01
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Device/_search
<i><small>body:</small></i> patient=ad2085b5-b974-401d-bfcb-3b865109fd35&_lastUpdated=ge2017-01-01
</pre>
&nbsp;

#### Search for a device with the id '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Device?identifier=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Device/_search
<i><small>body:</small></i> identifier=123
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Device?_id=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Device/_search
<i><small>body:</small></i> _id=123
</pre>
&nbsp;

## DocumentReference

### Overview
A reference to a [document](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-documentreference.html) of any kind for any purpose. Provides metadata about the document so that the document can be discovered and managed. The scope of a document is any seralized object with a mime-type, so includes formal patient centric documents (CDA), clinical notes, scanned paper, and non-patient specific documents like policy text.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique id string assigned to each documentreference | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| identifier | The unique identifier assigned to each documentreference | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _16.7_ |
| status | Specifies the status of the document reference | [Code](https://www.hl7.org/fhir/R4/datatypes.html#code) | _16.7_ |
| type | Specifies the particular kind of document referenced (e.g. History and Physical, Discharge Summary, Progress Note). This usually equates to the purpose of making the document referenced. LOINC Code if possible | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.8_ |
| category | The categorization for the document reference | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.7_ |
| subject | The patient pertaining to the documentreference | [Reference](https://www.hl7.org/fhir/R4/references.html) ([US Core Patient Profile](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.7_ |
| date | document creation time (in UTC) | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.7_ |
| author | Identifies who is responsible for the information in the document reference | [Reference](https://www.hl7.org/fhir/R4/references.html) ([US Core Practitioner Profile](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-practitioner.html)) | _16.7_ |
| description | The description of the documentreference | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| content.format | An identifier of the document encoding, structure, and template that the document conforms to | [Coding](http://hl7.org/fhir/R4/datatypes.html#Coding) | _16.7_ |
| content.attachment.contentType | The mimetype of the content.| [Code](https://www.hl7.org/fhir/R4/datatypes.html#code) | _16.7_ |
| content.attachment.data | The base64 encoded data of the attachment. | [base64Binary](http://hl7.org/fhir/R4/datatypes.html#base64Binary) | _16.7_ |
| content.attachment.url | The url to retrieve the data from the binary endpoint | [url](http://hl7.org/fhir/R4/datatypes.html#url) | _17.0_ |
| content.attachment.title | The title of the document| [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| extension: note-category | Contains the category of the document | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| extension: document-publish-portal | Contains whether the document is published to myPatientVisit | [boolean](https://www.hl7.org/fhir/R4/datatypes.html#boolean)  | _16.7_ | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) |
| context.encounter | The clinical context in which the document was prepared. | [Reference](https://www.hl7.org/fhir/R4/references.html) ([US Core Encounter Profile](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-encounter.html)) | _16.8_ |
| context.period | The time period over which the service that is described by the document was provided | [Period](http://hl7.org/fhir/R4/datatypes.html#Period) | _16.7_ |
| custodian | Identifies the organization or group who is responsible for ongoing maintenance of and access to the document. | [Reference](https://www.hl7.org/fhir/R4/references.html) ([US Core Organization Profile](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-organization.html)) | _16.8_ |

### Example
<pre class="center-column">
{
    "resourceType": "DocumentReference",
    "id": "history-2262",
    "identifier": [
        {
            "use": "official",
            "value": "history-2262"
        }
    ],
    "status": "current",
    "type": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "18842-5",
                "display": "Discharge Summary"
            }
        ],
        "text": "Discharge Summary"
    },
    "category": [
        {
            "coding": [
                {
                    "system": "https://select.nextech-api.com/api/structuredefinition/note-category",
                    "code": "Prescriptions",
                    "display": "Prescriptions"
                }
            ],
            "text": "Prescriptions"
        }
    ],
    "subject": {
        "reference": "Patient/c21ab936-3a2a-4c5a-81b8-76b120194053",
        "display": "White, Nicole Francis"
    },
    "date": "2022-06-02T17:11:23.943+00:00",
    "author": [
        {
            "reference": "Organization/22",
            "display": "Clinic One"
        }
    ],
    "custodian": {
        "reference": "Organization/22",
        "display": "Clinic One"
    },
    "content": [
        {
            "attachment": {
                "contentType": "text/plain",
                "url": "Binary/history-125369",
                "title": "small text doc.txt"
            },
            "format": {
                "system": "urn:oid:1.3.6.1.4.1.19376.1.2.3",
                "code": "urn:ihe:iti:xds:2017:mimeTypeSufficient",
                "display": "mimeType Sufficient"
            }
        }
    ],
    "context": {
        "encounter": [
            {
                "reference": "Encounter/6",
                "display": "Encounter Name"
            }
        ],
        "period": {
            "start": "2022-06-02T17:11:23.943+00:00",
            "end": "2022-06-02T17:11:23.943+00:00"
        }
    }
}
</pre>
&nbsp;

### *Get By ID*
Finds a single document based on the ID

#### HTTP Request 
`GET /r4/DocumentReference/{documentType-id}` 

#### Parameters
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| DocumentType-id | Must be in the form `documenttype-id` i.e: GET /r4/DocumentReference/history-5  | Yes | 16.8 |

#### Supported Document Types
The supported document type specifiers for IDs are `history-{id}` and `emn-{id}`.

#### Example: Get the history document with ID 2262 which is a text file with a content of "Hello!"
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference/history-2262
</pre>
&nbsp;

### *Search*
Finds a bundle of documents based on the search parameters

#### HTTP Request 
- `GET /r4/DocumentReference?{parameters}`
- `POST /r4/DocumentReference/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| \_id | query or body | Unique ID of the document  | No | _16.8_ |
| identifier | query or body | Unique ID of the document  | No | _16.8_ |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional `Provenance` resources that relate to each document reference | No | _17.0_ |
| patient | query or body | The ID of the patient associated with the document | No | _16.9_ |
| category | query or body | The category of the document | No | _16.9_ |
| date | query or body| This searches based on the created date of the document, either a specific date or a range depending on search modifiers | No | _16.9_ |
| type | query or body| The type of the document | No | _16.9_ |
**_Note:_**  The possible filter values for the date parameter are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

#### Retrieve Provenance with document references
The `_revinclude` parameter allows support for including Provenance references that match the returned document references.
This value must be `Provenance:target`, otherwise the request will result in an error.
These will be in additional bundle entry components, which have a `Provenance.Target` entry that identifies the relative link to the document reference

#### Example: Get the history document with ID 7741
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference?_id=history-7741
</pre>
&nbsp;

#### Example: Searching for all documents that have a type of 11488-4, category of Unknown, created on 2022-06-03 for the specific patient
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference?type=11488-4&category=Unknown&date=2022-06-03&patient=c21ab936-3a2a-4c5a-81b8-76b120194053
</pre>
&nbsp;

#### Example: Search for all documents that were created between 2020-06-03 and 2022-06-01
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference?date=gt2020-06-03&date=lt2022-06-01
</pre>
&nbsp;

#### Example Search by _id in POST Body
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/DocumentReference/_search
<i><small>body:</small></i> 
_id:history-2262
</pre>

#### Example Searching for all documents that have a type of 11488-4, category of Clinical, created before 2022-06-03 for the specific patient

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/DocumentReference/_search
<i><small>body:</small></i> 
type:11488-4
category:Clinical
date:lt2022-06-03
patient:c21ab936-3a2a-4c5a-81b8-76b120194053
</pre>

### *Create*
Creates the document in the provided `content.attachment` POST body field for a patient, and attaches it to the patient's history tab in the Nextech software.

#### HTTP Request 
`POST /r4/DocumentReference` 

#### Body Fields
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| resourceType | Must be `DocumentReference` | Yes | 16.8 |
| type | Specifies the particular kind of document referenced (e.g. History and Physical, Discharge Summary, Progress Note). This usually equates to the purpose of making the document referenced. LOINC Code if possible | Yes | _16.8_ |
| category | Allows setting category of the document  | No | _16.8_ |
| date | The date (in UTC) of the composition. ie. `2017-10-16T20:32:28.9692476Z` | No | _16.8_ |
| author.display | The name of the author. This will be appended to the beginning of the description value. | No | _16.8_ |
| description | A description of the document | No | _16.8_ |
| content.attachment.contentType | The mimetype of the document. See Allowed Mimetypes below | Yes | _16.8_ |
| content.attachment.data | The base64 data of the document | Yes | _16.8_ |
| content.attachment.title | The title of the document, will be used as the filename| Yes | _16.8_ |
| extension: note-category | Allows setting category of the document | No | _16.8_ |
| extension: document-publish-portal | Allows setting whether or not to publish the document to myPatientVisit. Note: Must be licensed for myPatientVisit and have permission to publish EMNs to MPV to work | No | _16.8_ |

### Extension: note-category
This is a custom extension to allow the setting of the category on the document. This must match with an existing note category or is left blank.  There can be only one `note-category` extension.

Note: This custom extension should not be used, instead `category` is encouraged.
When `category` is supplied, only the first coding will be used. Any others will be ignored.
When both `category` and the this extension are used, the NexTech extension will be used instead of the `category`.

`Extension system url`: https://select.nextech-api.com/api/structuredefinition/note-category
`valueString`: `<name of Nextech note category>`

### Extension: document-publish-portal
This is a custom extension to allow publishing of a document to myPatientVisit. The client must be licensed for myPatientVisit and the caller must have permission to publish EMNs to MPV, otherwise the document will not be published.  There can be only one `document-publish-portal` extension.  If this extension is not included in the POST, the document is not published to myPatientVisit.

`Extension system url`: https://select.nextech-api.com/api/structuredefinition/document-publish-portal
`valueBoolean`: `true` or `false`
#### Example: Attach a new document for a patient
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/DocumentReference
</pre>
&nbsp;

#### Body
**Note**: The `note-category` NexTech extension should not be used, instead the FHIR `category` POST body member is encouraged
When the FHIR `category` POST body member is supplied, only the first coding will be used. Any others will be ignored.
When both the FHIR `category` and the `note-category` NexTech extension POST body members are used, the NexTech extension will be used instead of the FHIR `category` value
&nbsp;
<pre class="center-column">
{
    "resourceType": "DocumentReference",
    "type": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "18842-5",
                "display": "Discharge Summary"
            }
        ],
        "text": "Discharge Summary"
    },
    "category": [
        {
            "coding": [
                {
                    "system": "https://select.nextech-api.com/api/structuredefinition/note-category",
                    "code": "Prescriptions",
                    "display": "Prescriptions"
                }
            ],
            "text": "Prescriptions"
        }
    ],
    "subject": {
        "reference": "Patient/9CFE7258-8F50-45E8-9732-6433976CC164"
    },
    "content": [{"attachment": {
        "contentType": "text/plain",
        "data": "Tm8gYWN0aXZpdHkgcmVzdHJpY3Rpb24sIHJlZ3VsYXIgZGlldCwgZm9sbG93IHVwIGluIHR3byB0byB0aHJlZSB3ZWVrcyB3aXRoIHByaW1hcnkgY2FyZSBwcm92aWRlci4="
    } }],
    "context": {"encounter": {"reference": "Encounter/1"} },
    "extension": [
            {
                "url": "https://select.nextech-api.com/api/structuredefinition/note-category",
                "valueString": "Past Medical History"
            },
            {
                "url": "https://select.nextech-api.com/api/structuredefinition/document-publish-portal",
                "valueBoolean": "true"
            }
    ],
}
</pre>
&nbsp;

### *$docref* operation
This generates a CCDA for the given patient and attaches it to their patient history if no Summary of Care has been previously generated for the relevant encounters.
Otherwise, this returns the most recent CCDA Summary of Care document generated for each encounter.
If only `patient` is specified, then it will return one (1) Summary of Care document reference record for the latest encounter.
If `patient` and a date range are specified (`start`, `end`, `start`+`end`), then it will return one document reference for each encounter that falls within that range.

#### HTTP Request
`POST /r4/DocumentReference/$docref`

#### Body Fields
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| resourceType | Must be `Parameters` | Yes | _16.9_ |
| parameter | This is an array of [parameters](https://www.hl7.org/fhir/parameters.html) which must include one patient parameter | Yes | _16.9_ |
| parameter.patient | The patient the document is for | Yes | _16.9_ |
| parameter.start | The start date for EMN encounters | No | _16.9_ |
| parameter.end | the end date for EMN encounters | No | _16.9_ |

#### Example: Generating a CCDA for patient with an ID of C21AB936-3A2A-4C5A-81B8-76B120194053 via POST
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/DocumentReference/$docref
</pre>
&nbsp;

#### Body
<pre class="center-column">
 {
      "resourceType": "Parameters",
      "parameter": [
        {
          "name": "patient",
          "valueId" : "C21AB936-3A2A-4C5A-81B8-76B120194053"
        },
        {
            "name": "start",
            "valueDateTime": "2022-02-23T08:00:00"
        },
        {
            "name": "end",
            "valueDateTime": "2022-02-24T08:00:00"
        }
      ]
    }
</pre>
Note: The `start` and `end` parameters can be either of type `valueDateTime` as above, or simply `valueDate` and passing only values such as `2022-02-23`

#### HTTP Request 
`GET /r4/DocumentReference/$docref?{patient}[&{start}][&{end}]`

#### Parameters
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| patient | Must be in the form `{patient GUID}` i.e: `patient=C21AB936-3A2A-4C5A-81B8-76B120194053` | Yes | _16.9_ |
| start | Must be in the form of either  `2022-02-23T08:00:00` or `2022-02-23` | No | _16.9_ |
| end | Must be in the form of either `2022-02-24T08:00:00` or `2022-02-24` | No | _16.9_ |

#### *Note: Despite being a GET request, if an encounter that falls within the date range (if supplied) or the most recent encounter does not have a CCDA Summary of Care document previously generated, this request will cause one to be created and attached to the patient's document history*

#### Example: Generating a CCDA for patient with an ID of C21AB936-3A2A-4C5A-81B8-76B120194053 via GET
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference/$docref?patient=C21AB936-3A2A-4C5A-81B8-76B120194053
</pre>
#### Response
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 1,
    "entry": [
        {
            "resource": {
                "resourceType": "DocumentReference",
                "identifier": [
                    {
                        "use": "official",
                        "value": "history-2263"
                    }
                ],
                "status": "current",
                "type": {
                    "coding": [
                        {
                            "system": "http://loinc.org",
                            "code": "34133-9",
                            "display": "Summarization of Episode Note"
                        }
                    ],
                    "text": "Summarization of Episode Note"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "https://select.nextech-api.com/api/structuredefinition/note-category",
                                "code": "clinical",
                                "display": "Clinical Note"
                            }
                        ],
                        "text": "Clinical Note"
                    }
                ],
                "subject": {
                    "reference": "Patient/c21ab936-3a2a-4c5a-81b8-76b120194053",
                    "display": "White, Nicole Francis"
                },
                "date": "2022-06-02T13:26:26.2198865-04:00",
                "author": [
                    {
                        "reference": "Organization/1",
                        "display": "Pawtucket Plastic Surgeons"
                    }
                ],
                "custodian": {
                    "reference": "Organization/1",
                    "display": "Pawtucket Plastic Surgeons"
                },
                "content": [
                    {
                        "attachment": {
                            "contentType": "application/xml",
                            "url": "Binary/history-125369"
                        },
                        "format": {
                            "system": "urn:oid:1.3.6.1.4.1.19376.1.2.3",
                            "code": "urn:hl7-org:sdwg:ccda-structuredBody:2.1",
                            "display": "Documents following C-CDA constraints using a structured body"
                        }
                    }
                ],
                "context": {
                    "encounter": [
                        {
                            "reference": "Encounter/8109",
                            "display": "MUS2"
                        }
                    ],
                    "period": {
                        "start": "2022-06-02T13:26:26.2198865-04:00",
                        "end": "2022-06-02T13:26:26.2198865-04:00"
                    }
                }
            }
        }
    ]
}
</pre>


&nbsp;

### Allowed Mimetypes
The following mimetypes are currently supported:

| Document Type   | MimeType                                                |
|-----------------|---------------------------------------------------------|
| pdf             | application/pdf                                         |
| Microsoft Word  | application/msword                                      |
| Microsoft Excel | application/vnd.ms-excel or application/vnd.ms-excel.12 |
| Tif Image files | application/tif, application/tiff, or image/tiff        |
| HTML            | text/html                                               |
| Text            | text/plain                                              |
| XML             | text/xml                                                |
| BMP Image       | image/bmp                                               |
| GIF Image       | image/gif                                               |
| JPG Image       | image/jpeg                                              |
| PNG Image       | image/png or image/x-png                                |


## Encounter

### Overview
The [Encounter](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-encounter.html) resource describes an interaction between a patient and healthcare provider.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique value assigned to each encounter which discerns them from all others | [string](https://www.hl7.org/fhir/r4/datatypes.html#string) | _16.9_ |
| identifier | The unique value assigned to each encounter which discerns them from all others | [Identifier](https://www.hl7.org/fhir/r4/datatypes.html#Identifier) | _16.9_ |
| status | The current state of the encounter (either `in-progress`, `finished`, or `unknown`) | [code](https://hl7.org/fhir/R4/datatypes.html#code) with [encounter status value set](http://hl7.org/fhir/R4/valueset-encounter-status.html) | _16.9_ |
| class | The classification of the encounter | [Coding](http://hl7.org/fhir/R4/datatypes.html#Coding) | _16.9_ |
| type | The specific type of the encounter | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| subject | The patient pertaining to the encounter | [Reference](https://www.hl7.org/fhir/r4/references.html)([US Core Patient Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.9_ |
| participant | The medical professionals involved in the encounter | [BackboneElement](https://www.hl7.org/fhir/r4/backboneelement.html) | _16.9_ |
| period | The start and end date of the encounter in the form YYYY-MM-DD | [period](https://www.hl7.org/fhir/R4/datatypes.html#Period) | _16.9_ |
| reasonCode | The coded reason the encounter took place | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| hospitalization.dischargeDisposition | Category or kind of location after discharge | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| location.location | Location the encounter took place at | [Reference](https://www.hl7.org/fhir/r4/references.html)([US Core Location Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-location.html)) | _16.9_ |
| meta.lastUpdated | The last time the encounter was updated | [instant](https://www.hl7.org/fhir/R4/datatypes.html#instant) | _16.9_ |

### Example
<pre class="center-column">
{
    "resourceType": "Encounter",
    "id": "19632",
    "meta": {
        "lastUpdated": "2022-07-20T09:41:50.82-04:00"
    },
    "identifier": [
        {
            "use": "official",
            "system": "https://select.nextech-api.com/api/structuredefinition/encounter-id",
            "value": "19632"
        }
    ],
    "status": "in-progress",
    "class": {
        "system": "http://terminology.hl7.org/CodeSystem/v3-ActCode",
        "code": "AMB",
        "display": "ambulatory"
    },
    "type": [
        {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/data-absent-reason",
                    "code": "unknown",
                    "display": "Unknown"
                }
            ],
            "text": "Unknown"
        }
    ],
    "subject": {
        "reference": "Patient/2ab530e0-9606-4f7a-8b67-e2de253ba80b",
        "display": "Smith, John"
    },
    "participant": [
        {
            "type": [
                {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/v3-ParticipationType",
                            "code": "PRF",
                            "display": "performer"
                        }
                    ],
                    "text": "performer"
                }
            ],
            "period": {
                "start": "2022-04-22",
                "end": "2022-04-22"
            },
            "individual": {
                "reference": "Practitioner/123",
                "display": "1, Doctor"
            }
        },
        {
            "type": [
                {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/v3-ParticipationType",
                            "code": "PRF",
                            "display": "performer"
                        }
                    ],
                    "text": "performer"
                }
            ],
            "period": {
                "start": "2022-04-22",
                "end": "2022-04-22"
            },
            "individual": {
                "reference": "Practitioner/124",
                "display": "2, Doctor"
            }
        },
        {
            "type": [
                {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/v3-ParticipationType",
                            "code": "PRF",
                            "display": "performer"
                        }
                    ],
                    "text": "performer"
                }
            ],
            "period": {
                "start": "2022-04-22",
                "end": "2022-04-22"
            },
            "individual": {
                "reference": "Practitioner/125",
                "display": "3, Doctor"
            }
        },
        {
            "type": [
                {
                    "coding": [
                        {
                            "system": "http://terminology.hl7.org/CodeSystem/v3-ParticipationType",
                            "code": "PRF",
                            "display": "performer"
                        }
                    ],
                    "text": "performer"
                }
            ],
            "period": {
                "start": "2022-04-22",
                "end": "2022-04-22"
            },
            "individual": {
                "reference": "Practitioner/126",
                "display": "4, Doctor"
            }
        }
    ],
    "period": {
        "start": "2022-04-22",
        "end": "2022-04-22"
    },
    "reasonCode": [
        {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/data-absent-reason",
                    "code": "unknown",
                    "display": "Unknown"
                }
            ],
            "text": "Unknown"
        }
    ],
    "hospitalization": {
        "dischargeDisposition": {
            "coding": [
                {
                    "system": "http://terminology.hl7.org/CodeSystem/data-absent-reason",
                    "code": "unknown",
                    "display": "Unknown"
                }
            ],
            "text": "Unknown"
        }
    },
    "location": [
        {
            "location": {
                "reference": "Location/1",
                "display": "Pawtucket Plastic Surgeons"
            }
        }
    ]
}
</pre>
&nbsp;

### *Get*
Returns a single Encounter result based on the Encounter ID.

#### HTTP Request 
`GET /r4/Encounter/{encounterID}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| encounterID | path | The encounter unique identifier | Yes | _16.9_ |

#### Example: Get an encounter with an ID of '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Encounter/123
</pre>
&nbsp;

### *Search*
Returns encounters based on the provided search parameters.

#### HTTP Requests
- `GET /r4/Encounter?{parameters}`
- `POST /r4/Encounter/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _lastUpdated | query or body | The date the encounter was last modified, formatted as yyyy-MM-dd. We also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] . Note that the + character must be URL encoded. (i.e. `%2B`) | No | _16.9_ |
| patient | query or body | The official patient identifier acquired from a patient search | No | _16.9_ |
| date | query or body | The date the encounter took place in the form YYYY-MM-DD  | No | _16.9_ |
| identifier | query or body | The encounter unique identifier | No | _16.9_ |
| _id | query or body | The encounter unique identifier | No | _16.9_ |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that relate to each encounter | No | _17.0_ |

**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

&nbsp;
#### Retrieve Provenance with encounters
The `_revinclude` parameter allows support for including [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that match the returned encounters.
This value must be `Provenance:target`, otherwise the request will result in an error.
These will be in additional bundle entry components, which have a `Provenance.Target` entry that identifies the relative link to the encounter.
&nbsp;
#### Examples: 

#### Get all encounters

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Encounter
</pre>

#### Search for encounters for the patient with the id '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Encounter?patient=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Encounter/_search
<i><small>body:</small></i> patient=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

#### Search for encounters for the patient with the id '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192' that took place between and including 1/1/2022 through 11/14/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Encounter?patient=patient/9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&date=ge2022-01-01&date=lt2022-11-14
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Encounter/_search
<i><small>body:</small></i> patient=patient/9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&date=ge2022-01-01&date=lt2022-11-14
</pre>

#### Search for an Encounter with the id '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Encounter?identifier=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Encounter/_search
<i><small>body:</small></i> identifier=123
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Encounter?_id=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Encounter/_search
<i><small>body:</small></i> _id=123
</pre>


## Goal

### Overview
The [goal](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-goal.html) resource describes a desired state of health for a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each goal which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _17.0_ |
| id | The unique value assigned to each goal which discerns them from all others. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _17.0_ |
| subject | The patient pertaining to the goal | [Reference](https://www.hl7.org/fhir/R4/references.html)([US Core Patient Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _17.0_ |
| target | The target outcome of the goal | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _17.0_ |
| note | Comments about the goal | [Annotation](https://www.hl7.org/fhir/R4/datatypes.html#Annotation) | _17.0_ |
| date | The date or date range of the goal or goals | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _17.0_ |
| meta.lastUpdated | The last time the goal was modified | [instant](https://hl7.org/fhir/R4/datatypes.html#instant) | _17.0_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Goal",
        "id": "goalemn-2284code-559215",
         "meta": {
           "lastUpdated": "2022-08-05T14:29:08.217-04:00"
         },
        "identifier": [
          {
            "use": "official",
            "value": "goalemn-2284code-559215"
          }
        ],
        "subject": {
          "reference": "Patient/F15FB185-5E63-485E-B025-D113103DCEC3",
          "display": "Smith, Jane"
        },
        "target": {
          "measure": {
            "coding": [
              {
                "system": "http://loinc.org",
                "code": "LA7435-6"
              }
            ],
            "text": "Fever"
          }
        },
        "note": [
          {
            "text": "Goal (Free Text): Take time off work, get bed rest"
          }
        ]
      }
    }
  ]
}
</pre>
&nbsp;

### *Get*
Returns a single Goal based on the goal's ID.

#### HTTP Request 
`GET r4/Goal/{GoalID}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| GoalID | path | The official goal identifier acquired from a goal search | Yes | _17.0_ |

#### Example: Get a goal by GoalID

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Goal/{GoalID}
</pre>
&nbsp;

### *Search*
Searches for goals for a single patient

#### HTTP Requests
- `GET /r4/Goal?{parameters}`
- `POST /r4/Goal/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or body | The goal identifier | No | _17.0_ |
| _id | query or body | The goal identifier | No | _17.0_ |
| patient | query or body | The official patient identifier acquired from a patient search | No | _17.0_ |
| date | query or body | The date of the encounter containing the goal in the form YYYY-MM-DD | No | _17.0_ |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that relate to each encounter | No | _17.0_ |
| _lastUpdated | query or body | The date a goal was last modified | No | _17.0_ |
#### Example: Get all goals for a single patient

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Goal?patient=29D5AA40-6E3E-4683-B17F-2FBFECACF9BC
</pre>
&nbsp;

#### Example: Get all goals for a single patient, using a `Patient/` reference prefix

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Goal?patient=Patient/29D5AA40-6E3E-4683-B17F-2FBFECACF9BC
</pre>
&nbsp;

#### Example: Get all goals for a patient on a date

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Goal?patient=29D5AA40-6E3E-4683-B17F-2FBFECACF9BC&date=2017-01-01
</pre>
&nbsp;


#### Example: Get all goals for a patient on a date

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Goal/_search?patient=29D5AA40-6E3E-4683-B17F-2FBFECACF9BC&date=2017-01-01
</pre>
&nbsp;

## Immunization

### Overview
The [Immunization](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-immunization.html) resource describes an administered vaccine.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The logical id of the resource, as used in the URL for the resource. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| identifier | The unique value assigned to each immunization which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _16.7_ |
| status | Either `completed` or `not-done` | [code](https://hl7.org/fhir/R4/datatypes.html#code) with [immunization status value set](https://hl7.org/fhir/R4/valueset-immunization-status.html) | _16.7_ |
| statusReason | Reason that an immunization event was not performed, if any | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) using [Substance Refusal Reason (NIP) value set](https://phinvads.cdc.gov/vads/ViewCodeSystem.action?id=2.16.840.1.114222.4.5.294) | _16.7_ |
| vaccineCode | Vaccine product administered | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) using [vaccine administered value set](https://www.hl7.org/fhir/R4/valueset-vaccine-code.html) | _16.7_ |
| patient | The immunized patient | [Reference](https://www.hl7.org/fhir/R4/references.html) ([US Core Patient Profile](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.7_ |
| occurrenceDateTime | The vaccination administration date in the form YYYY-MM-DD | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.7_ |
| primarySource | Whether or not the information is from the person who administered the vaccine | [boolean](https://www.hl7.org/fhir/R4/datatypes.html#boolean) | _16.7_ |
| meta.lastUpdated | The last time the immunization was updated | [instant](https://www.hl7.org/fhir/R4/datatypes.html#instant) |  _16.7_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Immunization",
        "id": "123",
        "meta": 
        {
           "lastUpdated": "2022-04-02T14:04:35.9+00:00"
         },
        "identifier": [
          {
            "use": "official",
            "value": "123"
          }
        ],
        "status": "completed",
        "vaccineCode": {
          "coding": [
            {
              "system": "http://hl7.org/fhir/sid/cvx",
              "code": "05",
              "display": "measles virus vaccine"
            }
          ],
          "text": "measles virus vaccine"
        },
        "patient": {
          "reference": "Patient/4AAE9E3C-B1E4-46EA-93C2-CF3B36747D1A",
          "display": "Tinsley, Carol F"
        },
        "occurrenceDateTime": "2013-08-17",
        "primarySource" : true
      }
    }
  ]
}
</pre>
&nbsp;

### *Get*
Returns a single Immunization result based on the Immunization ID.

#### HTTP Request 
`GET /r4/Immunization/{immunizationID}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| immunizationID | path | The immunization unique identifier | Yes | _16.7_ |

#### Example: Get an immunization with an ID of '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization/123
</pre>
&nbsp;

### *Search*
Returns immunizations based on the provided search parameters.

#### HTTP Requests
- `GET /r4/Immunization?{parameters}`
- `POST /r4/Immunization/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _lastUpdated | query or body | The date the patient was last modified, formatted as yyyy-MM-dd. We also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] . Note that the + character must be URL encoded. (i.e. `%2B`) | No | _16.7_ |
| patient | query or body | The official patient identifier acquired from a patient search | No | _16.7_ |
| date | query or body | The date the immunization was administered in the form YYYY-MM-DD  | No | _16.7_ |
| identifier | query or body | The immunization unique identifier | No | _16.7_ |
| _id | query or body | The immunization unique identifier | No | _16.7_ |

**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

&nbsp;
#### Examples: 

#### Get all immunizations

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization
</pre>

#### Search for immunizations for the patient with the id '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization?patient=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Immunization/_search
<i><small>body:</small></i> patient=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

#### Search for immunizations for the patient with the id '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192' administered between and including 1/1/2022 through 11/14/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization?patient=patient/9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&date=ge2022-01-01&date=lt2022-11-14
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Immunization/_search
<i><small>body:</small></i> patient=patient/9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&date=ge2022-01-01&date=lt2022-11-14
</pre>

#### Search for an immunization with the id '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization?identifier=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Immunization/_search
<i><small>body:</small></i> identifier=123
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization?_id=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Immunization/_search
<i><small>body:</small></i> _id=123
</pre>

&nbsp;

## Diagnostic Report

### Overview
A diagnostic report resource describes the findings and interpretation of diagnostic tests performed on patients and/or specimens derived from these. There are two types of diagnostic reports that can be returned:

* [Diagnostic reports for laboratory specimens](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-diagnosticreport-lab.html)
* [Diagnostic reports containing result documents for laboratory specimens](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-diagnosticreport-note.html)

These types of laboratory reports are denoted by their category. Diagnostic reports for laboratory specimens will always have a category of "LAB", while reports containing result documents will have a the document's assigned LOINC code as their category. For example, "LP29684-5" would be the category for a radiology document report.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The logical id of the resource, as used in the URL for the resource. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.9_ |
| identifier | The unique value assigned to each diagnostic report which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _16.9_ |
| status | The status of the diagnostic report | [code](https://hl7.org/fhir/R4/datatypes.html#code) with [DiagnosticReportStatus](http://hl7.org/fhir/R4/valueset-diagnostic-report-status.html) | _16.9_ |
| category | Classification of type of diagnostic report | [Category](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) using [Diagnostic Service Section Codes](http://hl7.org/fhir/R4/valueset-diagnostic-service-sections.html) | _16.9_ |
| code | A code that describes the diagnostic report | [LOINC Diagnostic Report Codes](http://hl7.org/fhir/R4/valueset-report-codes.html) | _16.9_ |
| subject | The patient pertaining to the diagnostic report | [Reference](https://www.hl7.org/fhir/R4/references.html) ([US Core Patient Profile](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.9_ |
| effectiveTime | The date and time of specimen collection | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.9_ |
| issued | The date and time that this version of the report was made available to providers | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.9_ |
| performer | The provider who is responsible for issuing the report | [Reference](http://hl7.org/fhir/R4/references.html#Reference) ([US Core Practitioner Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-practitioner.html)) | _16.9_ |
| encounter | The healthcare event which this diagnostic report is about | [Reference](http://hl7.org/fhir/R4/references.html#Reference)([US Core Encounter Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-encounter.html)) | _16.9_ |
| result | A reference to the related lab result observations | [Reference](http://hl7.org/fhir/R4/references.html#Reference) ([US Core Observation Lab Profile](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-observation-lab.html)) | _16.9_ |
| presentedForm | A document attachment containing lab result data for the report | [Attachment](http://hl7.org/fhir/R4/datatypes.html#Attachment) | _16.9_ |
| presentedForm.url | The url to retrieve the data from the binary endpoint | [url](http://hl7.org/fhir/R4/datatypes.html#url) | _17.0_ |

### Example
<pre class="center-column">
{
   "resourceType":"Bundle",
   "entry":[
      {
         "resource":{
            "resourceType":"DiagnosticReport",
            "id":"244",
            "identifier":[
               {
                  "use":"official",
                  "value":"244"
               },
               {
                  "use":"usual",
                  "value":"XY202200011 - A"
               }
            ],
            "status":"registered",
            "category":[
               {
                  "coding":[
                     {
                        "system":"http://terminology.hl7.org/CodeSystem/v2-0074",
                        "code":"LAB"
                     }
                  ]
               }
            ],
            "code":{
               "coding":[
                  {
                     "system":"http://loinc.org",
                     "code":"11268-0",
                     "display":"S pyog Throat Ql Cult"
                  }
               ],
               "text":"S pyog Throat Ql Cult"
            },
            "subject":{
               "reference":"Patient/C56936DF-FED7-4EFA-8998-2A9848C99631"
            },
            "effectiveDateTime":"2022-06-24T00:00:00-04:00",
            "issued":"2022-06-24T00:00:00-04:00",
            "performer":[
               {
                  "reference":"Practitioner/9149",
                  "display":"Smith, Susan"
               }
            ],
            "result":[
               {
                  "reference":"Observation/442",
                  "display":""
               }
            ]
         }
      }
   ]
}
</pre> 
&nbsp;

### *Get*
Returns a single DiagnosticReport result based on the DiagnosticReport ID.

#### HTTP Request 
`GET /r4/DiagnosticReport/{DiagnosticReportID}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| DiagnosticReport | path | The diagnostic report unique identifier | Yes | _16.9_ |

#### Example: Get a diagnostic report with an ID of '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DiagnosticReport/123
</pre>
&nbsp;

### *Search*
Returns diagnostic reports based on the provided search parameters

#### HTTP Request 
- `GET /r4/DiagnosticReport?{parameters}` 
- `POST /r4/DiagnosticReport/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both.

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or body or path | The diagnostic report identifier | No | _16.9_ |
| _id | query or body or path | The diagnostic report identifier | No | _16.9_ |
| patient | query or body | The official patient identifier acquired from a patient search | No | _16.9_ |
| category | query or body | The category of the diagnostic report by either "LAB" or code ie. category=LP29684-5 or by token ie. category=http://terminology.hl7.org/CodeSystem/v2-0074&vert;LP29684-5 | No | _16.9_ |
| date | query or body | The diagnostic report date in the form YYYY-MM-DD | No | _16.9_ |
| code | query or body | The loinc code of the diagnostic report by code ie. code=49765-1 or token ie. code=http://loinc.org&vert;49765-1 | No | _16.9_ |
| _lastUpdated | query or body | The date the report was last modified, formatted as yyyy-MM-dd. We also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] . Note that the + character must be URL encoded. (i.e. `%2B`) (**_Note:_** Currently this search parameter will not filter the results) | No | _16.9_ |
**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`.

#### Example: Get all lab-type diagnostic reports on or after 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DiagnosticReport?category=LAB&date=ge2017-05-01
</pre>
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/DiagnosticReport/_search
<i><small>body:</small></i> category=LAB&date=ge2017-05-01
</pre>
&nbsp;

## Medication Request

### Overview
The [Medication Request](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-medicationrequest.html) resource can be used to record a patient's medication prescription or order.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The logical id of the resource, as used in the URL for the resource | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _17.0_ |
| status | A code specifying the current state of the medication request | [MedicationRequestStatus](http://hl7.org/fhir/R4/ValueSet/medicationrequest-status) | _17.0_ |
| intent | Whether the request is a proposal, plan, or an original order | [MedicationRequestIntent](http://hl7.org/fhir/R4/ValueSet/medicationrequest-intent) | _17.0_ |
| reported | Indicates if this record was captured as a secondary 'reported' record rather than as an original primary source-of-truth record | [boolean](http://hl7.org/fhir/R4/datatypes.html#boolean) | _17.0_ |
| medication | The supplied medication | [CodeableConcept](http://hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _17.0_ |
| authoredOn | The date and time when the prescription was initially written or authored on | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _17.0_ |
| subject | The patient pertaining to the medication request | [Reference](http://hl7.org/fhir/R4/references.html#Reference) ([US Core Patient Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _17.0_ |
| requester | The individual, organization, or device that initiated the request and has responsibility for its activation | [Reference](http://hl7.org/fhir/R4/references.html#Reference) ([US Core Practitioner Profile](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-practitioner.html)) | _17.0_ |
| encounter | The Encounter during which the medication request was created or to which the creation of this record is tightly associated | [Reference](http://hl7.org/fhir/R4/references.html#Reference) ([US Core Encounter Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-encounter.html)) | _17.0_ |
| dosageInstruction | Indicates how the medication is to be used by the patient | [Dosage](http://hl7.org/fhir/R4/dosage.html#Dosage) | _17.0_ |

### Example
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 1,
    "entry": [
        {
            "resource": {
                "resourceType": "MedicationRequest",
                "id": "1",
                "status": "active",
                "intent": "original-order",
                "reportedBoolean": false,
                "medicationCodeableConcept": {
                    "coding": [
                        {
                            "system": "http://www.nlm.nih.gov/research/umls/rxnorm",
                            "code": "310964",
                            "display": "ibuprofen"
                        }
                    ],
                    "text": "ibuprofen"
                },
                "subject": {
                    "reference": "Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
                    "display": "Newman, Alice Jones"
                },
                "encounter": {
                    "reference": "Encounter/1"
                },
                "authoredOn": "2022-07-06T18:20:39+02:00",
                "requester": {
                    "reference": "Practitioner/84",
                    "display": "Davis, Albert"
                },
                "dosageInstruction": [
                    {
                        "text": "1 capsule by mouth twice a day"
                    }
                ]
            }
        }
    ]
}
</pre>
&nbsp;

### *Get*
Returns a single Medication Request result based on the Medication Request ID.

#### HTTP Request 
`GET /r4/MedicationRequest/{medicationRequestId}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| medicationRequestId | path | The unique identifier for the medication request | Yes | _17.0_ |

#### Example: Get the medication request with an ID of '12'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest/12
</pre>
&nbsp;

### *Search*
Searches for medication requests for a single patient

#### HTTP Requests

- `GET /r4/MedicationRequest?{parameters}`
- `POST /r4/MedicationRequest/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patient | query or body | The official patient identifier acquired from a patient search | No | _17.0_ |
| _id | query or body | The unique identifier for the medication request | No | _17.0_ |
| identifier | query or body | The unique identifier for the medication request | No | _17.0_ |
| intent | query or body | The intent of the medication request. Ex.: 'original-order' | No | _17.0_ |
| status | query or body | The status of the medication request. Ex.: 'active' | No | _17.0_ |
| _lastUpdated | query or body | The date the medication request was last modified, formatted as OOXXXXX where OO is an operator and XXXXX is a date in the form YYYY-MM-DD. | No | _17.0_ |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that relate to each medication request | No | _17.0_ |

**_Note:_**  The possible filter values for the _lastUpdated parameter are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

#### Retrieve Provenance with medication requests
The `_revinclude` parameter allows support for including [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that match the returned medication requests.
This value must be `Provenance:target`, otherwise the request will result in an error.
These will be in additional bundle entry components, which have a `Provenance.Target` entry that identifies the relative link to the medication request.
&nbsp;

#### Example: Get the medication request with an ID of '12'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?identifier=12
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/MedicationRequest/_search
<i><small>body:</small></i> identifier=12
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?_id=12
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/MedicationRequest/_search
<i><small>body:</small></i> _id=12
</pre>
&nbsp;

#### Example: Get all medication requests for a single patient with id 'c27e5be0-4b44-4ec5-a284-4308d6ac2b1a'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?patient=Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/MedicationRequest/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a
</pre>
&nbsp;

#### Example: Get all medication requests for a single patient with id 'c27e5be0-4b44-4ec5-a284-4308d6ac2b1a' and intent 'original-order'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&intent=original-order
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?patient=Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&intent=http://hl7.org/fhir/CodeSystem/medicationrequest-intent|original-order
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/MedicationRequest/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&intent=original-order
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/MedicationRequest/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&intent=http://hl7.org/fhir/CodeSystem/medicationrequest-intent|original-order
</pre>
&nbsp;

#### Example: Get all medication requests for a single patient with id 'c27e5be0-4b44-4ec5-a284-4308d6ac2b1a', intent 'original-order' and status 'active'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&intent=original-order&status=active
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?patient=Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&intent=original-order&status=http://hl7.org/fhir/CodeSystem/medicationrequest-status|active
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/MedicationRequest/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&intent=original-order&status=active
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/MedicationRequest/_search
<i><small>body:</small></i> patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&intent=original-order&status=http://hl7.org/fhir/CodeSystem/medicationrequest-status|active
</pre>
&nbsp;

#### Example: Get all medication requests for a single patient that were modified as of 5/5/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?patient=c27e5be0-4b44-4ec5-a284-4308d6ac2b1a&_lastUpdated=ge2022-05-05
</pre>
&nbsp;

#### Example: Get all medication requests that were modified by 5/5/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/MedicationRequest?_lastUpdated=le2022-05-05
</pre>
&nbsp;

## Observation

### Overview
An observation resource describes a measurement or an assertion made about a patient. The following category codes are supported:

* laboratory
* social-history
* vital-signs

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each observation which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _16.9_ |
| subject | The patient pertaining to the observation | [Reference](https://www.hl7.org/fhir/R4/references.html)([US Core Patient Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.9_ |
| status | The observation status | [Observation Status](https://www.hl7.org/fhir/R4/valueset-observation-status.html) | _16.9_ |
| category | Classification of type of observation | [Category](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| code | Type of observation | [LOINC Code](https://www.hl7.org/fhir/R4/valueset-observation-codes.html) | _16.9_ |
| effectiveDate | Clinically relevant time/time-period for observation | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.9_ |
| value | Observation result | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| issued | The date and time this version of the observation was made available to providers | [instant](http://hl7.org/fhir/R4/datatypes.html#instant) | _16.9_ |
| value | Observation result | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| bodySite | Indicates the site on the subject's body where the observation was made (i.e. the target site) | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| method | Indicates the mechanism used to perform the observation | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _16.9_ |
| hasMember | Used when reporting vital signs panel components | [Reference](http://hl7.org/fhir/R4/references.html#Reference)([US Core Observation Lab Profile](http://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-observation-lab.html)) |  _16.9_ |
| component | Used when reporting systolic and diastolic blood pressure | [BackboneElement](http://hl7.org/fhir/R4/backboneelement.html#BackboneElement) |  _16.9_ |
| meta.lastUpdated | The last time the observation was updated | [instant](https://www.hl7.org/fhir/R4/datatypes.html#instant) |  _16.9_ |

### Example
<pre class="center-column">
{
  "resource":{
    "resourceType":"Observation",
    "id":"lab-452",
    "identifier":[
      {
        "use":"official",
        "value":"lab-452"
      },
      {
        "use":"usual",
        "value":"XY202200016 - A"
      }
    ],
    "status":"registered",
    "category":[
      {
        "coding":[
          {
            "system":"http://terminology.hl7.org/CodeSystem/observation-category",
            "code":"laboratory",
            "display":"laboratory"
          }
        ],
        "text":"Laboratory"
      }
    ],
    "code":{
      "coding":[
        {
          "system":"http://loinc.org",
          "code":"11065-0"
        }
      ],
      "text":"HPV Cervix"
    },
    "subject":{
      "reference":"Patient/4CC272B3-0842-4D9E-A4AD-9535FA1AD01E",
      "display":"Underwood, Jane"
    },
    "effectiveDate":"2022-06-30",
    "issued":"2022-06-01T11:39:12+47:11",
    "bodySite":{
      "text":"right anterior 1st finger"
    },
    "method":{
      "text":"Excision"
    }
  }
}
</pre> 
&nbsp;

### *Get*
Returns a single Observation result based on the Observation ID.

#### HTTP Request 
`GET /r4/Observation/{observationId}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| observationId | path | The unique identifier for the observation | Yes | _16.9_ |

#### Example: Get a lab observation with an ID of '12'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Observation/lab-12
</pre>
&nbsp;

### *Search*
Returns observations based on the provided search parameters

#### HTTP Request 
- `GET /r4/Observation?{parameters}` 
- `POST /r4/Observation/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both.

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or body | The observation identifier | No | _16.9_ |
| _id | query or body | The observation identifier | No | _16.9_ |
| patient | query or body | The official patient identifier acquired from a patient search | No | _16.9_ |
| category | query or body | The category of observation by code ie. category=laboratory or by token ie. category=http://terminology.hl7.org/CodeSystem/observation-category&vert;laboratory | No | _16.9_ |
| date | query or body | The observation date in the form YYYY-MM-DD | No | _16.9_ |
| code | query or body | The loinc code of observation by code ie. code=49765-1 or token ie. code=http://loinc.org&vert;49765-1 | No | _16.9_ |
| \_revinclude | query or body | Must be `Provenance:target`. This enables requesting additional [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that relate to each observation | No | _17.0_ |
| _lastUpdated | query or body | The date the observation was last modified, formatted as yyyy-MM-dd. We also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] . Note that the + character must be URL encoded. (i.e. `%2B`) (**_Note:_** Currently this search parameter will not filter the results for laboratory type observations) | No | _16.9_ |
**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`.

#### Retrieve Provenance with observations
The `_revinclude` parameter allows support for including [Provenance resources](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-provenance.html) that match the returned observations.
This value must be `Provenance:target`, otherwise the request will result in an error.
These will be in additional bundle entry components, which have a `Provenance.Target` entry that identifies the relative link to the observation.
&nbsp;

#### Example: Get all laboratory requisitions and lab results 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Observation?category=laboratory&date=ge2017-05-01
</pre>
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Observation/_search
<i><small>body:</small></i> category=laboratory&date=ge2017-05-01
</pre>
&nbsp;

#### Example: Get the social histories charted in encounters as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Observation?category=social-history&date=ge2017-05-01
</pre>
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Observation/_search
<i><small>body:</small></i> category=social-history&date=ge2017-05-01
</pre>
&nbsp;

#### Example: Get the vital signs charted in encounters as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Observation?category=vital-signs&date=ge2017-05-01
</pre>
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Observation/_search
<i><small>body:</small></i> category=vital-signs&date=ge2017-05-01
</pre>
&nbsp;

## Procedure

### Overview
A [procedure](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-procedure.html) resource describes an activity performed with or on a patient as part of the provision of care.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The logical id of the resource, as used in the URL for the resource. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| identifier | The unique value assigned to each procedure which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _16.7_ |
| status | The status of the procedure | [EventStatus](http://hl7.org/fhir/R4/valueset-event-status.html) | _16.7_ |
| subject | Who the procedure was performed on | [Reference](https://www.hl7.org/fhir/R4/references.html) ([US Core Patient Profile](https://www.hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _16.7_ |
| performedDateTime | Date the procedure was performed | [DateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.7_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Procedure",
        "id": "2053",
        "identifier": [
          {
            "use": "official",
            "value": "2053"
          }
        ],
	"status": "completed",
        "code": {
          "coding": [
            {
              "system": "CPT4",
              "code": "54601",
	      "display": "Microdermabrasion"
            }
          ],
          "text": "Microdermabrasion"
        },
        "subject": {
          "reference": "Patient/5F37E582-FD96-48C5-9EE3-02E26D96CB72",
          "display": "Smith, John"
        },
	"performedDateTime": "2011-10-05"
      }
    }
  ]
}
</pre>
&nbsp;

### *Get*
Returns a single Procedure result based on the Procedure ID.

#### HTTP Request 
`GET /r4/Procedure/{procedureID}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| procedureID | path | The procedure unique identifier | Yes | _16.7_ |

#### Example: Get an procedure with an ID of '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Procedure/123
</pre>
&nbsp;

### *Search*
Returns procedures based on the provided search parameters.

#### HTTP Requests
- `GET /r4/Procedure?{parameters}`
- `POST /r4/Procedure/_search?{parameters}`
  - *application/x-www-form-urlencoded body:* `{parameters}`

**_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _lastUpdated | query or body | The date the procedure was last modified, formatted as yyyy-MM-dd. We also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] . Note that the + character must be URL encoded. (i.e. `%2B`) | No | _16.7_ |
| patient | query or body | The official patient identifier acquired from a patient search | No | _16.7_ |
| date | query or body | The date the procedure was performed in the form YYYY-MM-DD  | No | _16.7_ |
| _id | query or body | The procedure unique identifier | No | _16.7_ |
| identifier | query or body | The procedure unique identifier | No | _16.7_ |

**_Note:_**  The possible filter values for date or _lastUpdated parameters are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

&nbsp;
#### Examples: 

#### Get all procedures

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Procedure
</pre>

#### Search for procedures for the patient with the id '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Procedure?patient=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Procedure/_search
<i><small>body:</small></i> patient=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

#### Search for procedures for the patient with the id '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192' performed between and including 1/1/2022 through 11/14/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Procedure?patient=patient/9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&date=ge2022-01-01&date=lt2022-11-14
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Procedure/_search
<i><small>body:</small></i> patient=patient/9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&date=ge2022-01-01&date=lt2022-11-14
</pre>

#### Search for an procedure with the id '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Procedure?_id=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Procedure/_search
<i><small>body:</small></i> _id=123
</pre>

&nbsp;


## Binary

### Overview
Returns the [Binary](https://hl7.org/fhir/R4/binary.html) data and content type of a Document Reference or a Diagnostic Report.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| contentType | The mimetype of the content.| [Code](https://hl7.org/fhir/R4/datatypes.html#code) | _17.0_ |
| data | The base64 encoded data of the attachment. | [base64Binary](http://hl7.org/fhir/R4/datatypes.html#base64Binary) | _17.0_ |

#### Example
<pre class="center-column">
{
    "resourceType": "Binary",
    "contentType": "text/plain",
    "data": "U0dWc2JHOGg=",
}
</pre>
&nbsp;

### *Get By ID*
Gets the binary form of a document by ID

#### HTTP Request 
`GET /r4/Binary/{documentType-id}` 

#### Parameters
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| documentType-id | Must be in the form `documenttype-id` i.e: GET /r4/Binary/history-5  | Yes | 17.0 |

#### Supported Document Types
The supported document type specifiers for IDs are `history-{id}` and `emn-{id}`.

#### Example: Get the binary form of a history document with ID 2262 which is a text file with a content of "Hello!"
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Binary/history-2262
</pre>
&nbsp;

