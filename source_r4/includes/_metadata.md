# Metadata

## Metadata

### Overview
Information about supported server functionality and server's SMART on FHIR configuration.

### Capability Statement

#### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| resourceType | The declaration of the type of resource this is. | [string](https://www.hl7.org/fhir/datatypes.html#string) | |
| status | The status of this capability statement. | [code](https://www.hl7.org/fhir/datatypes.html#code) | |
| date |The date (and optionally time) when the capability statement was published.|[dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | |
| publisher | The name of the organization or individual that published the capability statement. | [string](https://www.hl7.org/fhir/datatypes.html#string) | |
| kind | The way that this statement is intended to be used, to describe an actual running instance of software, a particular product or a class of implementation. | [code](https://www.hl7.org/fhir/datatypes.html#code) | |
| implementation.description | Information about the specific installation that this capability statement relates to. | [string](https://www.hl7.org/fhir/datatypes.html#string) | |
| implementation.url | An absolute base URL for the implementation. | [url](https://www.hl7.org/fhir/datatypes.html#url) | |
| fhirVersion | The version of the FHIR specification that this CapabilityStatement describes. | [code](https://www.hl7.org/fhir/datatypes.html#code) | |
| format | A list of the formats supported by this implementation using their content types. | [code](https://www.hl7.org/fhir/datatypes.html#code) | |
| implementationGuide | A list of implementation guides that the server does (or should) support in their entirety. | [canonical](https://www.hl7.org/fhir/datatypes.html#canonical)([Implementation Guide](https://www.hl7.org/fhir/implementationguide.html)) ||
| instantiates | Reference to a canonical URL of another CapabilityStatement that this software implements. | [canonical](https://www.hl7.org/fhir/datatypes.html#canonical)([Capabiliy Statement](https://www.hl7.org/fhir/capabilitystatement.html)) | |
| rest.mode | Identifies whether this portion of the statement is describing the ability to initiate or receive restful operations. | [code](https://www.hl7.org/fhir/datatypes.html#code) | |
| rest.security.extension | The oauth uris for this server ('authorize' and 'token' endpoints). | [Extension](https://build.fhir.org/extensibility.html#Extension) | |
| rest.security.service | Types of security services that are supported by the system. | [CodeableConcept](https://www.hl7.org/fhir/datatypes.html#CodeableConcept) | |
| rest.resource.type | A type of resource exposed via the restful interface. | [code](https://www.hl7.org/fhir/datatypes.html#code) | |
| rest.resource.supportedProfile | A list of profiles that represent different use cases supported by the system. | [canonical](https://www.hl7.org/fhir/datatypes.html#canonical)([StructureDefinition](https://www.hl7.org/fhir/structuredefinition.html)) | |
| rest.resource.interaction.code | Coded identifier of the operation, supported by the system resource. | [code](https://www.hl7.org/fhir/datatypes.html#code) | |
| rest.resource.searchRevInclude | A list of _revinclude (reverse include) values supported by the server. | [string](https://www.hl7.org/fhir/datatypes.html#string) ||
| rest.resource.searchParam.name | The name of the search parameter used in the interface. | [string](https://www.hl7.org/fhir/datatypes.html#string) | |
| rest.resource.searchParam.type | The type of value a search parameter refers to, and how the content is interpreted. | [code](https://www.hl7.org/fhir/datatypes.html#code) | |
| rest.resource.operation.name | The name of the operation or query. | [string](https://www.hl7.org/fhir/datatypes.html#string) | |

&nbsp;

#### Example
<pre class="center-column">
{
    "resourceType": "CapabilityStatement",
    "status": "active",
    "date": "2022-06-30",
    "publisher": "Nextech Systems, LLC",
    "kind": "instance",
    "implementation": {
        "description": "PartnerAPI provides secure access to patient data through a RESTful implementation based on the R4 version of the FHIR standard.",
        "url": "https://nxpartnerapi-dev.azurewebsites.net/"
    },
    "fhirVersion": "4.0.1",
    "format": [
        "application/fhir+xml",
        "application/fhir+json"
    ],
    "implementationGuide": [
        "http://hl7.org/fhir/r4/implementationguide.html"
    ],
    "instantiates": [
        "http://hl7.org/fhir/uv/bulkdata/CapabilityStatement/bulk-data"
    ],
    "rest": [
        {
            "mode": "server",
            "security": {
                "extension": [
                    {
                        "url": "http://fhir-registry.smarthealthit.org/StructureDefinition/oauth-uris",
                        "extension": [
                            {
                                "url": "token",
                                "valueUri": "https://mypatientvisit-sts-dev.azurewebsites.net"
                            },
                            {
                                "url": "authorize",
                                "valueUri": "https://mypatientvisit-sts-dev.azurewebsites.net"
                            }
                        ]
                    }
                ],
                "service": [
                    {
                        "coding": [
                            {
                                "system": "http://terminology.hl7.org/CodeSystem/restful-security-service",
                                "code": "SMART-on-FHIR"
                            }
                        ],
                        "text": "OAuth2 using SMART-on-FHIR profile (see http://docs.smarthealthit.org)"
                    }
                ]
            },
            "resource": [
                {
                    "type": "AllergyIntolerance",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-allergyintolerance"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "CarePlan",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-careplan"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "category",
                            "type": "token"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "CareTeam",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-careteam"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "status",
                            "type": "token"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Condition",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-condition"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Device",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-implantable-device"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "date",
                            "type": "date"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "DiagnosticReport",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-diagnosticreport-lab",
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-diagnosticreport-note"
                    ],
                    "interaction": [
                        {
                            "code": "create"
                        },
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "category",
                            "type": "token"
                        },
                        {
                            "name": "code",
                            "type": "token"
                        },
                        {
                            "name": "date",
                            "type": "date"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "DocumentReference",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-documentreference"
                    ],
                    "interaction": [
                        {
                            "code": "create"
                        },
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "category",
                            "type": "token"
                        },
                        {
                            "name": "type",
                            "type": "token"
                        },
                        {
                            "name": "date",
                            "type": "date"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Encounter",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-encounter"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "date",
                            "type": "date"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Goal",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-goal"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "date",
                            "type": "date"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Group",
                    "operation": [
                        {
                            "name": "export",
                            "definition": "http://hl7.org/fhir/uv/bulkdata/OperationDefinition/group-export"
                        }
                    ]
                },
                {
                    "type": "Immunization",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-immunization"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "date",
                            "type": "date"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Location",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-location"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "name",
                            "type": "string"
                        },
                        {
                            "name": "address",
                            "type": "string"
                        },
                        {
                            "name": "status",
                            "type": "string"
                        },
                        {
                            "name": "includeall",
                            "type": "string"
                        },
                        {
                            "name": "address-city",
                            "type": "string"
                        },
                        {
                            "name": "address-state",
                            "type": "string"
                        },
                        {
                            "name": "address-postalcode",
                            "type": "string"
                        },
                        {
                            "name": "phone",
                            "type": "string"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Medication",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-medication"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchParam": [
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "MedicationRequest",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-medicationrequest"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "status",
                            "type": "token"
                        },
                        {
                            "name": "intent",
                            "type": "token"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Observation",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-smokingstatus",
                        "http://hl7.org/fhir/us/core/StructureDefinition/pediatric-weight-for-height",
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-observation-lab",
                        "http://hl7.org/fhir/us/core/StructureDefinition/pediatric-bmi-for-age",
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-pulse-oximetry",
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-pulse-oximetry",
                        "http://hl7.org/fhir/us/core/StructureDefinition/head-occipital-frontal-circumference-percentile",
                        "http://hl7.org/fhir/StructureDefinition/bp",
                        "http://hl7.org/fhir/StructureDefinition/bodyheight",
                        "http://hl7.org/fhir/StructureDefinition/bodyweight",
                        "http://hl7.org/fhir/StructureDefinition/heartrate",
                        "http://hl7.org/fhir/StructureDefinition/resprate",
                        "http://hl7.org/fhir/StructureDefinition/bodytemp"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "category",
                            "type": "token"
                        },
                        {
                            "name": "code",
                            "type": "token"
                        },
                        {
                            "name": "date",
                            "type": "date"
                        },
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Organization",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-organization"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchParam": [
                        {
                            "name": "name",
                            "type": "string"
                        },
                        {
                            "name": "address",
                            "type": "string"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Patient",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-patient"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "birthdate",
                            "type": "date"
                        },
                        {
                            "name": "gender",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "name",
                            "type": "string"
                        },
                        {
                            "name": "family",
                            "type": "string"
                        },
                        {
                            "name": "given",
                            "type": "string"
                        },
                        {
                            "name": "phone",
                            "type": "string"
                        },
                        {
                            "name": "address",
                            "type": "string"
                        },
                        {
                            "name": "address-city",
                            "type": "string"
                        },
                        {
                            "name": "address-state",
                            "type": "string"
                        },
                        {
                            "name": "address-postalcode",
                            "type": "string"
                        },
                        {
                            "name": "email",
                            "type": "string"
                        },
                        {
                            "name": "group-id",
                            "type": "number"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Practitioner",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-practitioner"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchParam": [
                        {
                            "name": "name",
                            "type": "string"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "gender",
                            "type": "token"
                        },
                        {
                            "name": "active",
                            "type": "string"
                        },
                        {
                            "name": "family",
                            "type": "string"
                        },
                        {
                            "name": "given",
                            "type": "string"
                        },
                        {
                            "name": "phone",
                            "type": "string"
                        },
                        {
                            "name": "address",
                            "type": "string"
                        },
                        {
                            "name": "address-city",
                            "type": "string"
                        },
                        {
                            "name": "address-state",
                            "type": "string"
                        },
                        {
                            "name": "address-postalcode",
                            "type": "string"
                        },
                        {
                            "name": "email",
                            "type": "string"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Procedure",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-procedure"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchRevInclude": [
                        "Provenance:target"
                    ],
                    "searchParam": [
                        {
                            "name": "patient",
                            "type": "reference"
                        },
                        {
                            "name": "_id",
                            "type": "token"
                        },
                        {
                            "name": "identifier",
                            "type": "token"
                        },
                        {
                            "name": "date",
                            "type": "date"
                        },
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                },
                {
                    "type": "Provenance",
                    "supportedProfile": [
                        "http://hl7.org/fhir/us/core/StructureDefinition/us-core-provenance"
                    ],
                    "interaction": [
                        {
                            "code": "search-type"
                        },
                        {
                            "code": "read"
                        }
                    ],
                    "searchParam": [
                        {
                            "name": "_lastUpdated",
                            "type": "date"
                        }
                    ]
                }
            ],
            "operation": [
                {
                    "extension": [
                        {
                            "url": "http://hl7.org/fhir/StructureDefinition/capabilitystatement-expectation",
                            "valueCode": "SHOULD"
                        }
                    ],
                    "name": "export",
                    "definition": "http://hl7.org/fhir/uv/bulkdata/OperationDefinition/export"
                }
            ]
        }
    ]
}
</pre>
&nbsp;

#### *Get*
Retrieves the Capability Statement which holds information about supported server functionality.

##### HTTP Request 
`GET /r4/metadata`

##### Example: Get Capability Statement

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/metadata
</pre>
&nbsp;

### SMART Configuration

#### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| capabilities | Array of strings representing SMART capabilities | [string](https://www.hl7.org/fhir/datatypes.html#string) | |
| authorization_endpoint | URL to the OAuth2 authorization endpoint | [url](https://www.hl7.org/fhir/datatypes.html#url) | |
| token_endpoint | URL to the OAuth2 token endpoint | [url](https://www.hl7.org/fhir/datatypes.html#url) | |
| token_endpoint_auth_methods_supported | Array of client authentication methods supported by the token endpoint | [string](https://www.hl7.org/fhir/datatypes.html#string) | |
| token_endpoint_auth_signing_alg_values_supported | Array containing a list of the JWS signing algorithms supported by the token endpoint. | [string](https://www.hl7.org/fhir/datatypes.html#string) | |

#### Example
<pre class="center-column">
{
    "capabilities": [
        "launch-ehr",
        "launch-standalone",
        "client-public",
        "client-confidential-symmetric",
        "sso-openid-connect",
        "context-banner",
        "context-style",
        "context-ehr-patient",
        "context-ehr-encounter",
        "context-standalone-patient",
        "context-standalone-encounter",
        "permission-offline",
        "permission-patient",
        "permission-user"
    ],
    "authorization_endpoint": "https://mypatientvisit-sts-dev.azurewebsites.net",
    "token_endpoint": "https://mypatientvisit-sts-dev.azurewebsites.net",
    "token_endpoint_auth_methods_supported": [
        "private_key_jwt"
    ],
    "token_endpoint_auth_signing_alg_values_supported": [
        "RS384",
        "ES384"
    ]
}
</pre>
&nbsp;

#### *Get*
Retrieves server's SMART on FHIR configuration

##### HTTP Request 
`GET /r4/.well-known/smart-configuration`


##### Example: Get SMART on FHIR configuration

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/.well-known/smart-configuration
</pre>
&nbsp;