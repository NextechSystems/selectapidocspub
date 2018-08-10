# Patient

## Patient

### Overview
The patient resource contains information about the demographics of a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each patient which discerns them from all others. It can be the patient's unique identifier or the patient's Nextech chart number | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
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
| referring-patient | The unique identifier for the referring patient for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| primary-care-physician | The primary care physician for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| patient-location | The default location for patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| affiliate-physician | The affiliate physician for the patient, contained in the extension | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| affiliate-physician-type | The affiliate physician type for the patient, contained in the extension | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.9.20_ |
| patient-employment-status | The employment status for the patient, contained in the extension | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.9.20_ |


### Example
<pre class="center-column">
{
    "resourceType": "Patient",
    "id": "45bb641e-44c5-49a8-a36f-9dd7a0a50828",
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
            "value": "abcde@test.com"
        },
        {
            "system": "phone",
            "value": "(411)941-0786",
            "use": "mobile",
            "rank": 1
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

### *Search*
Searches for all patients matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /Patient?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Type | Initial Version |
| ---- | ---------- | ----------- | -------- | ---- | --------------- |
| _lastUpdated | query | The date the patient was last modified formatted as YYYY-MM-DD | No | dateTime | _12.8_ |
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

_At least one of query parameters is required to perform a search._

### HTTP Request 
`GET /Patient/ID?{parameters}` 

### Parameters
| Name | Located in | Description | Required | Type | Initial Version |
| ---- | ---------- | ----------- | -------- | ---- | --------------- |
| _lastUpdated | query | The date the patient was last modified formatted as YYYY-MM-DD | No | dateTime | _12.8_ |
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
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
|identifier| Social Security number of the patient. Note: Social Security Number is not returned in the response. | No | _12.9.20_ |
| name | Names of the patient, use element must be included.  Only one use of "official" is supported and one use of "nickname" is supported | First and last name are required | _12.9.20_  |
| telecom | Contact details for the patient, one each of home, work, mobile, other, fax, email address is supported. Preferred Contact is designated by setting a rank of 1 on a contact point.  Privacy fields are designated by having an extension of method-privacy set to true.  You may set Text messaging privacy and preferred contact by using SMS as a system without a value. Note: when a contact detail is set to privacy, it is not returned in the response. | One of home, work, or mobile phone are required as well as an email address | _12.9.20_  |
| gender | The gender of the patient | No | _12.9.20_  |
| birthDate | The date of birth of the patient | Yes | _12.9.20_  |
| address | Address associated with the patient, only one address is currently supported.  For country, only an ISO-3166 3 character code is supported | Postal Code is required | _12.6_ |
| communication | A list of Languages which may be used to communicate with the patient about his or her health | No | _12.9.20_  |
| maritalStatus | The marital status of the patient, a code of 'M' (married) maps to Married status in Nextech, 'U' (unmarried) and 'S' (never married) map to Single in Nextech, all others map to Other in Nextech | No | _12.9.20_ | 
| contact | The emergency contact and/or employer for the patient, only a relationship code of C for emergency contact or E for employer is supported | No | _12.9.20_ |
| generalPractitioner | The practitioner at this office who is responsible for the patient, only one generalPractitioner is currently supported | No | _12.9.20_ |
| race | The race of the patient | No | _12.9.20_  |
| ethnicity | The ethnicity of the patient | No | _12.9.20_ |
| patient-note | The text of the General 1 note for the patient | No | _12.9.20_ |
| referral-source | The primary referral source for the patient | No | _12.9.20_ |
| referring-physician | The referring physician for the patient | No | _12.9.20_ |
| referring-patient | The unique identifier for the referring patient for the patient | No | _12.9.20_ |
| primary-care-physician | The primary care physician for the patient | No | _12.9.20_ |
| affiliate-physician | The affiliate physician for the patient | No | _12.9.20_ |
| affiliate-physician-type | The affiliate physician type for the patient. Must be a value of: "preop", "postop", "preandpostop" | No | _12.9.20_ |
| patient-location | The default location for patient, must be an active, managed location of General type. | No | _12.9.20_ |
| patient-employment-status | The employment status for patient. Must be a value of: "full time","part time", "full time student", "part time student", "retired", "other" | No | _12.9.20_ |


Whether the patient is created as a patient, or a prospect is controlled by the Default Status preference in Nextech found under Tools->Preferences->Patients Module->New Patients->Default Status Preference.

Before creating a patient, the system will check the required fields (first, last, email address, birthdate, zip code, and one of home, work, or mobile phone numbers, to see if they match existing patients.  If a match is found, the patient will not be created and a 409 Conflict with a message indicating the patient already exists.

#### Example: Create a new patient with minimum information
<pre class="center-column">
{
  "resourceType": "Patient",	
	"name": [
		{			
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
                "reference": "referring-physician/23",              
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
              "system": "http://hl7.org/fhir/patient-contact-relationship",
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
            ],
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
            },
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
              "system": "http://hl7.org/fhir/patient-contact-relationship",
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
            ],
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

*Note: 
* Patient name, date of birth and postal code cannot be updated. The fields will be ignored when updating the patient.
* All other patient related fields can be updated. However, if they are updated with invalid values (e.g. updating the country with a country code of JGU) the result of the update will be a success but the field will not be updated.

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

## Allergy Intolerance

### Overview
The allergy intolerance resource describes the risk of undesirable responses of exposure to a substance.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each allergy intolerance record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| clinicalStatus | Describes whether the allergy or intolerance is active, inactive or resolved | [AllergyIntoleranceStatus](https://www.hl7.org/fhir/valueset-allergy-clinical-status.html) | _12.6_ |
| code | The clinical code that identifies the allergy or intolerance | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.6_ |
| patient | The patient who the allergy or intolerance is for | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| assertedDate | The date the record was believed to be accurate | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |

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
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The date the record was believed accurate in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all allergies for a single patient that were believed to be accurate as of 1/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/AllergyIntolerance?date=ge2017-01-01
</pre>
&nbsp;


## Binary

### Overview
Binary resources contain patient health information in a structured document or media form.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ---------- | ----- | --------------- |
| contentType | MimeType of the binary content | [MimeType](http://www.rfc-editor.org/bcp/bcp13.txt) | _12.6_ |
| content | The document content | [base64Binary](https://www.hl7.org/fhir/datatypes.html#base64Binary) | _12.6_ |

### *Generate CCDA*
Generates a CCDA for a single patient

#### HTTP Request 
`GET /Patient/{patientUid}/Binary/$autogen-ccd-if?{parameters}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| start | query | The start date in the form YYYY-MM-DD for which the CCD should be generated (if not specified then all records starting with the patient's first visit are included) | No | _12.6_ |
| end | query | The end date in the form YYYY-MM-DD for which the CCD should be generated (if not specified then all records through the patient's latest visit are included) | No | _12.6_ |

#### Example: Get all CCDA's for a single patient corresponding to visits in 2007

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/Binary/$autogen-ccd-if?start=2017-01-01&end=2018-01-01
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


## Clinical Impression

### Overview
The clinical impression resource contains information regarding what problem(s) may affect the patient by treatment.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each clinical impression record which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| subject | The patient pertaining to the clinical impression | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| date | When the assessment was documented | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |
| summary | Summary of the assessment | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.6_ |

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
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| date | query | The collection of visit date filters | No | _12.6_ |

#### Example: Get all clinical impressions for a single patient charted on a visit on 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/ClinicalImpression?date=eq2017-05-01
</pre>
&nbsp;


## Composition

### Overview
The Composition resource defines a collection of healthcare-related information bundled together as a single document that provides meaning for a given patient. 

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique identifier assigned to each composition | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.7_ |
| extension | See [flag-priority](http://hl7.org/fhir/StructureDefinition/flag-priority) extension | [CodableConcept](http://hl7.org/fhir/datatypes.html#CodeableConcept) | _12.7_ |
| subject | The patient pertaining to the composition | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.7_ |
| date | The date of the composition (in UTC) | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.7_ |
| author | Identifies who is responsible for the information in the composition | [Reference(Practitioner)](https://www.hl7.org/fhir/references.html#Reference) | _12.7_ |
| section.title | The name of the Nextech note category | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.7_ |
| section.text | The contents of the composition | [Narrative](https://www.hl7.org/fhir/narrative.html) | _12.7_ |

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

#### HTTP Request 
`POST /Patient/{patientUid}/Composition` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.7_ |
| composition | body | Represents the `Composition` resource to create for the given patient | Yes | _12.7_ |

#### Body Fields
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| resourceType | Must be `Composition` | Yes | _12.7_ |
| extension | Must use `http://hl7.org/fhir/StructureDefinition/flag-priority` extension to specify the priority of the composition. See example below for specific format. Default priority code is `PL` | No | _12.7_ |
| date | The date (in UTC) of the composition. ie. `2017-10-16T20:32:28.9692476Z` | No | _12.7_ |
| author.display | The name of the author. This will be appended to the beginning of the `section.text.div` value. | No | _12.7_ |
| section.title | The name of the Nextech note category. This must match with an existing note category or is left blank. | No | _12.7_ |
| section.text.div | The non-clinical note associated with the subject. | No | _12.7_ |

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
| documentreference | body | Represents the `DocumentReference` resource to create for the given patient | Yes | _12.7_ |

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


## Medication Dispensement

### Overview
The medication dispersement resource describes the supply of medications by a health care provider to a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each dispensement which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| medicationCodeableConcept | The supplied medication | [SNOMED CT Medication Code](https://www.hl7.org/fhir/valueset-medication-codes.html) | _12.6_ |
| subject | The patient pertaining to the dispensement | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |
| whenPrepared | When product was packaged and reviewed | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |

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
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| whenPrepared | query | The preparation date in the form YYYY-MM-DD | No | _12.6_ |

#### Example: Get all prescriptions for a single patient prepared as of 5/1/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/MedicationDispense?whenPrepared=ge2017-05-01
</pre>
&nbsp;


## Medication Statements

### Overview
A medication statement resource describes a medication being consumed by a patient. This includes medications not prescribed by the health care provider. 

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each medication statement which discerns them from all others. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| status | The statement status | [MedicationStatementStatus](https://www.hl7.org/fhir/valueset-medication-statement-status.html) | _12.6_ |
| medication | The supplied medication | [SNOMED CT Medication Code](https://www.hl7.org/fhir/valueset-medication-codes.html) | _12.6_ |
| effective | The date/time when the medication was taken | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.6_ |
| subject | The patient pertaining to the medication statement | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.6_ |

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
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Yes | _12.6_ |
| effective | query | Date when patient was taking the medication in the form YYYY-MM-DD | No | _12.6_ |

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

## Payment Reconciliation

### Overview
The PaymentReconciliation resource is used in a POST command to post a single payment to an existing patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| requestProvider | The responsible practitioner | [Reference(Practitioner)](https://www.hl7.org/fhir/references.html#Reference) | _12.8_ |
| total | The payment amount | [Money](https://www.hl7.org/fhir/datatypes.html#Money) | _12.8_ |
| processNote | The payment description. If multiple processNotes are supplied, they will be joined together and separated by spaces. The description will be truncated to 255 characters. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| extension: location | The payment location reference | [Reference(Location)](https://www.hl7.org/fhir/references.html#Reference) | _12.8_ |
| extension: patient | The payment patient reference | [Reference(Patient)](https://www.hl7.org/fhir/references.html#Reference) | _12.8_ |
| extension: payment-method | The payment method. This may be one of the following values: Cash, Check, Charge | [string](https://www.hl7.org/fhir/datatypes.html#string)  | _12.8_ |
| extension: payment-date | The payment date (in UTC). This is a formatted date string in the form yyyy-MM-dd or yyyy-MM-ddTHH:mm:ss.fffZ  | [datetime](https://www.hl7.org/fhir/datatypes.html#datetime)  | _12.8_ |
| extension: effective-date | The payment input date (in UTC). This is a formatted date string in the form yyyy-MM-dd or yyyy-MM-ddTHH:mm:ss.fffZ  | [datetime](https://www.hl7.org/fhir/datatypes.html#datetime)  | _12.8_ |
| extension: deposited-date | The payment deposit date (in UTC). This is a formatted date string in the form yyyy-MM-dd or yyyy-MM-ddTHH:mm:ss.fffZ  | [datetime](https://www.hl7.org/fhir/datatypes.html#datetime)  | _12.8_ |
| extension: payment-category | The payment category. This must match an option in the Category dropdown of the Payment window in Nextech Practice | [string](https://www.hl7.org/fhir/datatypes.html#string)  | _12.8_ |
| extension: creditcard-type | The payment credit card type. This must match an option in the Credit Card dropdown of the Payment window in Nextech Practice | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| extension: check-number | The payment check number. The check number will be truncated to 50 characters. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |

### Example
<pre class="center-column">
{
    "resourceType": "PaymentReconciliation",
    "extension": [
        {
            "url": "http://hl7.org/fhir/StructureDefinition/Patient",
            "valueResourceReference": {
                "reference": "Patient/02c5a6ed-6c01-40a7-a065-a0be4732d6b9",
                "display": "Archer, Billy"
            }
        },
        {
            "url": "http://hl7.org/fhir/StructureDefinition/Location",
            "valueResourceReference": {
                "reference": "Location/1",
                "display": "NexTech Dermatology"
            }
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/payment-date",
            "valueDateTime": "2018-02-01T13:36:25.150Z"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/effective-date",
            "valueDateTime": "2018-02-02T05:00:00.000Z"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/deposited-date",
            "valueDateTime": "2018-02-08T05:00:00.000Z"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/payment-method",
            "valueString": "Charge"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/payment-category",
            "valueString": "PP - Patient Payment"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/creditcard-type",
            "valueString": "Visa"
        }
    ],
    "requestProvider": {
        "reference": "Practitioner/5",
        "display": "Davison, Darren"
    },
    "total": {
        "value": 200
    },
    "processNote": [
        {
            "type": {
                "coding": [
                    {
                        "system": "NoteType",
                        "code": "display"
                    }
                ]
            },
            "text": "Patient payment via check - Thank You"
        }
    ]
}
</pre>
&nbsp;

### *Create*
Creates a payment for an existing patient.

#### HTTP Request 
`POST /Patient/{patientUid}/PaymentReconciliation` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patientUid | path | The official patient identifier acquired from a patient search | Y | _12.8_ |
| paymentReconciliation | body | Represents the `PaymentReconciliation` resource to create for the given patient | Y | _12.8_ |

#### Body Fields
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| requestProvider | The responsible practitioner | Y | _12.8_ |
| total | The payment amount | Y | _12.8_ |
| processNote | The payment description | N | _12.8_ |
| extension: payment-method | The payment method. This may be one of the following values: Cash, Check, Charge | Y | _12.8_ |
| extension: payment-date | The payment date. This is a formatted date string in the form yyyy-MM-dd or yyyy-MM-ddTHH:mm:ss.fffZ  | Y |  _12.8_ |
| extension: effective-date | The payment input date. This is a formatted date string in the form yyyy-MM-dd or yyyy-MM-ddTHH:mm:ss.fffZ. This field defaults to the current date and time. | N | _12.8_ |
| extension: deposited-date | The payment deposit date. This is a formatted date string in the form yyyy-MM-dd or yyyy-MM-ddTHH:mm:ss.fffZ  | N | _12.8_ |
| extension: payment-category | The payment category. This must match an option in the Category dropdown of the Payment window in Nextech Practice | Y | _12.8_ |
| extension: credit-cardtype | The payment credit card type. This must match an option in the Credit Card dropdown of the Payment window in Nextech Practice | N | _12.8_ |
| extension: check-number | The payment check number | N | _12.8_ |
| extension: location | The payment location reference. The practice must have at least one Location resource with this identifier. | Y | _12.8_ |
| extension: apply-payment | Value indicating whether the payment should be applied to patient's responsibility. The payment will be applied to patient responsiblity charges with a balance from oldest to newest. | N | _12.8_ |

### Extensions
Extensions are used to support required values not part of the FHIR standard. 

#### Example: Post a $200 check for a patient
<pre class="center-column">
POST https://select.nextech-api.com/api/Patient/ad2085b5-b974-401d-bfcb-3b865109fd35/PaymentReconciliation
</pre>
&nbsp;
#### Body

<pre class="center-column">
{
  "resourceType": "PaymentReconciliation",
  "extension": [
    {
      "url": "https://select.nextech-api.com/api/structuredefinition/payment-date",
      "valueDate": {
        "value": "2018-01-02"
      }
    },
    {
      "url": "http://hl7.org/fhir/StructureDefinition/location",
      "valueReference": {
        "reference": "Location/1"
      }
    },
    {
      "url": "https://select.nextech-api.com/api/structuredefinition/effective-date",
      "valueDate": {
        "value": "2018-02-02"
      }
    },
    {
      "url": "https://select.nextech-api.com/api/structuredefinition/deposited-date",
      "valueDate": {
        "value": "2018-02-02"
      }
    },
    {
      "url": "https://select.nextech-api.com/api/structuredefinition/payment-method",
      "valueString": {
        "value": "Check"
      }
    },
    {
      "url": "https://select.nextech-api.com/api/structuredefinition/check-number",
      "valueString": {
        "value": "6751007623"
      }
    },
    {
      "url": "https://select.nextech-api.com/api/structuredefinition/payment-category",
      "valueString": {
        "value": "PP - Patient Payment"
      }
    },
    {
      "url": "https://select.nextech-api.com/api/structuredefinition/apply-payment",
      "valueBoolean": {
        "value": "true"
      }
    }
  ],
  "requestProvider": {
    "reference": "Practitioner/9219"
  },
  "total": {
    "value": 200
  },
  "processNote": [
    {
      "type": {
        "coding": [
          {
            "system": "NoteType",
            "code": "display"
          }
        ]
      },
      "text": "Patient payment via check - Thank You"
    }
  ]
}
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
