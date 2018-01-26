# Appointment

## Appointment

### Overview

The appointment resource contains information about a planned meeting between a patient and medical provider. Examples include new patient encounters, scheduled surgeries and and follow-up visits.

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each appointment which discerns it from all others | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.6_ |
| status | Indicates whether the appointment is cancelled, booked (confirmed), pending, arrived, fulfilled or no show | [AppointmentStatus](https://www.hl7.org/fhir/valueset-appointmentstatus.html) | _12.6_ |
| description | The appointment summary that includes the type and a list of purposes and resources | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.6_ |
| start | The date and time the appointment begins | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | _12.6_ |
| end | The date and time the appointment ends | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | _12.6_ |
| comment | The appointment notes | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.6_ |
| participant | The collection of appointment participants which includes patient, provider and location. Each element in the collection references an embedded resource found in the “contained” collection field | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | _12.6_ |
| created | The date that this appointment was initially created | [dateTime](https://www.hl7.org/fhir/datatypes.html#datetime) | _12.8_ |
| Extension | This is an extension of the class to provide more indepth objects like for appointment Types |  [extension](https://www.hl7.org/fhir/extensibility.html)  | _12.8_ |

### Sample
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
        "resourceType": "Appointment",
        "id": "12312",
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
              "reference": "#5",
              "display": "South Dermatology"
            }
          },
          {
            "actor": {
              "reference": "#2",
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
| _lastUpdated | query | The date the appointment was last modified formatted as YYYY-MM-DD | No | _12.8_ |
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
| commit | body | The object representing the changes to be made | Yes | _12.6_ |

The commit parameter should be in the form of an Appointment status field. See [https://www.hl7.org/fhir/http.html#update](https://www.hl7.org/fhir/http.html#update) for details on formatting PUT requests in RESTful API’s.

#### Example: Mark appointment 5453 as booked

<pre class="center-column">
PUT https://select.nextech-api.com/api/Appointment/5453
</pre>
<pre class="center-column">
{ "status": "booked" }
</pre>
&nbsp;
