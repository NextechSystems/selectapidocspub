# Claim

## Claim

### Overview
A list of services and products provided, or to be provided, to a patient.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | Unique identifier used to reference the Claim. | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.9.20_ |
| name |The name associated with the Claim. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.9.20_ |
| status | Indicates whether the Bill or Quote is presently active or cancelled. If a Bill is deleted or voided it will have a status of Cancelled. If a closed bill is corrected, the original bill will be voided with a status of Cancelled and a new bill will be created to replace it with an Active status. | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9.20_ |
| total | The total value of the claim. | [Money](https://www.hl7.org/fhir/datatypes.html#Money) | _12.9.20_ |
| use | Complete (Bill ), Exploratory (Quote). | [Code](https://www.hl7.org/fhir/datatypes.html#code) | _12.9.20_ |
| billablePeriod | The billable period for which charges are being submitted. | [Period](https://www.hl7.org/fhir/datatypes.html#Period) | _12.9.20_ |
| created | The date when the enclosed suite of services were performed or completed. | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.9.20_ |
| patient | Identifies the patient the Claim is associated with. | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| facility | Place of service where the services were provided. | [Reference](https://www.hl7.org/fhir/references.html)  | _12.9.20_ |
| careTeam | The members of the team who provided the overall service. | [Reference](https://www.hl7.org/fhir/references.html) | _12.9.20_ |
| diagnosis| List of patient diagnosis for which care is sought. | [Control](https://www.hl7.org/fhir/conformance-rules.html#conformance) | _12.9.20_|
| diagnosis.sequence| Sequence of diagnosis. | [positiveInt](https://www.hl7.org/fhir/datatypes.html#positiveInt) | _12.9.20_|
| diagnosis.diagnosis| The diagnosis | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9.20_|
| item | First tier of goods and services. | [Control](https://www.hl7.org/fhir/conformance-rules.html#conformance) | _12.9.20_|
| item.careTeamLinkId| CareTeam applicable for this service or product line. | [positiveInt](https://www.hl7.org/fhir/datatypes.html#positiveInt) | _12.9.20_|
| item.service | Code to indicate the Professional Service or Product supplied. | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9.20_ |
| item.modifier | Item typification or modifiers codes | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9.20_ |
| item.serviced | The date or dates when the enclosed suite of services were performed or completed. | [date](https://www.hl7.org/fhir/datatypes.html#date) | _12.9.20_ |
| item.location | Place of service code. | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9.20_ |
| item.item.quantity | The number of repetitions of a service or product. | [SimpleQuantity](https://www.hl7.org/fhir/datatypes.html#SimpleQuantity) | _12.9.20_ |
| item.unitPrice | Fee for the product or service. | [Money](https://www.hl7.org/fhir/datatypes.html#Money) | _12.9.20_ |
| item.net | The quantity times the unit price for an additional service or product or charge. | [Money](https://www.hl7.org/fhir/datatypes.html#Money) | _12.9.20_ |

### Extensions
| Name | Description | Url  | Type | Initial Version |
| ---- | ----------- | ---  | ---- | --------------- |
| item-status | Indicates whether the Charge line is presently active or cancelled. If a Charge is deleted or voided it will have a status of Cancelled. If a closed charge is corrected, the original Charge will be voided with a status of Cancelled and a new Charge will be created to replace it with an Active status. | https://select.nextech-api.com/api/structuredefinition/item-status | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9.20_ |
| claim-item-identifier | Identifier for the claim item. | https://select.nextech-api.com/api/structuredefinition/claim-item-identifier| [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _14.3_ |


### Example
<pre class="center-column">
{
    "resourceType": "Claim",
    "id": "58179",
    "identifier": [
        {
            "use": "official",
            "value": "58179"
        }
    ],
    "status": "active",
    "use": "complete",
    "patient": {
        "reference": "Patient/9ad0f4a0-f407-4df8-9561-767e09d3e8df"
    },
    "billablePeriod": {
        "start": "6/13/2018"
    },
    "created": "6/13/2018",
    "facility": {
        "reference": "Location/1"
    },
    "careTeam": [
        {
            "sequence": 1,
            "provider": {
                "reference": "Practitioner/9323"
            }
        }
    ],
    "diagnosis": [
        {
            "diagnosisCodeableConcept": {
                "coding": [
                    {
                        "system": "ICD-10",
                        "code": "M23.42"
                    }
                ],
                "text": "Loose body in knee, left knee"
            }
        }
    ],
    "item": [
        {
            "extension": [
                {
                    "url": "https://select.nextech-api.com/api/structuredefinition/item-status",
                    "valueString": "active"
                }
            ],
            "careTeamLinkId": [
                1
            ],
            "service": {
                "coding": [
                    {
                        "system": "http://hl7.org/fhir/ValueSet/service-uscls",
                        "code": "99244"
                    }
                ],
                "text": "CONSULT LEVEL 4"
            },
            "servicedDateTime": "6/13/2018",
            "locationCodeableConcept": {
                "coding": [
                    {
                        "system": "http://hl7.org/fhir/ValueSet/service-place",
                        "code": "11"
                    }
                ],
                "text": "Office"
            },
            "quantity": {
                "value": 1
            },
            "unitPrice": {
                "value": 125
            },
            "net": {
                "value": 125
            }
        }
    ],
    "total": {
        "value": 125
    }
}
</pre>
&nbsp;

### *Search*
Searches for all  based on the given search criteria.

#### HTTP Request 
`GET /Claim?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or uri | The unique value assigned to each Claim which discerns it from all others. |  No | _12.9.20_ |
| use | query | The use of the Claim. (exploratory for quote or complete for bill) | No | _12.9.20_ |
| facility | query | The place of service for the Claim. | No | _12.9.20_ |
| patient | query | The patient the Claim is tied to. | No | _12.9.20_ |
| created | query | The date the Claim was created. | No | _12.9.20_ |
| care-team | query | Member of the CareTeam. | No | _12.9.20_ |

#### Example: Get Claims with a particular place of service

<pre class="center-column">
GET https://select.nextech-api.com/api/Claim?facility=1
</pre>
&nbsp;

#### Example: Get Claims with a use of complete

<pre class="center-column">
GET https://select.nextech-api.com/api/Claim?use=complete 
</pre>
&nbsp;

#### Example: Get a specific Claims attached to a patient 

<pre class="center-column">
GET https://select.nextech-api.com/api/Claim?patient=59015300-e15b-474c-8314-7864712f6946
</pre>
&nbsp;

#### Example: Get all Claims that were created on a certain date

<pre class="center-column">
GET https://select.nextech-api.com/api/Claim?created=2018-06-01
</pre>
&nbsp;

#### Example: Get a specific Claim based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/Claim/12
</pre>
&nbsp;

