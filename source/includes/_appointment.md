# Appointment

## Appointment

### Overview

The appointment resource contains information about a planned meeting between a patient and medical provider. Examples include new patient encounters, scheduled surgeries and and follow-up visits.

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each appointment which discerns it from all others | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| status | Indicates whether the appointment is proposed (held), cancelled, booked (confirmed), pending, arrived, fulfilled or no show (this field is omitted if the appointment is in a status that doesn't correspond to any of the listed statuses) | [AppointmentStatus](https://www.hl7.org/fhir/valueset-appointmentstatus.html) | _12.6_ |
| description | The appointment summary that includes the type and a list of purposes and resources | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.6_ |
| start | The date and time the appointment begins | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | _12.6_ |
| end | The date and time the appointment ends | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | _12.6_ |
| comment | The appointment notes | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.6_ |
| participant | The collection of appointment participants which includes patient, provider and location.  As of version 14.1, the patient reference will not be included for non-patient appointments | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | _12.6_ |
| created | The date that this appointment was initially created | [dateTime](https://www.hl7.org/fhir/datatypes.html#datetime) | _12.8_ |
| Extension | This is an extension of the class to provide more indepth objects like for appointment types(_12.8_), appointment purposes (_12.9_), and Select appointment status (_15.9_) |  [extension](https://www.hl7.org/fhir/extensibility.html)  | _12.9_ |
| meta.lastUpdated | The last time the appointment was modified | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | _14.3_ |

### Sample
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Appointment",
        "id": "12312",
        "meta":
        {
          "lastUpdated": "2018-01-25T13:23:00.55+00:00"
        },
        "contained": [
          {
            "resourceType": "Location",
            "id": "5",
            "identifier": [
              {
                "use": "official",
                "value": "5"
              }
            ],
            "name": "South Dermatology"
          },
          {
            "resourceType": "Practitioner",
            "id": "2",
            "identifier": [
              {
                "use": "official",
                "value": "2"
              }
            ],
            "name": [
              {
                "text": "Davison, Darren",
                "family": "Davison",
                "given": [
                  "Darren",
                  ""
                ]
              }
            ]
          }
        ],
        "extension": [
	      {
            "url": "https://select.nextech-api.com/api/structuredefinition/appointment-status",
            "valueReference": {
              "reference": "appointment-status/0",
              "display": "Pending"
            }
          },
          {
            "url": "https://select.nextech-api.com/api/structuredefinition/appointment-type",
            "valueReference": {
              "reference": "appointment-type/9",
              "display": "Surgery Cosmetic"
            }
          },
          {
            "url": "https://select.nextech-api.com/api/structuredefinition/appointment-purpose",
            "valueReference": {
              "reference": "appointment-purpose/161",
              "display": "Chemical Peel/Skin Treatments"
            }
          }
        ],
        "identifier": [
          {
            "use": "official",
            "value": "12312"
          }
        ],
        "status": "booked",
        "description": "Consult - Insurance Est. - Skin Lesion/Tumor for Darren Davis, MD",
        "start": "2017-03-12T09:10:00-04:00",
        "end": "2017-03-12T09:40:00-04:00",
        "created": "2017-07-27T21:09:19.913Z",
        "comment": "This is a sample comment",
        "participant": [
          {
            "actor": {
              "reference": "Patient/4AAE9E3C-B1E4-46EA-93C2-CF3B36747D1A",
              "display": "Brimley, Henry"
            }
          },
          {
            "actor": {
              "reference": "Location/5",
              "display": "South Dermatology"
            }
          },
          {
            "actor": {
              "reference": "Practitioner/2",
              "display": "Davison, Darren"
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
Searches for all appointments matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /Appointment?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _lastUpdated | query | The date the appointment was last modified formatted as yyyy-MM-dd. As of version 14.3, we also support the format yyyy-MM-ddThh:mm:ss\[Z&#124;(+&#124;-)hh:mm\] . Note that the + character must be URL encoded. (i.e. `%2B`)  | No | _12.8_ |
| identifier | query | The unique identifier for a single appointment | No | _12.6_ |
| patient | query | The unique identifier acquired from the patient search or a patient chart number | No | _12.6_ |
| date | query | The appointment start date. When searching for appointments within a date range, the following prefixes may be used: lt, gt, eq, le, ge | No | _12.6_ |
| location.id | query | The id of the appointment's location | No | _12.7_ |
| location.name | query | The name of the appointment's location. | No | _12.7_ |
| practitioner.id | query | The id of the appointment's practitioner | No | _12.7_ |
| practitioner.name | query | The first or last name of the appointment's practitioner | No | _12.7_ |
| status | query | The status of the appointment.  Currently supported values are: cancelled, booked, noshow, arrived, fulfilled, and pending | No | _12.7_ |
| created | query | The date that this appointment was initially created | No | _12.8_ |

#### Multiple Search Values
Multiple search values are supported for all fields except date.  To use multiple values, a comma should be placed in between the values you would like to search for.  This search results in the values being ORed together.   

#### Example: Get all appointments for a patient by chart number

<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?patient=12345
</pre>
&nbsp;

#### Example: Get all appointments between and including 1/1/2017 through 5/31/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?date=ge2017-01-01&date=lt2017-06-01
</pre>
&nbsp;

#### Example: Get all appointments for Dr. Smith or Dr. Jones

<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?practitioner.name=smith,jones
</pre>
&nbsp;

#### Example: Get all appointments for a location by id

<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?location.id=1
</pre>
&nbsp;

#### Example: Get all appointments for either of 2 locations

<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?location.id=1,2
</pre>
&nbsp;

#### Example: Get all cancelled appointments

<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?status=cancelled
</pre>
&nbsp;

#### Example: Get all appointments created on 7/27/2017

<pre class="center-column">
GET https://select.nextech-api.com/api/Appointment?created=2017-07-27
</pre>
&nbsp;

### *Confirm Appointment*
Confirm a scheduled appointment.

#### HTTP Request 
`PUT /Appointment/{identifier}` 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | path | The unique identifier of the appointment to be updated | Yes | _12.6_ |
| appointment | body | The appointment object representing the changes to be made | Yes | _12.6_ |

The commit parameter should be in the form of an Appointment status field. See [https://www.hl7.org/fhir/http.html#update](https://www.hl7.org/fhir/http.html#update) for details on formatting PUT requests in RESTful API’s.

#### Example: Mark appointment 5453 as booked

<pre class="center-column">
PUT https://select.nextech-api.com/api/Appointment/5453
</pre>
<pre class="center-column">
{
	"resourceType": "Appointment",
	"status": "booked"
}
</pre>
&nbsp;

### *Update Appointment Status*
Updates the status of a given appointment

#### HTTP Request 
`PUT /Appointment/{identifier}` 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | path | The unique identifier of the appointment to be updated | Yes | _12.6_ |
| appointment | body | The appointment object representing the changes to be made | Yes | _12.6_ |
| appointment.status | body | The status to update the appointment to. As of 15.8 we'll now support "Booked", "Arrived", "Fulfilled" and "Pending" | Yes | _15.8_ |

The below FHIR statuses will be mapped to the below system level statuses in Select

<pre class="center-column">
"Pending" -> "Pending"
"Arrived" -> "In"
"Fulfilled" -> "Out"
</pre>

### Remarks
In a normal workflow an appointment would go from -> Pending -> Arrived -> Fulfilled. Once an appointment is moved from the Arrived status to any other status, you can no 
longer set the status back to arrived from the API. You'll need to manually set the status from within Select.

The commit parameter should be in the form of an Appointment status field. See [https://www.hl7.org/fhir/http.html#update](https://www.hl7.org/fhir/http.html#update) for details on formatting PUT requests in RESTful API’s.

#### Example: Mark appointment 5453 as arrived

<pre class="center-column">
PUT https://select.nextech-api.com/api/Appointment/5453
</pre>
<pre class="center-column">
{
	"resourceType": "Appointment",
	"status": "arrived"
}
</pre>
&nbsp;

### *Update Appointment With a Custom Status*
Updates the status of a given appointment with a custom status

#### HTTP Request 
`PUT /Appointment/{identifier}` 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | path | The unique identifier of the appointment to be updated | Yes | _12.6_ |
| appointment | body | The appointment object representing the changes to be made | Yes | _12.6_ |
| extension | body | An extension with the status (as defined in Select) to set the appointment to | Yes | _15.9_ |

#### Example: Set status of appointment 5453 to the status with ID 8

<pre class="center-column">
PUT https://select.nextech-api.com/api/Appointment/5453
</pre>
<pre class="center-column">
{
    "resourceType": "Appointment",
    "extension": [
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/appointment-status",
            "valueReference": {
                "reference": "appointment-status/8"
            }
        }
    ]
}
</pre>
&nbsp;

### *Request Appointment Cancellation*
Request a scheduled appointment to be cancelled.

#### HTTP Request 
`PUT /Appointment/{identifier}` 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | path | The unique identifier of the appointment to be updated | Yes | _14.6_ |
| appointment | body | The appointment object representing the appointment that is being requested to be cancelled | Yes | _14.6_ |

The commit parameter should be in the form of an Appointment status field of `cancelled` with a custom extension url of `https://select.nextech-api.com/api/structuredefinition/request-type` and value of `queue`. See [https://www.hl7.org/fhir/http.html#update](https://www.hl7.org/fhir/http.html#update) for details on formatting PUT requests in RESTful API’s.

#### Example: Request appointment 5453 to be cancelled

<pre class="center-column">
PUT https://select.nextech-api.com/api/Appointment/5453
</pre>
<pre class="center-column">
{
	"resourceType": "Appointment",
	"status": "cancelled",
	"extension": [
          {
				"url": "https://select.nextech-api.com/api/structuredefinition/request-type",
				"valueString": "queue"
          }
    ]
}
</pre>
&nbsp;

### *Cancel Appointment*
Cancels a scheduled appointment.

#### HTTP Request 
`PUT /Appointment/{identifier}` 


#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | path | The unique identifier of the appointment to be cancelled | Yes | _15.9_ |
| appointment | body | The appointment object representing the appointment to cancel | Yes | _15.9_ |

The commit parameter should be in the form of an Appointment status field of `cancelled` with **no custom extensions**. See [https://www.hl7.org/fhir/http.html#update](https://www.hl7.org/fhir/http.html#update) for details on formatting PUT requests in RESTful API’s.

#### Example: Cancel appointment 5453

<pre class="center-column">
PUT https://select.nextech-api.com/api/Appointment/5453
</pre>
<pre class="center-column">
{
	"resourceType": "Appointment",
	"status": "cancelled"
}
</pre>

### Remarks
* An appointment cancellation will fail for a number of reasons:
	* The appointment does not exist (HTTP Status Code: 404)
    * The appointment has already been cancelled (HTTP Status Code: 422)
    * A request to cancel the appointment has already been placed (HTTP Status Code: 422)
    * The appointment is tied to a room (HTTP Status Code: 422)
    * The appointment is tied to a patient photo (HTTP Status Code: 422)
    * The appointment is tied to a superbill (HTTP Status Code: 422)
    * The appointment is tied to an inventory allocation (HTTP Status Code: 422)
    * The appointment is linked to an order (HTTP Status Code: 422)
    * The appointment is tied to a case history (HTTP Status Code: 422)
    * The appointment is tied to a tracking procedure (HTTP Status Code: 422)
    * The appointment is not tied to a patient (HTTP Status Code: 422)
    * The appointment is linked to other appointments (HTTP Status Code: 422)
    * The appointment is associated with a tracking ladder event (HTTP Status Code: 422)
    * The practice has their `Require a cancellation reason` preference set to "Yes" (HTTP Status Code: 422)
&nbsp;

### *Book Appointment*
Create a scheduled appointment.

#### HTTP Request 
`POST /Appointment/` 


#### Parameters
| Name | Description | Type | Required | Initial Version |
| ---- | ----------- | ---- | -------- | --------------- |
| status | The current status of the appointment - must be proposed | [AppointmentStatus](https://www.hl7.org/fhir/valueset-appointmentstatus.html) | Yes | _12.9.10_ |
| start | The start time of the appointment ie.`2017-04-13T09:10:00-04:00` | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | Yes | _12.9.10_ |
| end | The end time of the appointment ie. `2017-04-13T09:40:00-04:00` | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | Yes | _12.9.10_ |
| Participant | Includes the patient reference (if existing patient), location for the appointment, and practitioner for the appointment  | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html)  | Location and practitioner are required, patient is required unless a contained section is included | _12.9.10_ |
| Extension | Contains the appointment type and appointment purposes for this appointment |  [extension](https://www.hl7.org/fhir/extensibility.html) | Yes, for version 16.2 and below, preference-based for 16.3+ (see * below) | _12.9.10_ |
| Contained | Contains a patient resource if the patient does not already exist in Nextech | [Patient Resource](https://www.hl7.org/fhir/patient.html)   | Yes, unless a patient reference is included in the participant section | _12.9.10_ |

When posting an appointment, there are multiple options to be considered:
The first set of options is whether this appointment should be booked or held.  A booked appointment is one which shows in the offices schedule as if the office created the appointment from inside Nextech.  A held appointment is an appointment which has a different flag in Nextech to indicate that it is held and also appears in a list of appointments for the office to follow up with.  In both situations the appointment shows on the office schedule in Nextech. 

Whether to book or hold an appointment is controlled by the appointment-schedule extension.  In order to hold an appointment, the extension would have "hold" as the value string.  To book an appointment, the extension would have "book" as the value string. If no appointment-schedule extension is sent, the office's preference for booking or holding is used.  See examples below.

The second set of options to choose from is whether the patient is existing, or if we are making an appointment for a unknown patient.
1. If you are scheduling an appointment for an existing patient, put the identifier for the patient in the participants section
2. If you are scheduling an appointment for a person that is not a patient, put the demographic information for the patient in the contained section.  When the appointment is scheduled, the demographic information in the contained section will be used to create a prospect that is then linked to the appointment.  The following information is required for the contained section:
   1. Name, given and family must be filled in
   2. At least one phone number, home, work, or cell as specified by the Use field in the telecom section
   3. An email address specified in the telecom section

Additional fields that can be sent and are recommended, but are not required are:   
   1. Birth Date
   2. Zip Code

*Prior to version 16.3, the `appointment-purpose` and `appointment-type` extension values are required in appointment creation requests. As of version 16.3, whether appointment types or appointment purposes are required is defined by the preferences in Nextech at `Tools->Preferences->Scheduler Module->Appts. 1->Appointments must have Purposes` and `Tools->Preferences->Scheduler Module->Appts. 1->Appointments must have Types`.

If the appointment creation succeeds, the appointment resource will be returned with a return status of Created (201).

If the appointment creation fails, an AppointmentResponse (https://www.hl7.org/fhir/appointmentresponse.html) resource will be returned with a status of Conflict (409).  The reason for why the creation failed will be included in the AppointmentResponse Comment field.  

If the appointment creation fails and a prospect was being created, the prospect will also be deleted.
   
#### Example: Create an appointment for an existing patient as a booked appointment

<pre class="center-column">
POST https://select.nextech-api.com/api/Appointment/
</pre>
<pre class="center-column">
{
	"resourceType": "Appointment",       
	"extension": [
	  {
		"url": "https://select.nextech-api.com/api/structuredefinition/appointment-type",
		"valueReference": {
			"reference": "appointment-type/25",
			"display": "Skin Care Established"
		}
	  },
	  {
		"url": "https://select.nextech-api.com/api/structuredefinition/appointment-purpose",
		"valueReference": {
		  "reference": "appointment-purpose/202",
		  "display": "Glycolic Peel"
		}
	  },
	  {
		"url": "https://select.nextech-api.com/api/structuredefinition/appointment-schedule",
		"valueString": "book"
	  }
	],		
	"status": "proposed",
	"start": "2017-04-13T09:10:00-04:00",
	"end": "2017-04-13T09:40:00-04:00",		
	"comment": "test note",
	"participant": [
	  {
		"actor": {
		  "reference": "patient/EEA9EC85-849E-4B88-9859-9F30CF309446",
		  "display": "Jane Smith"
		}
	  },
	  {
		"actor": {
		  "reference": "location/1",
		  "display": "Nextech Dermatology"
		}
	  },
	  {
		"actor": {
		  "reference": "practitioner/9323",
		  "display": "Walters, Sherri"
		}
	  }
	]
}
</pre>

#### Example: Create an appointment for a new prospect as a held appointment

<pre class="center-column">
POST https://select.nextech-api.com/api/Appointment/
</pre>
<pre class="center-column">
{
	"resourceType": "Appointment",       
	"extension": [
	  {
		"url": "https://select.nextech-api.com/api/structuredefinition/appointment-type",
		"valueReference": {
			"reference": "appointment-type/25",
			"display": "Skin Care Established"
		}
	  },
	  {
		"url": "https://select.nextech-api.com/api/structuredefinition/appointment-purpose",
		"valueReference": {
		  "reference": "appointment-purpose/202",
		  "display": "Glycolic Peel"
		}
	  },
	  {
		"url": "https://select.nextech-api.com/api/structuredefinition/appointment-schedule",
		"valueString": "hold"
	  }
	],		
	"status": "proposed",		
	"start": "2017-04-12T08:10:00-04:00",
	"end": "2017-04-12T08:40:00-04:00",		
	"comment": "test note",
	"participant": [
	  {
		"actor": {
		  "reference": "location/1",
		  "display": "Nextech Dermatology"
		}
	  },
	  {
		"actor": {
		  "reference": "practitioner/9323",
		  "display": "Walters, Sherri"
		}
	  }
	],
	"contained": [
		{
			"resourceType": "Patient",        		
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
			 "address": [
			 {
			   "use": "home",				      
			   "postalCode": "77014"
			 }
			 ],
			 "telecom": [
			 {
			   "system": "email",
			   "value": "jsmith@email.com"
			 },
			 {
			   "system": "phone",
			   "use" : "home",
			   "value": "346-555-3682"
			 }
			 ],
			   "birthDate": "1968-02-04",
		}
   ]
   
}
</pre>

#### Example: Create an appointment for a new prospect using the office's preference for booking or holding

<pre class="center-column">
POST https://select.nextech-api.com/api/Appointment/
</pre>
<pre class="center-column">
{
	"resourceType": "Appointment",       
	"extension": [
	  {
		"url": "https://select.nextech-api.com/api/structuredefinition/appointment-type",
		"valueReference": {
			"reference": "appointment-type/25",
			"display": "Skin Care Established"
		}
	  },
	  {
		"url": "https://select.nextech-api.com/api/structuredefinition/appointment-purpose",
		"valueReference": {
		  "reference": "appointment-purpose/202",
		  "display": "Glycolic Peel"
		}
	  }
	],		
	"status": "proposed",		
	"start": "2017-04-12T08:10:00-04:00",
	"end": "2017-04-12T08:40:00-04:00",		
	"comment": "test note",
	"participant": [
	  {
		"actor": {
		  "reference": "location/1",
		  "display": "Nextech Dermatology"
		}
	  },
	  {
		"actor": {
		  "reference": "practitioner/9323",
		  "display": "Walters, Sherri"
		}
	  }
	],
	"contained": [
		{
			"resourceType": "Patient",        		
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
			 "address": [
			 {
			   "use": "home",				      
			   "postalCode": "77014"
			 }
			 ],
			 "telecom": [
			 {
			   "system": "email",
			   "value": "jsmith@email.com"
			 },
			 {
			   "system": "phone",
			   "use" : "home",
			   "value": "346-555-3682"
			 }
			 ],
			   "birthDate": "1968-02-04",
		}
   ]
   
}
</pre>
&nbsp;

### Remarks
* If an appointment is returned without a practitioner in the participants section, please check the following:
	* Make sure the appointment's resource is linked to a provider in the Scheduler module's Resource Editor screen.
    * Make sure the provider that the appointment resource is linked to is listed in the Practitioner API resource. A provider is not returned as a Practitioner unless their Contacts module record has the Linked User setting configured.
