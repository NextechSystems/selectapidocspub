# DocumentReference

## DocumentReference

### Overview
A reference to a document of any kind for any purpose. Provides metadata about the document so that the document can be discovered and managed. The scope of a document is any seralized object with a mime-type, so includes formal patient centric documents (CDA), cliical notes, scanned paper, and non-patient specific documents like policy text.

### Fields
| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| masteridentifier | The unique identifier assigned to each documentreference | [Identifier](https://www.hl7.org/fhir/datatypes.html#Identifier) | _12.7_ |
| type | Specifies the particular kind of document referenced (e.g. History and Physical, Discharge Summary, Progress Note). This usually equates to the purpose of making the document referenced. LOINC Code if possible | Yes | _16.8_
| subject | The patient pertaining to the documentreference | [Reference(Patient)](https://www.hl7.org/fhir/references.html) | _12.7_ |
| date | document creation time (in UTC) | [dateTime](https://www.hl7.org/fhir/datatypes.html#dateTime) | _12.7_ |
| author | Identifies who is responsible for the information in the document reference | [Reference(Practitioner)](https://www.hl7.org/fhir/references.html#Reference) | _12.7_ |
| description | The description of the documentreference | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.7_ |
| content.attachment.contentType | The mimetype of the content.| [Code](https://www.hl7.org/fhir/datatypes.html#code) | _12.7_ |
| content.attachment.title | The title of the document| [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.7_ |
| extension: note-category | Contains the category of the document | [string](https://www.hl7.org/fhir/datatypes.html#string) | _12.8_ |
| extension: document-publish-portal | Contains whether the document is published to myPatientVisit | [boolean](https://www.hl7.org/fhir/datatypes.html#boolean)  | _12.9.20_ |
| context.encounter | The clinical context in which the document was prepared. | [Reference(US Core Encounter Profile)](https://www.hl7.org/fhir/references.html) | _16.8_ |
| custodian | Identifies the organization or group who is responsible for ongoing maintenance of and access to the document. | [Reference(USCoreOrganizationProfile)](https://www.hl7.org/fhir/references.html) | _16.8_ |


### *Get By ID*
Finds a single document based on the ID

#### HTTP Request 
`GET /DocumentReference/{documentType-id}` 

#### Parameters
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| identifier | Must be if the form `documenttype-id` i.e: GET /DocumentReference/history-5  | Yes | 16.8

#### Supported Document Types
The supported types are history, emn and labs. history and labs share identifiers so history-5 and lab-5 will refer to the same document.

#### Example: Get the history document with ID 2262 which is a text file with a content of "Hello!"
<pre class="center-column">
GET https://select.nextech-api.com/api/DocumentReference/history-2262
</pre>
&nbsp;

<pre class="center-column">
{
    "resourceType": "DocumentReference",
    "identifier": [
        {
            "use": "official",
            "value": "history-2262"
        }
    ],
    "status": "current",
    "type": {
        "coding": [
            {
                "system": "http://terminology.hl7.org/CodeSystem/v3-NullFlavor",
                "code": "UNK"
            }
        ],
        "text": "unknown"
    },
    "category": [
        {
            "coding": [
                {
                    "system": "http://hl7.org/fhir/us/core/CodeSystem/us-core-documentreference-category",
                    "code": "Miscellaneous",
                    "display": "Miscellaneous"
                }
            ],
            "text": "Miscellaneous"
        }
    ],
    "subject": {
        "reference": "Patient/c21ab936-3a2a-4c5a-81b8-76b120194053",
        "display": "White, Nicole Francis"
    },
    "date": "2022-06-02T17:11:23.943+00:00",
    "author": [
        {
            "reference": "Organization/22",
            "display": "Clinic One"
        }
    ],
    "custodian": {
        "reference": "Organization/22",
        "display": "Clinic One"
    },
    "content": [
        {
            "attachment": {
                "contentType": "text/plain",
                "data": "U0dWc2JHOGg=",
                "title": "small text doc.txt"
            },
            "format": {
                "system": "urn:oid:1.3.6.1.4.1.19376.1.2.3",
                "code": "urn:ihe:iti:xds:2017:mimeTypeSufficient",
                "display": "mimeType Sufficient"
            }
        }
    ],
    "context": {
        "period": {
            "start": "2022-06-02T17:11:23.943+00:00",
            "end": "2022-06-02T17:11:23.943+00:00"
        }
    }
}
</pre>
&nbsp;

### *Create*
Creates the document in the content.attachment for a patient and attaches it to the patient's history tab in the Nextech software.

#### HTTP Request 
`POST /DocumentReference` 

#### Body Fields
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| resourceType | Must be `DocumentReference` | Yes |
| type | Specifies the particular kind of document referenced (e.g. History and Physical, Discharge Summary, Progress Note). This usually equates to the purpose of making the document referenced. LOINC Code if possible | Yes | _16.8_ |
| date | The date (in UTC) of the composition. ie. `2017-10-16T20:32:28.9692476Z` | No | _12.7_ |
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
POST https://select.nextech-api.com/api/r4/DocumentReference
</pre>
&nbsp;

#### Body
<pre class="center-column">
{
    "resourceType": "DocumentReference",
    "type": {
        "coding": [
            {
                "system": "http://loinc.org",
                "code": "18842-5",
                "display": "Discharge Summary"
            }
        ],
        "text": "Discharge Summary"
    },
    "subject": {
        "reference": "[base]/Patient/9CFE7258-8F50-45E8-9732-6433976CC164"
    },
    "content": [{"attachment": {
        "contentType": "text/plain",
        "data": "Tm8gYWN0aXZpdHkgcmVzdHJpY3Rpb24sIHJlZ3VsYXIgZGlldCwgZm9sbG93IHVwIGluIHR3byB0byB0aHJlZSB3ZWVrcyB3aXRoIHByaW1hcnkgY2FyZSBwcm92aWRlci4="
    } }],
    "context": {"encounter": {"reference": "[base]/Encounter/1"} },
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
}
</pre>
&nbsp;

### *Create CCDA*
This generates a CCDA for the given patient and attaches it to their patient history

#### HTTP Request
`POST /DocumentReference/$docref`

#### Body Fields
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| resourceType | Must be `Parameters` | Yes |
| parameter | This is an array of [parameters](https://www.hl7.org/fhir/parameters.html) which must include one patient parameter | Yes |
| parameter.patient | The patient the document is for | Yes |

#### Example: Generating a CCDA for patient with an ID of C21AB936-3A2A-4C5A-81B8-76B120194053 via POST
<pre class="center-column">
POST https://select.nextech-api.com/api/r4/DocumentReference/$docref
</pre>
&nbsp;

#### Body
<pre class="center-column">
 {
      "resourceType": "Parameters",
      "parameter": [
        {
          "name": "patient",
          "valueId" : "C21AB936-3A2A-4C5A-81B8-76B120194053"
        }
      ]
    }
</pre>
Note: the response body will be the same as the GET example below

#### HTTP Request 
`GET /DocumentReference/$docref?{patient}`

#### Parameters
| Name | Description | Required | Initial Version |
| ---- | ----------- | -------- | --------------- |
| patient | Must be in the form `patient={patient GUID}` i.e: `patient=C21AB936-3A2A-4C5A-81B8-76B120194053` | Yes | 16.8

#### *Note: This will result in creating a new document attached to the patient's chart every request despite being a GET*

#### Example: Generating a CCDA for patient with an ID of C21AB936-3A2A-4C5A-81B8-76B120194053 via GET
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference/$docref?patient=C21AB936-3A2A-4C5A-81B8-76B120194053
</pre>
#### Response
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 1,
    "entry": [
        {
            "resource": {
                "resourceType": "DocumentReference",
                "identifier": [
                    {
                        "use": "official",
                        "value": "history-2263"
                    }
                ],
                "status": "current",
                "type": {
                    "coding": [
                        {
                            "system": "http://loinc.org",
                            "code": "34133-9"
                        }
                    ],
                    "text": "Summarization of Episode Note"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "http://hl7.org/fhir/us/core/CodeSystem/us-core-documentreference-category",
                                "code": "clinical-note",
                                "display": "clinical-note"
                            }
                        ],
                        "text": "clinical-note"
                    }
                ],
                "subject": {
                    "reference": "Patient/c21ab936-3a2a-4c5a-81b8-76b120194053",
                    "display": "White, Nicole Francis"
                },
                "date": "2022-06-02T13:26:26.2198865-04:00",
                "author": [
                    {
                        "reference": "Organization/1",
                        "display": "Pawtucket Plastic Surgeons"
                    }
                ],
                "custodian": {
                    "reference": "Organization/1",
                    "display": "Pawtucket Plastic Surgeons"
                },
                "content": [
                    {
                        "attachment": {
                            "contentType": "application/xml",
                            "data": ""
                        },
                        "format": {
                            "system": "urn:oid:1.3.6.1.4.1.19376.1.2.3",
                            "code": "urn:hl7-org:sdwg:ccda-structuredBody:2.1",
                            "display": "Documents following C-CDA constraints using a structured body"
                        }
                    }
                ],
                "context": {
                    "encounter": [
                        {
                            "reference": "Encounter/8109"
                        }
                    ],
                    "period": {
                        "start": "2022-06-02T13:26:26.2198865-04:00",
                        "end": "2022-06-02T13:26:26.2198865-04:00"
                    }
                }
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

