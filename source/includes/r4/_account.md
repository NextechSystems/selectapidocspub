# Account

### Overview
The [Account](https://hl7.org/fhir/R4/account.html) resource represents a financial tool for tracking value accrued for a particular purpose. In Nextech, it's used to track the patient's responsibility.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| id | Unique identifier used to reference the account. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _12.9_ |
| identifier | Unique identifier used to reference the account. | [Identifier](https://www.hl7.org/fhir/R4/datatypes.html#Identifier) | _12.9_ |
| name |The name associated with the Account. | [string](https://www.hl7.org/fhir/R4/datatypes.html#string) | _12.9_ |
| status | Indicates whether the account is presently used/usable or not. | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _12.9_ |
| type | Categorizes the account for reporting and searching purposes. | [CodeableConcept](https://www.hl7.org/fhir/R4/datatypes.html#CodeableConcept) | _12.9_ |
| balance | Represents the sum of all credits less all debits associated with the account. Might be positive, zero or negative. | [Money](https://www.hl7.org/fhir/R4/datatypes.html#Money) | _12.9_ |
| description | Provides additional information about what the account tracks and how it is used. | [string](https://www.hl7.org/fhir/R4/datatypes.html#String) | _12.9_ |
| subject | Identifies the patient or other object the account is associated with. | [Reference](https://www.hl7.org/fhir/R4/references.html) | _12.9_ |
| guarantor | Party financially responsible for the account. | [BackboneElement](https://www.hl7.org/fhir/R4/backboneelement.html) | _12.9_ |
| guarantor.party | The entity who is responsible. | [Reference](https://www.hl7.org/fhir/R4/references.html)([US Core Patient Profile](https://hl7.org/fhir/us/core/STU3.1.1/StructureDefinition-us-core-patient.html)) | _12.9_ |
}



### Example
<pre class="center-column">
{
    "resourceType": "Account",
    "id": "3200",
    "identifier": [
        {
            "use": "official",
            "value": "3200"
        }
    ],
    "status": "active",
    "type": {
        "coding": [
            {
                "system": "https://www.hl7.org/fhir/valueset-account-type.html",
                "code": "PBILLACCT"
            }
        ],
        "text": "Patient"
    },
    "name": "Test, John",
    "subject": {
        "reference": "Patient/59015300-e15b-474c-8314-7864712f6946"
    },
    "balance": {
        "value": 21
    },
    "description": "Patient Responsibility",
    "guarantor": [
        {
            "party": {
                "reference": "Patient/59015300-e15b-474c-8314-7864712f6946"
            }
        }
    ]
}
</pre>
&nbsp;

### *Get*
Returns a single Account based on the account ID.

#### HTTP Request

- `GET /r4/Account/{accountID}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| accountID | path | The account identifier | Yes | 12.9 |

#### Example: Get a specific Account with an id of '12'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Account/12
</pre>
&nbsp;

### *Search*
Searches for all accounts based on the given search criteria.

#### HTTP Request 
`GET r4/Account?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query or uri | The unique value assigned to each Account which discerns it from all others. |  No | _12.9_ |
| status | query | Searches for Accounts whose record has the search status.| No | _12.9_ |
| name | query | The name of the Account. | No | _12.9_ |
| balance | query | The balance of the Account. | No | _12.9_ |
| patient | query | The patient the account is tied to. | No | _12.9_ |

#### Example: Get all active Accounts

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Account?status=active
</pre>
&nbsp;

#### Example: Get accounts with a balance greater than zero

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Account?balance=gt0
</pre>
&nbsp;

#### Example: Get a specific Account attached to a patient 

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Account?patient=59015300-e15b-474c-8314-7864712f6946
</pre>
&nbsp;

#### Example: Get all Accounts whose name contains 'smith'

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Account?name:contains=smith
</pre>
&nbsp;

