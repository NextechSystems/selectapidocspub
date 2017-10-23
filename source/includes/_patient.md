# Patient API

## Patient

### Overview
The patient resource contains information about the demographics of a patient.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| race | The race of the patient | [Race](https://www.hl7.org/fhir/v3/Race/cs.html) |
| ethnicity | The ethnicity of the patient | [Ethnicity](https://www.hl7.org/fhir/v3/Ethnicity/cs.html) |
| name | Names of the patient | [HumanName](https://www.hl7.org/fhir/datatypes.html#HumanName) |
| telecom | Contact details for the patient | [ContactPoint](https://www.hl7.org/fhir/datatypes.html#ContactPoint) |
| gender | The gender of the patient | [AdministrativeGender](https://www.hl7.org/fhir/valueset-administrative-gender.html) |
| birthDate | The date of birth of the patient | [date](https://www.hl7.org/fhir/datatypes.html#date) |
| address | Addresses associated with the patient | [Address](https://www.hl7.org/fhir/datatypes.html#Address) |
| communication | A list of Languages which may be used to communicate with the patient about his or her health | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) |

### Example
<pre class="center-column">
{
  "resourceType": "Patient",
  "id": "ad2085b5-b974-401d-bfcb-3b865109fd35",
  "extension": [
    {
      "url": "http://hl7.org/fhir/v3/Race",
      "valueCodeableConcept": {
        "coding": [
          {
            "system": "http://hl7.org/fhir/v3/Race",
            "code": "2106-3"
          }
        ],
        "text": "Caucasian"
      }
    },
    {
      "url": "http://hl7.org/fhir/v3/Ethnicity",
      "valueCodeableConcept": {
        "coding": [
          {
            "system": "http://hl7.org/fhir/v3/Ethnicity",
            "code": "2186-5"
          }
        ],
        "text": "Not Hispanic or Latino"
      }
    }
  ],
  "identifier": [
    {
      "use": "official",
      "value": "ad2085b5-b974-401d-bfcb-3b865109fd35"
    },
    {
      "use": "usual",
      "value": "4471"
    }
  ],
  "name": [
    {
      "text": "Jane L Smith",
      "family": "Smith",
      "given": [
        "Jane",
        "L"
      ]
    }
  ],
  "telecom": [
    {
      "system": "email",
      "value": "jsmith@email.com"
    },
    {
      "system": "phone",
      "value": "346-555-3682"
    }
  ],
  "gender": "female",
  "birthDate": "1968-02-04",
  "address": [
    {
      "use": "home",
      "type": "both",
      "line": [
        "3485 Forest Lane",
        "Apt 324"
      ],
      "city": "Houston",
      "state": "TX",
      "postalCode": "77014"
    }
  ],
  "communication": [
    {
      "language": {
        "coding": [
          {
            "system": "BCP-47",
            "code": "en"
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

### *Search*
Searches for all patients matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /Patient?{parameters}`

#### Parameters
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
| identifier | query | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | No | string |

#### Example: Get the patient of a specific chart number

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/12345
</pre>
&nbsp;

#### Example: Get all patients who live within a specific zip code

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?address-postalcode=12345
</pre>
&nbsp;

#### Example: Get all patients with birth dates between and including 1/1/1981 through 5/31/1981

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient?birthdate=ge1981-01-01&birthdate=lt1981-06-01
</pre>
&nbsp;

### Patient ID Search
Attempts to find a single patient that matches the given search criteria and if
successful returns only that patient's unique identifier.   

_At least one of query parameters is required to perform a search._

### HTTP Request 
`GET /Patient/ID?{parameters}` 

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
| identifier | query | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | No | string |

#### Example: Get the unique identifier of a patient given first name, last name, and birthdate

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ID?family=Smith&given=John&birthdate=eq1972-04-21
</pre>
&nbsp;

## AllergyIntolerance

### Overview
The allergy intolerance resource describes the risk of undesirable responses of exposure to a substance.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each allergy intolerance record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| clinicalStatus | Describes whether the allergy or intolerance is active, inactive or resolved | [AllergyIntoleranceStatus](https://www.hl7.org/fhir/valueset-allergy-clinical-status.html) |
| code | The clinical code that identifies the allergy or intolerance | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) |
| patient | The patient who the allergy or intolerance is for | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| assertedDate | The date the record was believed to be accurate | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "AllergyIntolerance",
        "id": "438",
		"identifier": [
		{
		  "use": "official",
		  "value": "438"
		}
	  ],
        "clinicalStatus": "active",
        "code": {
          "coding": [
            {
              "system": "http://www.nlm.nih.gov/research/umls/rxnorm",
              "code": "1191",
              "display": "Aspirin"
            }
          ],
          "text": "Aspirin"
        }
      }
    }
  ]
}
</pre>
&nbsp;
### *Search*
Searches for allergy intolerances for a single patient

#### HTTP Request
`GET /Patient/{patientUid}/AllergyIntolerance?{parameters}`

#### Parameters
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| date | query | The date the record was believed accurate in the form YYYY-MM-DD | No |

#### Example: Get all allergies for a single patient that were believed to be accurate as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/AllergyIntolerance?date=ge2017-01-01
</pre>
&nbsp;


## Binary

### Overview
Binary resources contain patient health information in a structured document or media form.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| contentType | MimeType of the binary content | [MimeType](http://www.rfc-editor.org/bcp/bcp13.txt) |
| content | The document content | [base64Binary](https://www.hl7.org/fhir/datatypes.html#base64Binary) |

### *Generate CCDA*
Generates a CCDA for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Binary/$autogen-ccd-if?{parameters}` 

#### Parameters
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | 
| start | query | The start date in the form YYYY-MM-DD for which the CCD should be generated (if not specified then all records starting with the patient's first visit are included) | No |
| end | query | The end date in the form YYYY-MM-DD for which the CCD should be generated (if not specified then all records through the patient's latest visit are included) | No |

#### Example: Get all CCDA's for a single patient corresponding to visits in 2007

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Binary/$autogen-ccd-if?start=2017-01-01&end=2018-01-01
</pre>
&nbsp;


## Care Plan

### Overview
A Care Plan contains patient diet, procedure, lab work and counseling and other care information for a single patient.   

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each care plan which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| subject | The patient pertaining to the care plan | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| activity | The collection of coded care plan actions | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) |

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
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- | 
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| date | query | The encounter visit date filter in the form YYYY-MM-DD | No |

#### Example: Get all care plans for a single patient charted on a visit on 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/CarePlan?date=eq2017-05-01
</pre>
&nbsp;


## Clinical Impression

### Overview
The clinical impression resource contains information regarding what problem(s) may affect the patient by treatment.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each clinical impression record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| subject | The patient pertaining to the clinical impression | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| date | When the assessment was documented | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| summary | Summary of the assessment | [string](https://www.hl7.org/fhir/datatypes.html#string) |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "ClinicalImpression",
        "id": "4567",
        "identifier": [
          {
            "use": "official",
            "value": "4567"
          }
        ],
        "subject": {
          "reference": "Patient/ad2085b5-b974-401d-bfcb-3b865109fd35"
        },
		"summary": "provisional diagnoses of laceration of head",
		"date": "2017-06-05"
      }
    }
  ]
}
</pre>
&nbsp;

### *Search*
Searches for clinical impressions for a patient

#### HTTP Request 
`GET /Patient/{patientUid}/ClinicalImpression?{parameters}` 

### Parameters
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| date | query | The collection of visit date filters | No |

#### Example: Get all clinical impressions for a single patient charted on a visit on 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/ClinicalImpression?date=eq2017-05-01
</pre>
&nbsp;


## Composition

### Overview
The Composition resource defines a collection of healthcare-related information bundled together as a single document that provides meaning for a given patient. 

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique identifier assigned to each composition | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| extension | See [flag-priority](http://hl7.org/fhir/StructureDefinition/flag-priority) extension | [CodableConcept](http://hl7.org/fhir/datatypes.html#CodeableConcept) |
| subject | The patient pertaining to the composition | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| date | The date of the composition (in UTC) | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| author | Identifies who is responsible for the information in the composition | [Reference(Practitioner)](https://www.hl7.org/fhir/references.html#Reference) |
| section.title | The name of the Nextech note category | [string](https://www.hl7.org/fhir/datatypes.html#string) |
| section.text | The contents of the composition | [Narrative](https://www.hl7.org/fhir/narrative.html) |

### Example
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "document",
    "total": 1,
    "entry": [
        {
            "resource": {
                "resourceType": "Composition",
                "id": "218",
                "contained": [
                    {
                        "resourceType": "Practitioner",
                        "id": "6763",
                        "identifier": [
                            {
                                "use": "official",
                                "value": "6763"
                            }
                        ],
                        "name": [
                            {
                                "text": "API User",
                                "family": "API User",
                                "given": [
                                    "",
                                    ""
                                ]
                            }
                        ]
                    }
                ],
                "extension": [
                    {
                        "url": "http://hl7.org/fhir/StructureDefinition/flag-priority",
                        "valueCodeableConcept": {
                            "coding": [
                                {
                                    "system": "http://hl7.org/fhir/flag-priority-code",
                                    "code": "PM",
                                    "display": "Medium priority"
                                }
                            ]
                        }
                    }
                ],
                "identifier": {
                    "use": "official",
                    "value": "218"
                },
                "subject": {
                    "reference": "Patient/05df1439-c610-4840-a569-8afbca008705",
                    "display": "Smith, John"
                },
                "date": "2017-10-16T20:32:28.97Z",
                "author": [
                    {
                        "reference": "#6763",
                        "display": "API User"
                    }
                ],
                "section": [
                    {
                        "title": "",
                        "text": {
                            "div": "API user - This is an example non-clinical patient note."
                        }
                    }
                ]
            }
        }
    ]
}
</pre>
&nbsp;

### *Create*
Creates a non-clinical note for a patient that is visible in the patient's Notes tab in the Nextech software.  

_Requires version 12.7_

#### HTTP Request 
`POST /Patient/{patientUid}/Composition` 

#### Parameters
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| composition | body | Represents the `Composition` resource to create for the given patient | Yes |

#### Body Fields
| Name | Description | Required |
| ---- | ----------- | -------- |
| resourceType | Must be `Composition` | Yes |
| extension | Must use `http://hl7.org/fhir/StructureDefinition/flag-priority` extension to specify the priority of the composition. See example below for specific format. Default priority code is `PL` | No |
| date | The date (in UTC) of the composition. ie. `2017-10-16T20:32:28.9692476Z` | No |
| author.display | The name of the author. This will be appended to the beginning of the `section.text.div` value. | No |
| section.title | The name of the Nextech note category. This must match with an existing note category or is left blank. | No |
| section.text.div | The non-clinical note associated with the subject. | No |

#### Example: Create a new non-clinical note for a patient
<pre class="center-column">
POST https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Composition
</pre>
&nbsp;

#### Body
<pre class="center-column">
{
	"resourceType": "Composition",
	"extension": [
		{
			"url": "http://hl7.org/fhir/StructureDefinition/flag-priority",
			"valueCodeableConcept": {
				"coding": [
					{
						"system": "http://hl7.org/fhir/flag-priority-code",
						"code": "PM"
					}	
				]
			}
		}
	],
    "date": "2017-10-16T20:32:28.9692476Z",
    "author": [
        {
            "display": "API user"
        }
    ],
    "section": [
    	{
    		"title": "Follow Up",
	        "text": {
	        	"div": "This is an example of a non-clinical patient note."
	        }
    	}
    ]
}
</pre>
&nbsp;


## Condition

### Overview
The condition resource describes a certain state of health of a patient.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each allergy intolerance record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| clinicalStatus | The condition status | [Condition Clinical Status Code](https://www.hl7.org/fhir/valueset-condition-clinical.html) |
| verificationStatus | The condition verification status | [ConditionVerificationstatus](https://www.hl7.org/fhir/valueset-condition-ver-status.html) |
| code | Identification of the condition, problem or diagnosis | [Condition/Problem/Diagnosis Code](https://www.hl7.org/fhir/valueset-condition-code.html) |
| subject | The patient pertaining to the condition | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| onsetDate | Estimated or actual date | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| abatementDate | Resolution or remission date | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |

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
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| onset-date | query | The onset date in the form YYYY-MM-DD | No |
| abatement-date | query | The abatement date in the form YYYY-MM-DD | No |

#### Example: Get all conditions for a single patient with an onset date as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Condition?onset-date=ge2017-01-01
</pre>
&nbsp;


## Device

### Overview
The device resource identifies an instance or type of manufactured item used in the provision of healthcare.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | Unique device serial number | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| meta | Contains the last updated date of the record | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| udi | Unique device barcode string | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) |
| lotNumber | Lot number of manufacturer | [string](https://www.hl7.org/fhir/datatypes.html#string) |
| manufacturer | Manufacturer name | [string](https://www.hl7.org/fhir/datatypes.html#string) |
| manufactureDate | Device manufacture date | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| expirationDate | Device expiration date | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| version | Version number | [string](https://www.hl7.org/fhir/datatypes.html#string) |
| patient | The patient pertaining to the device | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |

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
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- | 
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| date | query | The device last update date in the form YYYY-MM-DD | No |

#### Example: Get all devices for a single patient that were recorded as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Device?date=ge2017-01-01
</pre>
&nbsp;

## DocumentReference

### Overview
The DocumentReference resource is used to describe a document that is made available to a healthcare system. A document is some sequence of bytes that is identifiable, establishes its own context (e.g., what subject, author, etc. can be displayed to the user), and has defined update management. The DocumentReference resource can be used with any document format that has a recognized mime type and that conforms to this definition.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| masteridentifier | The unique identifier assigned to each documentreference | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| subject | The patient pertaining to the documentreference | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| created | document creation time (in UTC) | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| author | Identifies who is responsible for the information in the document reference | [Reference(Practitioner)](https://www.hl7.org/fhir/references.html#Reference) |
| description | The description of the documentreference | [string](https://www.hl7.org/fhir/datatypes.html#string) |
| content.attachment.contentType | The mimetype of the content.| [Code](https://www.hl7.org/fhir/datatypes.html#code) |
| content.attachment.title | The title of the document| [string](https://www.hl7.org/fhir/datatypes.html#string) |

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
    "created": "2017-10-16T16:32:28.97-04:00",
    "author": [
        {
            "reference": "nexweb"
        }
    ],
    "description": "Author: API user \r\n Note: A description of the document",
    "content": [
        {
            "attachment": {				
                "contentType": "application/pdf",
                "title": "Document Title (6).pdf"
            }
        }
    ]
}
</pre>
&nbsp;

### *Create*
Creates the document in the content.attachment for a patient and attaches it to the patient's history tab in the Nextech software.  

_Requires version 12.7_

#### HTTP Request 
`POST /Patient/{patientUid}/DocumentReference` 

#### Parameters
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| documentreference | body | Represents the `DocumentReference` resource to create for the given patient | Yes |

#### Body Fields
| Name | Description | Required |
| ---- | ----------- | -------- |
| resourceType | Must be `DocumentReference` | Yes |
| created | The date (in UTC) of the composition. ie. `2017-10-16T20:32:28.9692476Z` | No |
| author.display | The name of the author. This will be appended to the beginning of the description value. | No |
| description | A description of the document | No |
| content.attachment.contentType | The mimetype of the document. See Allowed Mimetypes below | Yes |
| content.attachment.data | The base64 data of the document | Yes |
| content.attachment.title | The title of the document, will be used as the filename| Yes |

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
  "content": [
    {
      "attachment": {
        "contentType": "application/pdf",
		"title": "Document Title",
        "data": "<Snipped for Brevity>"
      }
    }
  ]
}
</pre>
&nbsp;

###Allowed Mimetypes
The following mimetypes are currently supported:
|Document Type | MimeType |
|--------------|----------|
|PDF|application/pdf|
|Microsoft Word|application/msword|
|Microsoft Excel|application/vnd.ms-excel or application/vnd.ms-excel.12|
|Tif Image files| application/tif, application/tiff, or image/tiff|
|HTML| text/html|
|Text| text/plain|
|XML|text/xml|
|BMP Image|image/bmp|
|GIF Image|image/gif|
|JPG Image|image/jpeg|
|PNG Image|image/png or image/x-png|


## Encounter

### Overview
The encounter resource describes an interaction between a patient and healthcare provider.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each encounter which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| subject | The patient pertaining to the encounter | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| participant | The medical professionals involved in the encounter | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) |
| period | The start and end date of the encounter in the form YYYY-MM-DD | [period](https://www.hl7.org/fhir/datatypes.html#Period) |

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
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| date | query | The date of the encounter in the form YYYY-MM-DD | No |

#### Example: Get all encounters for a single patient as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Encounter?date=ge2017-01-01
</pre>
&nbsp;


## Goal

### Overview
The goal resource describes a desired state of health for a patient.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each goal which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| subject | The patient pertaining to the goal | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| target | The target outcome of the goal | [CodeableConcept](https://www.hl7.org/fhir/backboneelement.html) |
| note | Comments about the goal | [Annotation](https://www.hl7.org/fhir/datatypes.html#Annotation) | 

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
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| date | query | The date of the encounter containing the goal in the form YYYY-MM-DD | No |

#### Example: Get all goals for a single patient charted on a visit on 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Goal?date=eq2017-05-01
</pre>
&nbsp;


## Immunization

### Overview
The immunization resource describes an administered vaccine.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each immunization which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| status | Either completed or entered in error | [Immunization status Code](https://www.hl7.org/fhir/valueset-immunization-status.html) |
| vaccineCode | Vaccine product adminstered | [Vaccine administered value set](https://www.hl7.org/fhir/valueset-vaccine-code.html) |
| patient | The immunized patient | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| date | The vaccination administration date in the form YYYY-MM-DD | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Immunization",
        "id": "immunization-1",
        "identifier": [
          {
            "use": "official",
            "value": "immunization-1"
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
        "date": "2013-08-17"
      }
    }
  ]
}
</pre>
&nbsp;

### *Search*
Searches for immunizations for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Immunization?{parameters}` 

#### Parameters
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- | 
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| date | query | The immunization administration date in the form YYYY-MM-DD | No |

#### Example: Get all immunizations for a single patient as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Immunization?date=ge2017-01-01
</pre>
&nbsp;


## Medication Dispensement

### Overview
The medication dispersement resource describes the supply of medications by a health care provider to a patient.

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each dispensement which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| medicationCodeableConcept | The supplied medication | [SNOMED CT Medication Code](https://www.hl7.org/fhir/valueset-medication-codes.html) |
| subject | The patient pertaining to the dispensement | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| whenPrepared | When product was packaged and reviewed | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "MedicationDispense",
        "id": "5172",
        "identifier": [
          {
            "use": "official",
            "value": "5172"
          }
        ],
        "medicationCodeableConcept": {
          "coding": [
            {
              "system": "http://www.nlm.nih.gov/research/umls/rxnorm",
              "code": "977434",
              "display": "Zortress 0.5 mg tablet"
            }
          ],
          "text": "Zortress 0.5 mg tablet"
        },
        "subject": {
          "reference": "Patient/Patient/56a784fa-4334-469d-dd12-a93248c74be3",
          "display": "Horus, Lana"
        },
        "whenPrepared": "2015-08-14"
      }
    }
  ]
}
</pre>
&nbsp;

### *Search*
Searches for medication dispensements for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/MedicationDispense?{parameters}` 

#### Parameters
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| whenPrepared | query | The preparation date in the form YYYY-MM-DD | No |

#### Example: Get all prescriptions for a single patient prepared as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/MedicationDispense?whenPrepared=ge2017-05-01
</pre>
&nbsp;


## Medication Statements

### Overview
A medication statement resource describes a medication being consumed by a patient. This includes medications not prescribed by the health care provider. 

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each medication statement which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| status | The statement status | [MedicationStatementStatus](https://www.hl7.org/fhir/valueset-medication-statement-status.html) |
| medication | The supplied medication | [SNOMED CT Medication Code](https://www.hl7.org/fhir/valueset-medication-codes.html) |
| effective | The date/time when the medication was taken | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| subject | The patient pertaining to the medication statement | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |

### Example
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "MedicationStatement",
        "id": "344",
        "identifier": [
          {
            "use": "official",
            "value": "344"
          }
        ],
        "status": "active",
        "medicationCodeableConcept": {
          "coding": [
            {
              "system": "http://www.nlm.nih.gov/research/umls/rxnorm",
              "code": "310964",
              "display": "Advil Liqui-Gel 200 mg capsule"
            }
          ],
          "text": "Advil Liqui-Gel 200 mg capsule"
        },
        "effectiveDateTime": "2014-03-04",
        "subject": {
          "reference": "Patient/Patient/c27e5be0-4b44-4ec5-a284-4308d6ac2b1a",
          "display": "Clay, William"
        }
      }
    }
  ]
}
</pre>
&nbsp;

### *Search*
Searches for current medications for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/MedicationStatement?{parameters}`

#### Parameters
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| effective | query | Date when patient was taking the medication in the form YYYY-MM-DD | No |

#### Example: Get all current medications for a single patient effective 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/MedicationStatement?date=ge2017-05-01
</pre>
&nbsp;


## Observation

### Overview
An observation resource describes a measurement or an assertion made about a patient. This request requires a category code to search on. The following category codes are supported:

* laboratory
* social-history
* vital-signs

### Fields
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each observation which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| subject | The patient pertaining to the observation | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| status | The observation status | [ObservationStatus](https://www.hl7.org/fhir/valueset-observation-status.html) |
| category | Classification of type of observation | [Category](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) |
| code | Type of observation | [LOINC Code](https://www.hl7.org/fhir/valueset-observation-codes.html) |
| effective | Clinically relevant time/time-period for observation | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |
| value | Observation result | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) |

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
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| category | query | The category of observation to load | Yes | 
| date | query | The observation date in the form YYYY-MM-DD | No |

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
| Name | Description | Type |
| ---- | ---------- | ----------- |
| identifier | The unique value assigned to each goal which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) |
| code | Identification of the procedure | [Procedure Codes (SNOMED CT)](https://www.hl7.org/fhir/valueset-procedure-code.html) |
| subject | Who the procedure was performed on | [Reference(Patient)](https://www.hl7.org/fhir/references.html) |
| performed | Date/Period the procedure was performed | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |

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
| Name | Located in | Description | Required |
| ---- | ---------- | ----------- | -------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes |
| date | query | The date the procedure was performed in the form YYYY-MM-DD | No |

#### Example: Get all procedures for a single patient performed as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Procedure?date=ge2017-05-01
</pre>
&nbsp;
