# Patient-Recall

## Patient-Recall

### Overview

The patient-recall resource contains information about when a patient is expected to return for an appointment with their provider.

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique value assigned to each recall which discerns it from all others | [identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _14.2_ |
| created | The date this recall was created in the system | [dateTime](https://www.hl7.org/fhir/datatypes.html#datetime) | _14.2_ |
| subject | A reference to the patient for whom this recall is for | [reference](https://www.hl7.org/fhir/references.html) | _14.2_ |
| extension:practitioner | A reference to the practitioner associated with this recall. Not included if there is no practitioner associated to the recall | [reference](https://www.hl7.org/fhir/references.html) | _14.2_ |
| extension:location | A reference to the location associated with this recall. Not included if there is no location associated to the recall | [reference](https://www.hl7.org/fhir/references.html) | _14.2_ |
| extension:recall-date | The recall date | [date](https://www.hl7.org/fhir/datatypes.html#date) | _14.2_ |
| extension:recall-status-name | The status of this recall. Possible values include: Need to Schedule, Past Due, Scheduled, Complete, Discontinued | [string](https://www.hl7.org/fhir/datatypes.html#string) | _14.2_ |
| extension:recall-appointment-date | The start time of the appointment that fulfills this recall, if exists | [dateTime](https://www.hl7.org/fhir/datatypes.html#datetime) | _14.2_ |
| extension:recall-template-name | The name of the recall template this recall is for |  [string](https://www.hl7.org/fhir/datatypes.html#string)  | _14.2_ |
| extension:recall-step-name | The name of the recall step this recall is for |  [string](https://www.hl7.org/fhir/datatypes.html#string)  | _14.2_ |
| extension:recall-deleted | Indicates if the recall has been deleted |  [string](https://www.hl7.org/fhir/datatypes.html#string)  | _14.4_ |

### Sample
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
	{
		"resource": {
		"resourceType": "patient-recall",        
		"identifier": [
		{
			"use": "official",
			"value": "12312"
		}
		],
		"created": "2017-07-27T21:09:19.913Z",
		"subject": {
			"reference": "Patient/5AAE9E3C-B1E4-46EA-93C2-CF3B36747D1A",
			"display": "Stephenson, Jim"
		},
		"extension" : [
		{
			"url" : "http://hl7.org/fhir/StructureDefinition/Practitioner",
			"valueResourceReference": {
				"reference": "Practitioner/9978",
				"display": "Davidson, Darren"
			}
		},
		{
			"url" : "http://hl7.org/fhir/StructureDefinition/Location",
			"valueResourceReference": {
				"reference": "Location/5",
				"display": "South Dermatology"
			}
		},
		{
			"url" : "https://select.nextech-api.com/api/structuredefinition/recall-date",
			"valueDate" : "2019-12-01"
		},
		{
			"url" : "https://select.nextech-api.com/api/structuredefinition/recall-status-name",		
			"valueString" : "Scheduled"
		},
		{
			"url" : "https://select.nextech-api.com/api/structuredefinition/recall-appointment-date",		
			"valueDateTime" : "2018-02-08T05:00:00.000Z"
		},
		{
			"url" : "https://select.nextech-api.com/api/structuredefinition/recall-template-name",		
			"valueString" : "Melanoma"
		},
		{
			"url" : "https://select.nextech-api.com/api/structuredefinition/recall-step-name",		
			"valueString" : "2 year follow-up"        
		},
		{
            "url": "https://select.nextech-api.com/api/structuredefinition/recall-deleted",
            "valueBoolean": false
        }
		]
		}
	}
  ]
}

</pre>
&nbsp;

### *Search*
Searches for all recalls matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /patient-recall?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query | The unique identifier for a single recall | No | _14.2_ |
| subject | query | The recall's patient reference | No | _14.2_ |
| created | query | The recall's created date. When searching for recalls within a date range, the following prefixes should be used: lt, gt, eq, le, ge | No | _14.2_ |
| location | query | The recall's location reference | No | _14.2_ |
| practitioner | query | The recall's practitioner reference | No | _14.2_ |
| recall-status-name | query | The status name of the recall.  Currently supported values are: Need to Schedule, Past Due, Scheduled, Complete, and Discontinued | No | _14.2_ |
| recall-date | query | The recall date | No | _14.2_ |
| deleted | query | The recall's deleted status | No | _14.4_ |

#### Multiple Search Values
Multiple search values are supported for all fields except dates.  To use multiple values, a comma should be placed in between the values you would like to search for.  This search results in the values being ORed together.   

#### Example: Get a specific recall based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall/55
</pre>
&nbsp;


#### Example: Get all recalls for a patient

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall?subject=Patient/5AAE9E3C-B1E4-46EA-93C2-CF3B36747D1A
</pre>
&nbsp;

#### Example: Get all recalls between and including 1/1/2019 through 5/31/2019

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall?recall-date=ge2019-01-01&recall-date=lt2019-06-01
</pre>
&nbsp;

#### Example: Get all recalls for Dr. Smith or Dr. Jones 

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall?practitioner=practitioner/9323,practitioner/7945
</pre>
&nbsp;

#### Example: Get all recalls for a location by id

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall?location=location/1
</pre>
&nbsp;

#### Example: Get all appointments for either of 2 locations

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall?location=location/1,location/2
</pre>
&nbsp;

#### Example: Get all completed recalls

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall?recall-status-name=complete
</pre>
&nbsp;

#### Example: Get all recalls  created on 7/27/2018

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall?created=eq2018-07-27
</pre>
&nbsp;