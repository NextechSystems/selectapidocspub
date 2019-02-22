# Slot

## Slot

### Overview

The slot resource contains information about available appointment slots. 

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| status | Indicates whether the slot is available. | [SlotStatus](https://www.hl7.org/fhir/slot-definitions.html#Slot.status) | 12.9 |
| schedule | The schedule that this slot belongs to | [Reference](https://www.hl7.org/fhir/references.html) | 12.9
| start | The date and time the slot begins | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | 12.9 |
| end | The date and time the slot ends | [instant](https://www.hl7.org/fhir/datatypes.html#instant) | 12.9|
| appointment-type extension | The Nextech appointment type of the slot | custom extension | 12.9 |
| appointment-purpose extension | The Nextech appointment purpose of the slot | custom extension | 12.9 |
| contained section | Contains the Location and Practitioner resources associated to the slot | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | 12.9.10 |



### Sample
<pre class="center-column">
{
  "resourceType": "Bundle",
  "entry": [
    {
      "resource": {
           "resourceType": "Slot",
		    "contained": [
                    {
                        "resourceType": "Location",
                        "id": "1",
                        "identifier": [
                            {
                                "use": "official",
                                "value": "1"
                            }
                        ],
                        "name": "NexTech Dermatology"
                    },
                    {
                        "resourceType": "Practitioner",
                        "id": "9323",
                        "identifier": [
                            {
                                "use": "official",
                                "value": "9323"
                            }
                        ],
                        "name": [
                            {
                                "text": "Walters, Sherri",
                                "family": "Walters",
                                "given": [
                                    "Sherri",
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
                       "reference": "appointment-purpose/224",
                       "display": "Skin Check"
                   }
               }
           ],
           "schedule": {
              "reference": "schedule/location_1_practitioner_9323"
           },
           "status": "free",
           "start": "2018-02-26T14:00:00-05:00",
           "end": "2018-02-26T15:00:00-05:00"
        }
     }  
  ]
}
</pre>
&nbsp;

### *Search*
Searches for all slots matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.  Only free slots are currently returned from the search.  A slot is returned for each practitioner/location combination.  

The number of days searched is determined by the start date parameters passed it.  If no less than operators are passed in, the search will default to 45 days.  The maximum number of days in the search criteria cannot exceed 60 days.

#### HTTP Request 
`GET /Slot?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| start | query | The slot start date/time. When searching for slots within a date range, the following prefixes may be used: lt, gt, eq, le, ge.  Note: the ne operator is not supported. | Yes | _<fill>_ |
| schedule.actor | query | The practitioners and/or locations of the slot you are searching for. At least one location actor is required.  If no practitioner actor is specified, all practitioners for the location specified will be searched.  A practitioner in practice is a schedule resource that is linked to a provider that is linked to a user in Nextech. | Yes | _<fill>_ |
|appointment-type | query | The appointment type the slot will be for.  | No if slot-length is specified | _<fill>_ |
|appointment-purpose | query | The appointment purpose the slot will be for.  | No | _<fill>_ |
|slot-length | query | The length of time the slot is needed for.  If not specified, default duration will be used | No, if appointment-type is specified | _<fill>_ |

#### Multiple Search Values
Multiple search values are supported for all fields except date.  To use multiple values, a comma should be placed in between the values you would like to search for.  This search results in the values being ORed together.  

If 2 practitioner schedule.actors are ORed together with a comma, any of those practitioners will be searched.  If they are ANDed together, all of the practitioners will be searched for, with a slot returned for each.   If you have both and AND and OR for practitioner scheduler.actors, they will all be ORed together.

#### Example: Get all available slots for consult type appointment in March 2018 at Pawtucket Plastic Surgery for any practitioner

<pre class="center-column">
GET https://select.nextech-api.com/api/slot?start=ge2018-03-01&start=lt2018-04-01&appointment-type=appointment-type/87&schedule.actor=location/5
</pre>
&nbsp;

#### Example: Get all available 15 minute slots for Dr. Smith at the West location in 2016

<pre class="center-column">
GET https://select.nextech-api.com/api/slot?start=ge2018-01-01&start=lt2019-01-01&schedule.actor=location/7&schedule.actor=practitioner/15&slot-length=15
</pre>
&nbsp;

#### Example: Get all 15 minute slots for Dr. Smith or Dr. Jones at the West location

<pre class="center-column">
GET https://select.nextech-api.com/api/slot?start=ge2018-01-01&start=lt2019-01-01&schedule.actor=location/7&schedule.actor=practitioner/15, practitioner/17&slot-length=15
</pre>
&nbsp;

### Remarks
* Slots will not be returned for appointment resources without a provider configured. In addition, slots will not be returned if the linked provider is not listed in the Practitioner API resource. A provider is not returned as a Practitioner unless their Contacts module record has the Linked User setting configured.
* Slots will not return for an appointment-type that has a default slot duration of 0 minutes, unless a slot-length > 0 is specified.
* This endpoint is to be used during the act of scheduling an appointment.
* This call is used to find available appointment times for one patient appointment, based on the desired appointment type, purpose, and provider.
* This endpoint should **not** be used to generically find all open times on the schedule for display purposes, or data syncing.