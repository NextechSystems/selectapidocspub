# Patient

## Patient

### Overview
The patient resource contains information about the demographics of a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number. <br/><br/> As a convenience for some use cases, in version 14.1 and above, the patient's masked social security number (last four only) is also returned in this field if available. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| race | The race of the patient | [Race](https://www.hl7.org/fhir/v3/Race/cs.html) | _12.6_ |
| ethnicity | The ethnicity of the patient | [Ethnicity](https://www.hl7.org/fhir/v3/Ethnicity/cs.html) | _12.6_ |
| name | Names of the patient, additional information including prefix and nickname added in version 12.9.20 | [HumanName](https://www.hl7.org/fhir/datatypes.html#HumanName) | _12.6_ |
| telecom | Contact details for the patient, fax, preferred contact, and other phone added 12.9.20 | [ContactPoint](https://www.hl7.org/fhir/datatypes.html#ContactPoint) | _12.6_ |
| gender | The gender of the patient | [AdministrativeGender](https://www.hl7.org/fhir/valueset-administrative-gender.html) | _12.6_ |
| birthDate | The date of birth of the patient | [date](https://www.hl7.org/fhir/datatypes.html#date) | _12.6_ |
| address | Addresses associated with the patient | [Address](https://www.hl7.org/fhir/datatypes.html#Address) | _12.6_ |
| communication | A list of Languages which may be used to communicate with the patient about his or her health | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | _12.6_ |
| maritalStatus | The marital status of the patient | [Codeable Concept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9.20_ | 
| contact | The emergency contact and employer for the patient | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | _12.9.20_ |
| generalPractitioner | The practitioner at this office who is responsible for the patient | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| patient-note | The text of the General 1 note for the patient, contained in the extension | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.9.20_ |
| referral-source | The primary referral source for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| referring-physician | The referring physician for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| referring-physician.HumanName | The referring physician name, contained in the extension | [HumanName](https://www.hl7.org/fhir/datatypes.html#HumanName) | _14.3_ |
| referring-patient | The unique identifier for the referring patient for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| primary-care-physician | The primary care physician for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| patient-location | The default location for patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| affiliate-physician | The affiliate physician for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| affiliate-physician-type | The affiliate physician type for the patient, contained in the extension | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.9.20_ |
| patient-employment-status | The employment status for the patient, contained in the extension | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.9.20_ |
| patients-referred | The number of patients this patient has referred, contained in the extension | [integer](https://www.hl7.org/fhir/datatypes.html#integer) | _14.1_ |
| prospects-referred | The number of prospects this patient has referred, contained in the extension | [integer](https://www.hl7.org/fhir/datatypes.html#integer) | _14.1_ |
| patient-type | The patient type for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _14.1_ |
| patient-status | The status for the patient (patient, prospect, or patientprospect), contained in the extension | [string](https://www.hl7.org/fhir/datatypes.html#string) | _14.1_ |
| exclude-from-mailings | Whether this patient is excluded from mailings, contained in the extension | [boolean](https://www.hl7.org/fhir/datatypes.html#boolean) | _14.1_ |
| meta.lastUpdated | The last time the patient was modified | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | _14.3_ |


### Example
<pre class="center-column">
{
    "resourceType": "Patient",
    "id": "45bb641e-44c5-49a8-a36f-9dd7a0a50828",
    "meta":
    {
        "lastUpdated": "2018-12-20T09:13:28.297+00:00"
    },
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
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/referral-source",
            "valueReference": {
                "reference": "referral-source/9238",
                "display": "Website"
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/referring-physician",
            "valueReference": {
                "reference": "referring-physician/23",
                "display": "Dole, Robert"
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/primary-care-physician",
            "valueReference": {
                "reference": "primary-care-physician/43",
                "display": "Hogan, Terry "
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/referring-patient",
            "valueReference": {
                "reference": "patient/f5a46423-0071-4437-aa34-231419fe970f",
                "display": "Brown, Phyllis"
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/affiliate-physician",
            "valueReference": {
                "reference": "affiliate-physician/6845",
                "display": "Allen, Joan"
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/affiliate-physician-type",
            "valueString": "postop"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-employment-status",
            "valueString": "full time"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-note",
            "valueString": "note text"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-location",
            "valueReference": {
                "reference": "location/1",
                "display": "NexTech Dermatology"
            }
        },
		{
			"url": "https://select.nextech-api.com/api/structuredefinition/patients-referred",
			"valueInteger": 2
		},
		{
			"url": "https://select.nextech-api.com/api/structuredefinition/prospects-referred",
			"valueInteger": 1
		},
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-status",
            "valueString": "prospect"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/exclude-from-mailings",
            "valueBoolean": true
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-type",
            "valueReference": {
                "reference": "patient-type/2",
                "display": "Insurance Patient"
            }
        }
    ],
    "identifier": [
        {
            "use": "official",
            "value": "45bb641e-44c5-49a8-a36f-9dd7a0a50828"
        },
        {
            "use": "usual",
            "value": "112711"
        },
		{
            "system": "http://hl7.org/fhir/sid/us-ssn",
            "value": "###-##-1234"
        }
    ],
    "name": [
        {
            "use": "official",
            "text": "Mr. Gregory Brinkley Jr.",
            "family": "Brinkley",
            "given": [
                "Gregory",
                ""
            ],
            "prefix": [
                "Mr."
            ],
            "suffix": [
                "Jr."
            ]
        },
        {
            "use": "nickname",
            "text": "Greg",
            "given": [
                "Greg"
            ]
        }
    ],
    "telecom": [
		{
			"system": "email",
			"value": "test@abc.com"
		},
		{
			"system": "phone",
			"value": "(813) 555-5555",
			"use": "home",
			"rank": 1
		},
		{
			"system": "phone",
			"value": "(813) 555-5555",
			"use": "work"
		},
		{
			"system": "other",
			"value": "(813) 555-5555"
		},
		{
			"system": "fax",
			"value": "(813) 555-5555"
		},
        {
            "extension": [
                {
                    "url": "https://select.nextech-api.com/api/structuredefinition/method-privacy",
                    "valueBoolean": true
                }
            ],
            "system": "sms"
        }
    ],
    "gender": "male",
    "birthDate": "1970-09-28",
    "address": [
        {
            "use": "home",
            "type": "both",
            "line": [
                "9801 Jetson Ave",
                "Apt A"
            ],
            "city": "Hyattsville",
            "state": "MD",
            "postalCode": "20787",
            "country": "USA"
        }
    ],
    "maritalStatus": {
        "coding": [
            {
                "system": "http://hl7.org/fhir/ValueSet/marital-status",
                "code": "M"
            }
        ],
        "text": "Married"
    },
    "contact": [
        {
            "extension": [
                {
                    "url": "https://select.nextech-api.com/api/structuredefinition/emergency-contact-relation",
                    "valueString": "Wife"
                }
            ],
            "relationship": [
                {
                    "coding": [
                        {
                            "system": "http://hl7.org/fhir/v2/0131",
                            "code": "C"
                        }
                    ]
                }
            ],
            "name": {
                "text": "Jane Smith",
                "family": "Smith",
                "given": [
                    "Jane"
                ]
            },
            "telecom": [
                {
                    "system": "phone",
                    "value": "(999)888-9999",
                    "use": "home"
                },
                {
                    "system": "phone",
                    "value": "(111)222-3333",
                    "use": "work"
                }
            ]
        },
        {
            "extension": [
                {
                    "url": "https://select.nextech-api.com/api/structuredefinition/patient-occupation",
                    "valueString": "Principal"
                },
                {
                    "url": "https://select.nextech-api.com/api/structuredefinition/patient-company",
                    "valueString": "Elementary School"
                },
                {
                    "url": "https://select.nextech-api.com/api/structuredefinition/patient-occupation-code",
                    "valueString": "0230"
                },
                {
                    "url": "https://select.nextech-api.com/api/structuredefinition/patient-industry-code",
                    "valueString": "7890"
                }
            ],
            "relationship": [
                {
                    "coding": [
                        {
                            "system": "http://hl7.org/fhir/v2/0131",
                            "code": "E"
                        }
                    ]
                }
            ],
            "name": {
                "text": "Grace G Johnson",
                "family": "Johnson",
                "given": [
                    "Grace",
                    "G"
                ]
            },
            "address": {
                "use": "work",
                "type": "both",
                "line": [
                    "9821 James Ave"
                ],
                "city": "Schenectady",
                "state": "NY",
                "postalCode": "12345"
            }
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
    ],
    "generalPractitioner": [
        {
            "reference": "practitioner/9219",
            "display": "Jones, Robert"
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
In the above example this is the **home** contact.
### *Search*
Searches for all patients matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /Patient?{parameters}`

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

_At least one query parameter is required to perform a search._

### HTTP Request 
`GET /Patient/ID?{parameters}` 

### Parameters
| Name | Located in | Description | Required | Type | Initial Version |
| ---- | ---------- | ----------- | -------- | ---- | --------------- |
| _lastUpdated | query | The date the patient was last modified formatted as yyyy-MM-dd. As of version 14.3, we also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] . Note that the + character must be URL encoded. (i.e. `%2B`) | No | dateTime | _12.8_ |
| family | query | The family (last) name of the patient | No | string | _12.6_ |
| given | query | The given (first) name of the patient | No | string | _12.6_ |
| birthdate | query | The patient's date of birth formatted as YYYY-MM-DD | No | dateTime | _12.6_ |
| phone | query | The patient's phone number which will be matched against any phone number (home, cell, etc.) | No | string | _12.6_ |
| email | query | The patient's email address | No | string | _12.6_ |
| address-city | query | The city of the patient's address | No | string | _12.6_ |
| address-state | query | The state of the patient's address | No | string | _12.6_ |
| address-postalcode | query | The postal (zip) code of the patient's address | No | string | _12.6_ |
| identifier | query | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | No | string | _12.6_ |

#### Example: Get the unique identifier of a patient given first name, last name, and birthdate

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ID?family=Smith&given=John&birthdate=eq1972-04-21
</pre>
&nbsp;

### *Create Patient*
Create a patient.

#### HTTP Request 
`POST /Patient/` 


#### Parameters
| Name | Description | Notes | Required | Initial Version |
| ---- | ----------- | ----- | -------- | --------------- |
|identifier| Social Security number of the patient. | Social Security Number is not returned in the response until version 14.1 when it is returned masked. | No | _12.9.20_ |
| name | Names of the patient. | The family, given and use elements, are required.<br> Only one use of "official" is supported and one use of "nickname" is supported | Yes | _12.9.20_  |
| telecom | Contact details for the patient. | E-mail, and one phone contact is required.<br> One each of home, work, mobile, other, fax, email address is supported.<br> Preferred Contact is designated by setting a rank of 1 on a contact point.<br> Privacy fields are designated by having an extension of method-privacy set to true. You may set Text messaging privacy and preferred contact by using SMS as a system without a value.<br> When a contact detail is set to privacy, it is not returned in the response. | Yes | _12.9.20_  |
| gender | The gender of the patient | - | No | _12.9.20_  |
| birthDate | The date of birth of the patient | - | Yes | _12.9.20_  |
| address | Address associated with the patient.  |  Postal code is required. Only one address is currently supported.  For country, only an ISO-3166 3 character code is supported. | Yes | _12.9.20_ |
| communication | A list of Languages which may be used to communicate with the patient about his or her health | - | No | _12.9.20_  |
| maritalStatus | The marital status of the patient. | A code of 'M' (married) maps to Married status in Nextech, 'U' (unmarried) and 'S' (never married) map to Single in Nextech, all others map to Other in Nextech. | No | _12.9.20_ |
| contact | The emergency contact and/or employer for the patient. | Only a relationship code of C for emergency contact or E for employer is supported. | No | _12.9.20_ |
| generalPractitioner | The practitioner at this office who is responsible for the patient | Only one generalPractitioner is currently supported. | No | _12.9.20_ |
| race | The race of the patient | - | No | _12.9.20_  |
| ethnicity | The ethnicity of the patient | - | No | _12.9.20_ |
| patient-note | The text of the General 1 note for the patient | - | No | _12.9.20_ |
| referral-source | The primary referral source for the patient | - | No | _12.9.20_ |
| referring-physician | The referring physician for the patient | - | No | _12.9.20_ |
| referring-patient | The unique identifier for the referring patient for the patient | - | No | _12.9.20_ |
| primary-care-physician | The primary care physician for the patient | - | No | _12.9.20_ |
| affiliate-physician | The affiliate physician for the patient | - | No | _12.9.20_ |
| affiliate-physician-type | The affiliate physician type for the patient. | Must be a value of: "preop", "postop", "preandpostop" | No | _12.9.20_ |
| patient-location | The default location for the patient. | Must be an active, managed location of General type. | No | _12.9.20_ |
| patient-employment-status | The employment status for the patient. | Must be a value of: "full time","part time", "full time student", "part time student", "retired", "other"  | No | _12.9.20_ |
| patient-status | The status for the new record. | Must be a value of: "patient","prospect", "patientprospect"  | No | _14.1_ |
| patient-type | The patient type for the patient. | - | No | _14.1_ |
| exclude-from-mailings | Whether to exclude the patient from mailings. | Must be true or false | No | _14.1_ |


Prior to version 14.1, whether the patient is created as a patient, or a prospect is controlled by the Default Status preference in Nextech found under Tools->Preferences->Patients Module->New Patients->Default Status Preference.  As of version 14.1 the patient status may be specified in the patient-status extension.  If not specified, the preference is used.

Before creating a patient, the system will check the required fields (first, last, email address, birthdate, zip code, and one of home, work, or mobile phone numbers, to see if they match existing patients.  If a match is found, the patient will not be created and a 409 Conflict with a message indicating the patient already exists.

#### Example: Create a new patient with minimum information
<pre class="center-column">
{
  "resourceType": "Patient",
	"name": [
		{
			"use": "official",
			"family": "Brimley",
			"given": [
				"Henry"
			]
		}
	],
	"telecom": [
		{
			"system": "phone",
			"value": "(518)929-8978",
			"use": "home"
		},
		{
			"system": "email",
			"value": "test@test.com"
		}
	],
	"birthDate": "1970-09-28",
	"address": [
		{	"use": "home",
			"postalCode": "20787"
		}
	]
}
</pre>
&nbsp;  
 
#### Example: Create a new patient with all currently supported options

<pre class="center-column">
{
  "resourceType": "Patient",    
    "extension": [
        {
            "url": "http://hl7.org/fhir/v3/Race",
            "valueCodeableConcept": {
                "coding": [
                    {
                        "system": "http://hl7.org/fhir/v3/Race",
                        "code": "2106-3"
                    }
                ]
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
                ]                
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/referral-source",
            "valueReference": {
                "reference": "referral-source/9238"                
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/referring-physician",
            "valueReference": {
                "reference": "referring-physician/23"              
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/primary-care-physician",
            "valueReference": {
                "reference": "primary-care-physician/123"
            }
        },
        
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/referring-patient",
            "valueReference": {
                "reference": "patient/F4B46423-0071-4127-BD44-231419FE980F"
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-location",
            "valueReference": {
                "reference": "location/1"
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-note",
            "valueString": "note text"
        },
		{
            "url": "https://select.nextech-api.com/api/structuredefinition/affiliate-physician",
            "valueReference": {
                "reference": "affiliate-physician/62345"
            }
        },
		{
            "url": "https://select.nextech-api.com/api/structuredefinition/affiliate-physician-type",
            "valueString": "postop"
        },
		{
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-employment-status",
            "valueString": "full time student"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-status",
            "valueString": "prospect"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/exclude-from-mailings",
            "valueBoolean": true
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-type",
            "valueReference": {
                "reference": "patient-type/2"                
            }
        }
    ],  
    "name": [
        {            
            "family": "Brinkley",
            "use":"official",
            "given": [
                "Gregory"
            ],
            "prefix" : [
            	"Mr."
            ],
            "suffix" : [
            	"Jr."
            ]
        	
        },
		{           
            "use" : "nickname",
            "given": [
                "Greg"
            ]           
        }
    ],
    "telecom": [
        {
            "system": "phone",
            "value": "(311)211-8888",
            "use": "home",
            "extension": [
			{
				"url": "https://select.nextech-api.com/api/structuredefinition/method-privacy",
				"valueBoolean": "true"
			}
			]
        },
        {
            "system": "phone",
            "value": "(411)941-0786",
            "use": "mobile",
			"rank": "1"
        },
		{
            "system": "phone",
            "value": "(111)332-1232",
			"use" : "work"
        },
        {
            "system": "email",
            "value": "abcde@test.com"
        },
		{
            "system": "other",
            "value": "(555)234-1233"            
        },
		{
            "system": "fax",
            "value": "(111)332-1232"           
        },
		{
            "system": "sms",
			"extension": [
			{
				"url": "https://select.nextech-api.com/api/structuredefinition/method-privacy",
				"valueBoolean": "true"
			}			
			]			
        }
    ],
    "identifier": [
          {
            "type": {
              "coding": [
                {
                  "system": "http://hl7.org/fhir/v2/0203",
                  "code": "SS"
                }
              ]
            },
            "system": "http://hl7.org/fhir/sid/us-ssn",
            "value": "123456789"
          }
        ],
    "gender": "male",
    "maritalstatus": {
                "coding": [
                    {
                        "system": "http://hl7.org/fhir/ValueSet/marital-status",
                        "code": "M"
                    }
                ],
                "text": "Married"
            },
    "generalPractitioner" : {
        "reference": "practitioner/9219"
    }, 
    "birthDate": "1970-09-28",
    "address": [
        {
            "use": "home",
            "type": "both",
            "line": [
                "9801 Jetson Ave",
                "Apt A"
            ],
            "city": "Hyattsville",
            "state": "MD",
            "postalCode": "20787",
            "country":"USA"
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
                ]
            },
            "preferred": true
        }
    ],
    "contact": [
		{
        "relationship": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/v2/0131",
              "code": "C"
            }
          ]
        }
      ],
        "name": [
            {
				"text": "Sally Smith",
				"family": "Smith",
				"given": [
					"Sally"
				]
            }
         ],
         "telecom": [
            {
                "system": "phone",
                "value": "(999)888-9999",
                "use": "home"
            },
            {
                "system": "phone",
                "value": "(111)222-3333",
                "use": "work"
            }
        ],
        "extension":
        [
            {
				"url": "https://select.nextech-api.com/api/structuredefinition/emergency-contact-relation",
				"valueString": "Wife"
            }
        ]
         
    },
	{
        "relationship": [
        {
          "coding": [
            {
              "system": "http://hl7.org/fhir/v2/0131",
              "code": "E"
            }
          ]
        }
      ],
        "name": [
            {            
            "family": "Jenkins",
				"given": [
					"George",
					"G"
				]
            }
         ],
		 "address": [
          {
            "use": "work",
            "type": "both",
            "line": [
                "9821 James Ave"
            ],
            "city": "Schenectady",
            "state": "NY",
            "postalCode": "12345"
		  }
		],         
        "extension":
        [
            {
				"url": "https://select.nextech-api.com/api/structuredefinition/patient-occupation",
				"valueString": "Teacher"
            },
			{
				"url": "https://select.nextech-api.com/api/structuredefinition/patient-company",
				"valueString": "Williams High School"
            },
			{
				"url": "https://select.nextech-api.com/api/structuredefinition/patient-occupation-code",
				"valueString": "0230"
            },
			{
				"url": "https://select.nextech-api.com/api/structuredefinition/patient-industry-code",
				"valueString": "7890"
            }
        ]
         
    }
	]
}
</pre>
&nbsp; 

### *Update Patient*
Update a patient.

#### HTTP Request 
`PUT /Patient/` 

#### Parameters
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
|FHIR Patient object| The full patient FHIR object is accepted in the body. | Yes | _14.0_ |

All patient related fields can be updated, except for the below exceptions. If a field is updated with an invalid value (e.g. updating the country with a country code of JGU) the result of the update will be a success but the field will not be updated.

Field Update Exceptions:
* Patient Name cannot be updated and will be ignored.
* Date of Birth cannot be updated and will be ignored.
* Postal Code cannot be updated prior to version 14.1.  On version 14.1 and after postal code can be updated, but it cannot be cleared.
* Social Security Number cannot be updated prior to version 14.1.  On version 14.1 and after social security number can be changed, but it cannot be cleared.
* Patients Referred cannot be updated.
* Prospects Referred cannot be updated.
* Preferred Contact method can be updated but not cleared out.

For identifier fields, a use type is required.  A use type of "official" must be used when including the patient's unique identifier. A use type of "usual" must be used when including the patient's chart number.

#### Example: Update a patient's home number

<pre class="center-column">
{
    "resourceType": "Patient",    
    "identifier": [
        {
            "use": "official",
            "value": "f4a46423-0071-4127-bd34-231419fe970f"
        }
    ],
    "telecom": [
        {
            "system": "phone",
            "value": "(813) 217-4571",
            "use": "home"
        }
    ]
}
</pre>
&nbsp; 

### Remarks
* The generalPractitioner field will not be returned if the provider is not listed in the Practitioner resource. A provider is not returned as a Practitioner unless their Contacts module record has the Linked User setting configured.
    * Prior to version 14.1, Practitioners could be returned more than once if multiple users are assigned to use the same provider in their Contacts module User properties. This would cause patients to be duplicated if their generalPractitioner is returned multiple times in the Practitioner resource.

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
GET https://nxpartnerapi-dev.azurewebsites.net/api/r4/Patient/b664fd37-ff5f-4022-9d71-2e476d42f316/AllergyIntolerance?date=ge2022-01-01
</pre>
<pre class="center-column">
GET https://nxpartnerapi-dev.azurewebsites.net/api/r4/AllergyIntolerance?patient=b664fd37-ff5f-4022-9d71-2e476d42f316
</pre>
<pre class="center-column">
GET https://nxpartnerapi-dev.azurewebsites.net/api/r4/AllergyIntolerance?patient=Patient/b664fd37-ff5f-4022-9d71-2e476d42f316
</pre>
<pre class="center-column">
POST https://nxpartnerapi-dev.azurewebsites.net/api/r4/AllergyIntolerance/_search
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
GET https://nxpartnerapi-dev.azurewebsites.net/api/r4/AllergyIntolerance/21
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
| identifier | The unique value assigned to each immunization which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| status | Either completed or entered in error | [Immunization status Code](https://www.hl7.org/fhir/valueset-immunization-status.html) | _12.6_ |
| vaccineCode | Vaccine product adminstered | [Vaccine administered value set](https://www.hl7.org/fhir/valueset-vaccine-code.html) | _12.6_ |
| patient | The immunized patient | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| date | The vaccination administration date in the form YYYY-MM-DD | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |

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
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The immunization administration date in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all immunizations for a single patient as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Immunization?date=ge2017-01-01
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
