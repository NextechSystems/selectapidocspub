# Patient

## Patient

### Overview
The patient resource contains information about the demographics of a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The unique identifier of the patient | [string](http://hl7.org/fhir/R4/datatypes.html#string) | _12.6_ |
| identifier | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number. <br/><br/> As a convenience for some use cases, in version 14.1 and above, the patient's masked social security number (last four only) is also returned in this field if available. | [Identifier](http://hl7.org/fhir/R4/datatypes.html#Identifier) | _12.6_ |
| extension:race | The race of the patient | [Extension](http://hl7.org/fhir/R4/extensibility.html#Extension) ([USCoreRaceExtension](http://hl7.org/fhir/us/core/STU4/StructureDefinition-us-core-race.html)) | _12.6_ |
| extension:ethnicity | The ethnicity of the patient | [Extension](http://hl7.org/fhir/R4/extensibility.html#Extension) ([USCoreEthnicityExtension](http://hl7.org/fhir/us/core/STU4/StructureDefinition-us-core-ethnicity.html)) | _12.6_ |
| extension:birthsex | The patient's sex assigned at birth | [Extension](http://hl7.org/fhir/R4/extensibility.html#Extension) ([USCoreBirthSexExtension](http://hl7.org/fhir/us/core/STU4/StructureDefinition-us-core-birthsex.html)) | |
| name | Names of the patient, additional information including prefix and nickname added in version 12.9.20 | [HumanName](http://hl7.org/fhir/R4/datatypes.html#HumanName) | _12.6_ |
| telecom | Contact details for the patient, fax, preferred contact, and other phone added 12.9.20 | [ContactPoint](http://hl7.org/fhir/R4/datatypes.html#ContactPoint) | _12.6_ |
| gender | The gender of the patient | [code](http://hl7.org/fhir/R4/datatypes.html#code) | _12.6_ |
| birthDate | The date of birth of the patient | [date](http://hl7.org/fhir/R4/datatypes.html#date) | _12.6_ |
| address | Addresses associated with the patient | [Address](http://hl7.org/fhir/R4/datatypes.html#Address) | _12.6_ |
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
Searches for all patients matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
- `GET /r4/Patient?{parameters}`
- `POST /r4/Patient/_search`
  - *application/x-www-form-urlencoded payload:* `{parameters}`
> **_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Type | Initial Version |
| ---- | ---------- | ----------- | -------- | ---- | --------------- |
| _lastUpdated | query | The date the patient was last modified formatted as yyyy-MM-dd. As of version 14.3, we also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] | No | dateTime | _12.8_ |
| family | query | The family (last) name of the patient | No | string | _12.6_ |
| given | query | The given (first) name of the patient | No | string | _12.6_ |
| birthdate | query | The patient's date of birth formatted as YYYY-MM-DD | No | dateTime | _12.6_ |
| phone | query | The patient's phone number which will be matched against any phone number (home, cell, etc.) | No | string | _12.6_ |
| email | query | The patient's email address | No | string | _12.6_ |
| address-city | query | The city of the patient's address | No | string | _12.6_ |
| address-state | query | The state of the patient's address | No | string | _12.6_ |
| address-postalcode | query | The postal (zip) code of the patient's address | No | string | _12.6_ |
| identifier | query | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | No | string | _12.6_ |
| _id | query | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | No | string | _12.6_ |
| gender | query | The gender of the patient | No | string | _12.6_ |
| name | query | The given(first) name, middle name, family(last) name, prefix or title of the patient | No | string |  |

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
<i><small>payload:</small></i> identifier=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?_id=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>payload:</small></i> _id=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

#### Example: Get all patients who live within '12345' zip code

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?address-postalcode=12345
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>payload:</small></i> address-postalcode=12345
</pre>

#### Example: Get all patients with birth dates between and including 1/1/1981 through 5/31/1981

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient?birthdate=ge1981-01-01&birthdate=lt1981-05-31
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Patient/_search
<i><small>payload:</small></i> birthdate=ge1981-01-01&birthdate=lt1981-05-31
</pre>


## Allergy Intolerance

### Overview
The allergy intolerance resource describes the risk of undesirable responses of exposure to a substance.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The logical id of the resource, as used in the URL for the resource. | [string](http://hl7.org/fhir/R4/datatypes.html#string) |  |
| identifier | The unique value assigned to each allergy intolerance record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| clinicalStatus | Describes whether the allergy or intolerance is active, inactive or resolved | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) |  |
| verificationStatus | Assertion about certainty associated with the propensity, or potential risk, of a reaction to the identified substance (including pharmaceutical product). | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) |  |
| code | The clinical code that identifies the allergy or intolerance | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.6_ |
| patient | The patient who the allergy or intolerance is for | [Reference](http://hl7.org/fhir/R4/references.html#Reference) [(USCorePatientProfile)](https://www.hl7.org/fhir/us/core/StructureDefinition-us-core-patient.html) | _12.6_ |
| reaction | Details about each adverse reaction event linked to exposure to the identified substance. | [BackboneElement](http://hl7.org/fhir/R4/datatypes.html#BackboneElement) | |
| reaction.manifestation | Clinical symptoms and/or signs that are observed or associated with the adverse reaction event. |  [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | |

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
- `GET /r4/Patient/{patientUid}/AllergyIntolerance?[date=(filter)YYYY-MM-DD]`

- `GET /r4/AllergyIntolerance?patient={patientUid}&[date=(filter)YYYY-MM-DD]`

- `GET /r4/AllergyIntolerance?patient=Patient/{patientUid}&[date=(filter)YYYY-MM-DD]`

- `POST /r4/Patient/AllergyIntolerance/_search`
*payload:* `patient={patientUid}`




#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path, query or payload | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The date the record was believed accurate in the form YYYY-MM-DD  | No | _12.6_ |

> **_Note:_**  The possible filter values for date parameter are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

&nbsp;
#### Examples: 

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient/b664fd37-ff5f-4022-9d71-2e476d42f316/AllergyIntolerance?date=ge2022-01-01
</pre>
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/AllergyIntolerance?patient=b664fd37-ff5f-4022-9d71-2e476d42f316
</pre>
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/AllergyIntolerance?patient=Patient/b664fd37-ff5f-4022-9d71-2e476d42f316
</pre>
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/AllergyIntolerance/_search
<i><small>payload:</small></i> patient=b664fd37-ff5f-4022-9d71-2e476d42f316
</pre>
&nbsp;

### *Get*
Returns single Allergy result based on the Allergy ID.

#### HTTP Request

- `GET /r4/AllergyIntolerance/{allergyID}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| allergyID | path | The allergy unique identifier | Yes |  |

&nbsp;
#### Example: 
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/AllergyIntolerance/21
</pre>

&nbsp;

## Care Plan

### Overview
A Care Plan contains patient diet, procedure, lab work and counseling and other care information for a single patient.   

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each care plan which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| subject | The patient pertaining to the care plan | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| activity | The collection of coded care plan actions | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | _12.6_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "CarePlan",
        "id": "3099",
        "identifier": [
          {
            "use": "official",
            "value": "3099"
          }
        ],
        "subject": {
          "reference": "Patient/ad2085b5-b974-401d-bfcb-3b865109fd35"
        },
        "activity": [
          {
            "id": "pocinsemn-3099code-745799",
            "detail": {
              "code": {
                "coding": [
                  {
                    "system": "2.16.840.1.113883.10.20.22.4.20",
                    "code": "225323000"
                  }
                ],
                "text": "Smoking cessation education"
              },
              "description": "Patient to read literature on lung tissue damage"
            }
          }
        ]
      }
    }
  ]
}
</pre>
&nbsp;

### *Search*
Searches for care plans for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/CarePlan?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The encounter visit date filter in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all care plans for a single patient charted on a visit on 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/CarePlan?date=eq2017-05-01
</pre>
&nbsp;

## Condition

### Overview
The condition resource describes a certain state of health of a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each allergy intolerance record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| clinicalStatus | The condition status | [Condition Clinical Status Code](https://www.hl7.org/fhir/valueset-condition-clinical.html) | _12.6_ |
| verificationStatus | The condition verification status | [ConditionVerificationstatus](https://www.hl7.org/fhir/valueset-condition-ver-status.html) | _12.6_ |
| code | Identification of the condition, problem or diagnosis | [Condition/Problem/Diagnosis Code](https://www.hl7.org/fhir/valueset-condition-code.html) | _12.6_ |
| subject | The patient pertaining to the condition | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| onsetDate | Estimated or actual date | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |
| abatementDate | Resolution or remission date | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Condition",
        "id": "54",
        "identifier": [
          {
            "use": "official",
            "value": "54"
          }
        ],
        "clinicalStatus": "active",
        "verificationStatus": "confirmed",
        "code": {
          "coding": [
            {
              "system": "SNOMED",
              "code": "11381005"
            }
          ],
          "text": "Acne"
        },
        "subject": {
          "reference": "Patient/ad2085b5-b974-401d-bfcb-3b865109fd35"
        },
        "onsetDate": "2015-06-05"
      }
    }
  ]
}
</pre>
&nbsp;

### *Search*
Searches for conditions for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Condition?{parameters}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| onset-date | query | The onset date in the form YYYY-MM-DD | No | _12.6_ |
| abatement-date | query | The abatement date in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all conditions for a single patient with an onset date as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Condition?onset-date=ge2017-01-01
</pre>
&nbsp;


## Device

### Overview
The device resource identifies an instance or type of manufactured item used in the provision of healthcare.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | Unique device serial number | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| meta | Contains the last updated date of the record | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |
| udi | Unique device barcode string | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | _12.6_ |
| lotNumber | Lot number of manufacturer | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.6_ |
| manufacturer | Manufacturer name | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.6_ |
| manufactureDate | Device manufacture date | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |
| expirationDate | Device expiration date | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |
| version | Version number | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.6_ |
| patient | The patient pertaining to the device | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Device",
        "id": "2",
        "meta": {
          "lastUpdated": "2017-05-15T10:28:00+00:00"
        },
        "identifier": [
          {
            "type": {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/identifier-type",
                  "code": "SNO",
                  "display": "Serial Number"
                }
              ],
              "text": "Serial Number"
            },
            "value": "000025"
          }
        ],
        "udi": {
          "deviceIdentifier": "W4146EB0010T0475",
          "name": "Trabexus® EB"
        },
        "type": {
          "text": "Cadaveric-donor/synthetic mineral bone graft"
        },
        "lotNumber": "000000000000XYZ123",
        "manufacturer": "Vivorte, Inc",
        "manufactureDate": "2013-02-01T00:00:00Z",
        "expirationDate": "2014-02-01T00:00:00Z",
        "version": "10 cc",
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

### *Search*
Searches for devices for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Device?{parameters}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The device last update date in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all devices for a single patient that were recorded as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Device?date=ge2017-01-01
</pre>
&nbsp;

## Document Reference

### Overview
The DocumentReference resource is used to describe a document that is made available to a healthcare system. A document is some sequence of bytes that is identifiable, establishes its own context (e.g., what subject, author, etc. can be displayed to the user), and has defined update management. The DocumentReference resource can be used with any document format that has a recognized mime type and that conforms to this definition.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| masteridentifier | The unique identifier assigned to each documentreference | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.7_ |
| subject | The patient pertaining to the documentreference | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.7_ |
| created | document creation time (in UTC) | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.7_ |
| author | Identifies who is responsible for the information in the document reference | [Reference(Practitioner)](https://www.hl7.org/fhir/references.html#Reference) | _12.7_ |
| description | The description of the documentreference | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.7_ |
| content.attachment.contentType | The mimetype of the content.| [Code](https://www.hl7.org/fhir/datatypes.html#code) | _12.7_ |
| content.attachment.title | The title of the document| [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.7_ |
| extension: note-category | Contains the category of the document | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| extension: document-publish-portal | Contains whether the document is published to myPatientVisit | [boolean](https://www.hl7.org/fhir/datatypes.html#boolean)  | _12.9.20_ |

### Example
<pre class="center-column">
{
    "resourceType": "DocumentReference",
    "id": "8529",
    "masterIdentifier": {
        "use": "official",
        "value": "8529"
    },
    "subject": {
        "reference": "Patient/22b51855-0fe2-47a3-8000-4344b4e8e69d",
        "display": "Dateline, Martha R"
    },
    "created": "2017-10-24T20:10:36Z",
     "author": [
        {
            "reference": "",
            "display": "nexweb"
        }
    ],
    "description": "Author: API user \r\n Note: A description of the document",
	"extension": [
		{
			"url": "https://select.nextech-api.com/api/structuredefinition/note-category",
			"valueString": "Past Medical History"
		},
		{
 		    "url": "https://select.nextech-api.com/api/structuredefinition/document-publish-portal",
		    "valueBoolean": true
		}
    ],
    "content": [
        {
            "attachment": {				
                "contentType": "application/pdf",
                "title": "Document Title.pdf"
            }
        }
    ]
}
</pre>
&nbsp;

### *Create*
Creates the document in the content.attachment for a patient and attaches it to the patient's history tab in the Nextech software.

#### HTTP Request 
`POST /Patient/{patientUid}/DocumentReference` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.7_ |
| documentreference | body | Represents the `DocumentReference` resource to create for the given patient. The request length must not exceed 10 MB in size. | Yes | _12.7_ |

#### Body Fields
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| resourceType | Must be `DocumentReference` | Yes |
| created | The date (in UTC) of the composition. ie. `2017-10-16T20:32:28.9692476Z` | No | _12.7_ |
| author.display | The name of the author. This will be appended to the beginning of the description value. | No | _12.7_ |
| description | A description of the document | No | _12.7_ |
| content.attachment.contentType | The mimetype of the document. See Allowed Mimetypes below | Yes | _12.7_ |
| content.attachment.data | The base64 data of the document | Yes | _12.7_ |
| content.attachment.title | The title of the document, will be used as the filename| Yes | _12.7_ |
| extension: note-category | Allows setting category of the document | No | _12.8_ |
| extension: document-publish-portal | Allows setting whether or not to publish the document to myPatientVisit. Note: Must be licensed for myPatientVisit and have permission to publish EMNs to MPV to work | No | _12.9.20_ |

### Extension: note-category
This is a custom extension to allow the setting of the category on the document. This must match with an existing note category or is left blank.  There can be only one note-category extension.

Url: https://select.nextech-api.com/api/structuredefinition/note-category
valueString: Name of Nextech note category

### Extension: document-publish-portal
This is a custom extension to allow publishing of a document to myPatientVisit. The client must be licensed for myPatientVisit and the caller must have permission to publish EMNs to MPV, otherwise the document will not be published.  There can be only one document-publish-portal extension.  If this extension is not included in the POST, the document is not published to myPatientVisit.

Url: https://select.nextech-api.com/api/structuredefinition/document-publish-portal
valueBoolean: true or false

#### Example: Attach a new document for a patient
<pre class="center-column">
POST https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/DocumentReference
</pre>
&nbsp;

#### Body
<pre class="center-column">
{
  "resourceType": "DocumentReference",  
  "author": [
        {
            "display": "API user"
        }
  ],  
  "created": "2017-10-16T20:32:28.9692476Z",
  "description": "A description of the document",
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
  "content": [
    {
      "attachment": {
        "contentType": "text/plain",
		"title": "Sample Document",
        "data": "c2FtcGxlIGRvY3VtZW50"
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
The encounter resource describes an interaction between a patient and healthcare provider.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each encounter which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| subject | The patient pertaining to the encounter | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| participant | The medical professionals involved in the encounter | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | _12.6_ |
| period | The start and end date of the encounter in the form YYYY-MM-DD | [period](https://www.hl7.org/fhir/datatypes.html#Period) | _12.6_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Encounter",
        "id": "1294",
        "contained": [
          {
            "resourceType": "Practitioner",
            "id": "9938",
            "identifier": [
              {
                "use": "usual",
                "system": "http://hl7.org/fhir/sid/us-npi",
                "value": "11192383741"
              }
            ],
            "name": [
              {
                "text": "Davison, Darren",
                "family": "Davison",
                "given": [
                  "Darren",
                  "L"
                ]
              }
            ]
          }
        ],
        "identifier": [
          {
            "use": "official",
            "value": "1294"
          }
        ],
        "subject": {
          "reference": "Patient/45822",
          "display": "Smith, John"
        },
        "participant": [
          {
            "type": [
              {
                "coding": [
                  {
                    "system": "http://hl7.org/fhir/v3/ParticipationType",
                    "code": "PRF"
                  }
                ]
              }
            ],
            "individual": {
              "reference": "Practitioner/9938"
            }
          }
        ],
        "period": {
          "start": "2015-05-03",
          "end": "2015-05-03"
        }
      }
    }
  ]
}
</pre>
&nbsp;

### *Search*
Searches for encounters for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Encounter?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The date of the encounter in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all encounters for a single patient as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Encounter?date=ge2017-01-01
</pre>
&nbsp;


## Goal

### Overview
The goal resource describes a desired state of health for a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each goal which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| subject | The patient pertaining to the goal | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| target | The target outcome of the goal | [CodeableConcept](https://www.hl7.org/fhir/backboneelement.html) | _12.6_ |
| note | Comments about the goal | [Annotation](https://www.hl7.org/fhir/datatypes.html#Annotation) | _12.6_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Goal",
        "id": "goalemn-2284code-559215",
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

### *Search*
Searches for goals for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Goal?{parameters}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The date of the encounter containing the goal in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all goals for a single patient charted on a visit on 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Goal?date=eq2017-05-01
</pre>
&nbsp;


## Immunization

### Overview
The immunization resource describes an administered vaccine.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | The logical id of the resource, as used in the URL for the resource. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _16.7_ |
| identifier | The unique value assigned to each immunization which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _16.7_ |
| status | Either `completed` or `not-done` | [code](https://hl7.org/fhir/R4/datatypes.html#code) with [immunization status value set](https://hl7.org/fhir/R4/valueset-immunization-status.html) | _16.7_ |
| statusReason | Reason that an immunization event was not performed, if any | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) using [ActReason value set](https://hl7.org/fhir/R4/v3/ActReason/cs.html) | _16.7_ |
| vaccineCode | Vaccine product administered | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) using [vaccine administered value set](https://www.hl7.org/fhir/R4/valueset-vaccine-code.html) | _16.7_ |
| patient | The immunized patient | [Reference](https://www.hl7.org/fhir/R4/references.html) ([USCorePatientProfile](https://www.hl7.org/fhir/us/core/StructureDefinition-us-core-patient.html)) | _16.7_ |
| occurrenceDateTime | The vaccination administration date in the form YYYY-MM-DD | [dateTime](https://www.hl7.org/fhir/R4/datatypes.html#dateTime) | _16.7_ |
| primarySource | Whether or not the information is from the person who administered the vaccine | [boolean](https://www.hl7.org/fhir/R4/datatypes.html#boolean) | _16.7_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Immunization",
        "id": "123",
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

HTTP Requests
- `GET /r4/Immunization?{parameters}`
- `POST /r4/Immunization/_search`
  - *application/x-www-form-urlencoded payload:* `{parameters}`
> **_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patient | query or payload | The official patient identifier acquired from a patient search | No | _16.7_ |
| date | query or payload | The date the immunization was administered in the form YYYY-MM-DD  | No | _16.7_ |
| identifier | query or payload | The immunization unique identifier | No | _16.7_ |
| _id | query or payload | The immunization unique identifier | No | _16.7_ |

> **_Note:_**  The possible filter values for date parameter are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

&nbsp;
#### Examples: 

#### Get all immunizations

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization
</pre>

#### Search for immunizations under the patient with the id '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization?patient=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Immunization/_search
<i><small>payload:</small></i> patient=9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192
</pre>

#### Search for immunizations under the patient with the id '9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192' administered between and including 1/1/2022 through 11/14/2022

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization?patient=patient/9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&date=ge2022-01-01&date=lt2022-11-14
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Immunization/_search
<i><small>payload:</small></i> patient=patient/9D0B7ADE-4B5B-41DD-8AC4-88DB4C93B192&date=ge2022-01-01&date=lt2022-11-14
</pre>

#### Search for an immunization with the id '123'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization?identifier=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Immunization/_search
<i><small>payload:</small></i> identifier=123
</pre>

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Immunization?_id=123
</pre>

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/Immunization/_search
<i><small>payload:</small></i> _id=123
</pre>

&nbsp;

## Observation

### Overview
An observation resource describes a measurement or an assertion made about a patient. This request requires a category code to search on. The following category codes are supported:

* laboratory
* social-history
* vital-signs

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each observation which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| subject | The patient pertaining to the observation | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| status | The observation status | [ObservationStatus](https://www.hl7.org/fhir/valueset-observation-status.html) | _12.6_ |
| category | Classification of type of observation | [Category](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.6_ |
| code | Type of observation | [LOINC Code](https://www.hl7.org/fhir/valueset-observation-codes.html) | _12.6_ |
| effective | Clinically relevant time/time-period for observation | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |
| value | Observation result | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.6_ |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Observation",
        "id": "smokestatemn-3093code-745770",
        "identifier": [
          {
            "use": "official",
            "value": "smokestatemn-3093code-745770"
          }
        ],
        "status": "final",
        "category": [
          {
            "coding": [
              {
                "system": "observation-category",
                "code": "social-history"
              }
            ],
            "text": "Social History"
          }
        ],
        "code": {
          "coding": [
            {
              "system": "http://loinc.org",
              "code": "72166-2"
            }
          ]
        },
        "subject": {
          "reference": "Patient/F15FB185-5E63-485E-B025-D113103DCEC3",
          "display": "Morgan, Stanley"
        },
        "effectivePeriod": {
          "start": "2009-03-02",
          "end": "2013-08-17"
        },
        "valueCodeableConcept": {
          "coding": [
            {
              "system": "2.16.840.1.113883.6.96",
              "code": "8517006"
            }
          ],
          "text": "Ex-smoker"
        }
      }
    }
  ]
}
</pre> 
&nbsp;

### *Search*
Searches for observations for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Observation?{parameters}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| category | query | The category of observation to load | Yes | _12.6_ |
| date | query | The observation date in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all laboratory requisitions and results for a single patient as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Observation?category=laboratory&date=ge2017-05-01
</pre>
&nbsp;

#### Example: Get the social history of a single patient charted in encounters as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Observation?category=social-history&date=ge2017-05-01
</pre>
&nbsp;

#### Example: Get the vital signs of a single patient charted in encounters as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Observation?category=vital-signs&date=ge2017-05-01
</pre>
&nbsp;

## Procedure

### Overview
A procedure resource describes an activity performed with or on a patient as part of the provision of care.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each goal which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| code | Identification of the procedure | [Procedure Codes (SNOMED CT)](https://www.hl7.org/fhir/valueset-procedure-code.html) | _12.6_ |
| subject | Who the procedure was performed on | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| performed | Date/Period the procedure was performed | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |

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
        "code": {
          "coding": [
            {
              "system": "CPT4",
              "code": "54601"
            }
          ],
          "text": "Microdermabrasion"
        },
        "subject": {
          "reference": "Patient/5F37E582-FD96-48C5-9EE3-02E26D96CB72",
          "display": "Smith, John"
        }
      }
    }
  ]
}
</pre>
&nbsp;

### *Search*
Searches for procedures for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Procedure?{parameters}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The date the procedure was performed in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all procedures for a single patient performed as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Procedure?date=ge2017-05-01
</pre>
&nbsp;
