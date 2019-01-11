# PaymentReconciliation

## PaymentReconciliation

### Overview
A list of payments, adjustments, and refunds. Can be insurance or self-pay. 

#### Body Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | -------- | --------------- |
| requestProvider | The responsible practitioner. | [Reference(Practitioner)](https://www.hl7.org/fhir/references.html) | _14.2_ |
| total | The PaymentReconciliation amount total. | [Money](http://hl7.org/fhir/datatypes.html#Money) | _14.2_ |
| processNote | The PaymentReconciliation description. | [BackboneElement](https://www.hl7.org/fhir/backboneelement.html) | _14.2_ |
| created | The creation date. | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _14.2_ |
| status | The status of the PaymentReconciliation. This will be one of the following values active, cancelled ( voided ), entered-in-error ( deleted ) . <br> • For purposes of calculating the current balance of a patient account, Cancelled transactions may be excluded. <br> • For purposes of keeping a history of financial transactions that happened in a specific accounting period (by input date field/effective date extension) then the cancelled transactions should be included. <br> • When a transaction is Voided in Nextech, the original transaction remains unchanged in the original accounting period, but has a status of ‘Cancelled’. A new transaction that is the exact opposite of the original is created with a current input date/effective date and also has a status of ‘Cancelled’. The net of these transactions are $0. <br> • When a transaction is Voided & Corrected in Nextech, the original transaction remains unchanged in the the original accounting period, but has a status of ‘Cancelled’. A new transaction that is the exact opposite of the original is created with a current input date/effective date and also has a status of ‘Cancelled’. The net of these transactions are $0. A new “corrected” transaction is also created which is an copy of the original transaction, except for the input/effective date. The “corrected” transaction may be edited by the practice to change properties of the payment like the provider, location, amount, etc. | [code](https://www.hl7.org/fhir/datatypes.html#code) | _14.2_| 
| organization | The Insurer who is associated with the PaymentReconciliation. ( Insurance payments, adjustments and refunds only ). If there is no organization associated with a PaymentReconciliation, the PaymentReconciliation is in reference patient responsibility. | [Reference(Organization)](https://www.hl7.org/fhir/references.html) | _14.2_ |
| detail | List of individual settlement amounts and the corresponding transaction. | [Control](https://www.hl7.org/fhir/conformance-rules.html#conformance) | _14.2_| 
| detail.request | 	The claim or financial resource. | [Reference(Claim)](https://www.hl7.org/fhir/references.html) | _14.2_| 
| detail.type | Code to indicate the nature of the payment or adjustment (refund is categorized as a payment with negative amount). See [Payment Type Codes](http://hl7.org/fhir/codesystem-payment-type.html)  | [Code](https://www.hl7.org/fhir/datatypes.html#code) | _14.2_| 
| detail.amount | Amount paid for this detail. ( payments, adjustments, or refund amount applied to claim ) | [Money](http://hl7.org/fhir/datatypes.html#Money) | _14.2_ |

### Extensions
| Name | Description | Url  | Type | Initial Version |
| ---- | ----------- | ---  | ---- | --------------- |
| extension: claim-item | Reference to a claim item. |`https://select.nextech-api.com/api/structuredefinition/claim-item`| [Reference(Claim.item)](https://www.hl7.org/fhir/references.html) | _14.3_ |
| extension: applied-amount | The amount applied to a claim item from the PaymentReconciliation. |`https://select.nextech-api.com/api/structuredefinition/applied-amount` | [Money](http://hl7.org/fhir/datatypes.html#Money)| _14.3_ |
| extension: payment-method | The PaymentReconciliation method. |`https://select.nextech-api.com/api/structuredefinition/payment-method` |[string](http://hl7.org/fhir/datatypes.html#string) | _14.2_ |
| extension: payment-date | The PaymentReconciliation date.  |`https://select.nextech-api.com/api/structuredefinition/payment-date` |[dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) |  _14.2_ |
| extension: effective-date | The PaymentReconciliation input date. |`https://select.nextech-api.com/api/structuredefinition/effective-date` | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _14.2_ |
| extension: deposited-date | The PaymentReconciliation deposit date. |`https://select.nextech-api.com/api/structuredefinition/deposit-date` |[dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _14.2_ |
| extension: payment-category | The PaymentReconciliation category. |`https://select.nextech-api.com/api/structuredefinition/payment-category` |[string](http://hl7.org/fhir/datatypes.html#string) | _14.2_ |
| extension: credit-cardtype | The PaymentReconciliation credit card type. |`https://select.nextech-api.com/api/structuredefinition/credit-cardtype` | [string](http://hl7.org/fhir/datatypes.html#string) | _14.2_ |
| extension: check-number | The PaymentReconciliation check number |`https://select.nextech-api.com/api/structuredefinition/check-number` |[string](http://hl7.org/fhir/datatypes.html#string) | _14.2_ |
| extension: location | The PaymentReconciliation location reference. The practice must have at least one Location resource with this identifier. |`http://hl7.org/fhir/StructureDefinition/Location` |[Reference(Location)](https://www.hl7.org/fhir/references.html) | _14.2_ |


### Example
<pre class="center-column">
{
    "resourceType": "PaymentReconciliation",
    "id": "126671",
    "contained": [
        {
            "resourceType": "Organization",
            "id": "14",
            "identifier": [
                {
                    "use": "official",
                    "value": "14"
                }
            ],
            "type": [
                {
                    "coding": [
                        {
                            "system": "http://hl7.org/fhir/organization-type",
                            "code": "ins",
                            "display": "Insurance Company"
                        }
                    ]
                }
            ],
            "name": "Blue Cross/Blue Shield",
            "address": [
                {
                    "use": "work",
                    "type": "both",
                    "line": [
                        "123 Great Payment Way"
                    ],
                    "city": "Dallas",
                    "state": "TX",
                    "postalCode": "75201"
                }
            ]
        }
    ],
    "extension": [
        {
            "url": "http://hl7.org/fhir/StructureDefinition/Patient",
            "valueResourceReference": {
                "reference": "Patient/1ed5d91a-ce2d-4551-98d9-eecfc3b1ed2c",
                "display": "RevAPI, Test"
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
            "valueDateTime": "2018-12-12T05:00:00.000Z"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/effective-date",
            "valueDateTime": "2018-12-12T15:13:24.690Z"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/payment-method",
            "valueString": "Check"
        },
        {
            "url": "https://select.nextech-api.com/api/structuredefinition/payment-category",
            "valueString": "CO- Patient Co-Pay"
        }
    ],
    "identifier": [
        {
            "use": "official",
            "value": "126671"
        }
    ],
    "status": "active",
    "created": "2018-12-12T15:13:24.690Z",
    "organization": {
        "reference": "#14",
        "display": "Blue Cross/Blue Shield"
    },
    "detail": [
        {
            "type": {
                "coding": [
                    {
                        "system": "http://hl7.org/fhir/payment-type",
                        "code": "payment"
                    }
                ]
            },
            "request": {
                "reference": "Claim/58195"
            },
            "amount": {
                "value": 1000
            }
        }
    ],
    "total": {
        "value": 1000
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
            "text": "Insurance Payment"
        }
    ]
}
</pre>
&nbsp;

### *Search*
Searches for all  based on the given search criteria.

#### HTTP Request 
`GET /PaymentReconciliation?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or uri | The unique value assigned to each PaymentReconciliation. |  No | _14.2_ |
| location.id | query | The location for the PaymentReconciliation. | No | _14.2_ |
| patient | query | The patient the PaymentReconciliation is tied to. | No | _14.2_ |
| created | query | The date the PaymentReconciliation was created. | No | _14.2_ |
| status | query | The status of the PaymentReconciliation. This must be one of the following active, cancelled ( voided ), entered-in-error ( deleted ).  | No | _14.2_ |
| payment-date | query |The date of service for the PaymentReconciliation. | No | _14.2_ |
| request-provider| query | The provider associated with the PaymentReconciliation. This is a practitioner reference. | No | _14.2_ |


#### Example: Get PaymentReconciliations with a particular place of service

<pre class="center-column">
GET https://select.nextech-api.com/api/PaymentReconciliation?location.id=1
</pre>
&nbsp;

#### Example: Get PaymentReconciliations with a status of active

<pre class="center-column">
GET https://select.nextech-api.com/api/PaymentReconciliation?status=active
</pre>
&nbsp;

#### Example: Get a specific PaymentReconciliations attached to a patient 

<pre class="center-column">
GET https://select.nextech-api.com/api/PaymentReconciliation?patient=59015300-e15b-474c-8314-7864712f6946
</pre>
&nbsp;

#### Example: Get all PaymentReconciliations that were created on a certain date

<pre class="center-column">
GET https://select.nextech-api.com/api/PaymentReconciliation?created=2018-06-01
</pre>
&nbsp;

#### Example: Get all PaymentReconciliations on a certain date of service.

<pre class="center-column">
GET https://select.nextech-api.com/api/PaymentReconciliation?payment-date=2018-06-01
</pre>
&nbsp;

#### Example: Get all PaymentReconciliations for a certain practitioner.

<pre class="center-column">
GET https://select.nextech-api.com/api/PaymentReconciliation?request-provider=1
</pre>
&nbsp;

#### Example: Get a specific PaymentReconciliation based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/PaymentReconciliation/12
</pre>
&nbsp;



