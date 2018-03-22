# Coverage

## Coverage

### Overview
The Coverage resource provides patient insurance information which may be used to pay for the provision of health care products and services.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| identifier | The unique identifer for the coverage | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.9_ |
| status | The status of the coverage | [code](https://www.hl7.org/fhir/datatypes.html#code) | _12.9_ |
| type | The type of coverage (ie. Medical, Vision, Dental, Auto, Workers' Comp). See [Coverage Type Codes](http://hl7.org/fhir/valueset-coverage-type.html) | [CodeableConcept](http://hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9_ |
| subscriber | The subscriber to the policy | [Reference(Patient or RelatedPerson)](https://www.hl7.org/fhir/references.html) | _12.9_ |
| subscriberId | The identifier assigned to the subscriber | [string](http://hl7.org/fhir/datatypes.html#string) | _12.9_ |
| beneficiary | The patient who benefits from the coverage | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.9_ |
| relationship | The beneficiary (or patient) relationship to the subscriber. See [Policyholder Relationship Codes](http://hl7.org/fhir/valueset-policyholder-relationship.html) | [CodeableConcept](http://hl7.org/fhir/datatypes.html#CodeableConcept) | _12.9_ |
| period | The coverage effective and expiry dates (if available) | [Period](http://hl7.org/fhir/datatypes.html#Period) | _12.9_ |
| payor | The reference to the insurance company providing the insurance coverage | [Reference(Organization)](https://www.hl7.org/fhir/references.html) | _12.9_ |
| grouping.group | The policy group number for the coverage | [string](http://hl7.org/fhir/datatypes.html#string) | _12.9_ |
| grouping.planDisplay | The insurance plan name and type | [string](http://hl7.org/fhir/datatypes.html#string) | _12.9_ |
| order | The relative order of the coverage | [positiveInt](http://hl7.org/fhir/datatypes.html#positiveInt) | _12.9_ |

### Extensions
| Name | Description | Url | Type | Initial Version |
| ---- | ----------- | --- | ---- | --------------- |
| copay-amount | The copay amount for the 'Copay' pay group | `https://select.nextech-api.com/api/structuredefinition/copay-amount` | [Money](http://hl7.org/fhir/datatypes.html#Money) | _12.9_ |
| copay-percentage | The copay percentage for the 'Copay' pay group | `https://select.nextech-api.com/api/structuredefinition/copay-percentage` | [Integer](http://hl7.org/fhir/datatypes.html#integer) | _12.9_ |

### Example
<pre class="center-column">
{
    "resource": {
        "resourceType": "Coverage",
        "contained": [
            {
                "resourceType": "RelatedPerson",
                "id": "6783",
                "identifier": [
                    {
                        "use": "official",
                        "value": "6783"
                    }
                ],
                "name": [
                    {
                        "text": "David M Aaron",
                        "family": "Aaron",
                        "given": [
                            "David",
                            "M"
                        ]
                    }
                ],
                "gender": "male",
                "address": [
                    {
                        "use": "home",
                        "type": "both",
                        "line": [
                            "123 Fake Street"
                        ],
                        "city": "Saint Petersburg",
                        "state": "FL",
                        "postalCode": "33716"
                    }
                ]
            },
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
                        "use": "home",
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
                "url": "https://select.nextech-api.com/api/structuredefinition/copay-amount",
                "valueMoney": {
                    "value": 25
                }
            }
        ],
        "status": "active",
        "type": {
            "coding": [
                {
                    "system": "http://hl7.org/fhir/v3/ActCode",
                    "code": "EHCPOL",
                    "display": "extended healthcare"
                }
            ]
        },
        "subscriber": {
            "reference": "#6783",
            "display": "Aaron, David M"
        },
        "subscriberId": "12345678",
        "beneficiary": {
            "reference": "Patient/ce2a5ae0-3514-4f63-8609-911da841e72e",
            "display": "Aaron, Jane M"
        },
        "relationship": {
            "coding": [
                {
                    "system": "http://hl7.org/fhir/policyholder-relationship",
                    "code": "spouse",
                    "display": "Spouse"
                }
            ]
        },
        "payor": [
            {
                "reference": "#14",
                "display": "Blue Cross/Blue Shield"
            }
        ],
        "grouping": {
            "group": "abc123",
            "planDisplay": "Blue Cross/Blue Shield - Group Health Plan"
        },
        "order": 2
    }
}
</pre>
&nbsp;

### *Search*
Searches for all _active_ coverages (insured parties) based on the given search criteria.

#### HTTP Request 
`GET /Coverage?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patient | query | Search coverages by patient identifier |  N | _12.9_ |
| beneficiary | query | Search coverages by patient identifier | N | _12.9_ |

#### Example: Get coverages for a single patient

<pre class="center-column">
GET https://select.nextech-api.com/api/Coverage?patient=ce2a5ae0-3514-4f63-8609-911da841e72e
</pre>
&nbsp;