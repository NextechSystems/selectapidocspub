# DocumentReference

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
| context.encounter | The clinical context in which the document was prepared. | [Reference(US Core Encounter Profile)](https://www.hl7.org/fhir/references.html) | _16.8_ |
| custodian | Identifies the organization or group who is responsible for ongoing maintenance of and access to the document. | [Reference(USCoreOrganizationProfile)](https://www.hl7.org/fhir/references.html) | _16.8_ |


### *Search*
Finds a bundle documents based on the search parameters

#### HTTP Request 
`GET /DocumentReference?{parameters}` 
`POST /DocumentReference/_search`
  - *application/x-www-form-urlencoded payload:* `{parameters}`
> **_Note:_**  For POST based searches the parameters can be provided in either the URL, the body, or both. 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _id | query or payload | Must be in the form `documenttype-id` i.e: GET /DocumentReference?_id=history-5  | No | 16.8
| patient | query or payload | The ID of the patient associated with the document | No | 16.9
| category | query or payload | The category of the document | No | 16.9
| date | query or payload| This searches based on the created date of the document, either a specific date or a range depending on search modifiers | No | 16.9
| type | query or payload| The type of the document | No | 16.9
> **_Note:_**  The possible filter values for the date parameter are: `eq`, `ne`, `le`, `lt`, `ge` and `gt`. 

#### Supported Document Types
The supported types are history and EMN.

#### Example: Get the history document with ID 7741
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference?_id=history-7741
</pre>
&nbsp;

#### Example: Searching for all documents that have a type of 11488-4, category of Unknown, created on 2022-06-03 for the specific patient
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference?type=11488-4&category=Unknown&date=2022-06-03&patient=c21ab936-3a2a-4c5a-81b8-76b120194053
</pre>
&nbsp;

#### Example: Search for all documents that were created between 2020-06-03 and 2022-06-01
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference?date=gt2020-06-03&date=lt2022-06-01
</pre>
&nbsp;
#### Example Search by _id in POST Body

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/DocumentReference
<i><small>payload:</small></i> 
_id:history-2262
</pre>

#### Example Searching for all documents that have a type of 11488-4, category of Clinical, created before 2022-06-03 for the specific patient

<pre class="center-column">
POST https://select.nextech-api.com/api/r4/DocumentReference
<i><small>payload:</small></i> 
type:11488-4
category:Clinical
date:lt2022-06-03
patient:c21ab936-3a2a-4c5a-81b8-76b120194053
</pre>


### *Get By ID*
Finds a single document based on the ID

#### HTTP Request 
`GET /DocumentReference/{documentType-id}` 

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| DocumentReferenceID | path | Must be if the form `documenttype-id` i.e: GET /DocumentReference/history-5  | Yes | 16.8

#### Supported Document Types
The supported types are history and EMN.

#### Example: Get the history document with ID 2262 which is a text file with a content of "Hello!"
<pre class="center-column">
GET https://select.nextech-api.com/api/r4/DocumentReference/history-2262
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
                "system": "http://loinc.org",
                "code": "18842-5",
                "display": "Discharge Summary"
            }
        ],
        "text": "Discharge Summary"
    },
    "category": [
        {
            "coding": [
                {
                    "system": "https://select.nextech-api.com/api/structuredefinition/note-category",
                    "code": "Prescriptions",
                    "display": "Prescriptions"
                }
            ],
            "text": "Prescriptions"
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
        "encounter": [
            {
                "reference": "Encounter/6",
                "display": "Encounter Name"
            }
        ],
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
| resourceType | Must be `DocumentReference` | Yes | _12.7_ |
| type | Specifies the particular kind of document referenced (e.g. History and Physical, Discharge Summary, Progress Note). This usually equates to the purpose of making the document referenced. LOINC Code if possible | Yes | _16.8_ |
| date | The date (in UTC) of the composition. ie. `2017-10-16T20:32:28.9692476Z` | No | _12.7_ |
| author.display | The name of the author. This will be appended to the beginning of the description value. | No | _12.7_ |
| description | A description of the document | No | _12.7_ |
| content.attachment.contentType | The mimetype of the document. See Allowed Mimetypes below | Yes | _12.7_ |
| content.attachment.data | The base64 data of the document | Yes | _12.7_ |
| content.attachment.title | The title of the document, will be used as the filename| Yes | _12.7_ |

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
    "context": {"encounter": {"reference": "[base]/Encounter/1"} }
}
</pre>
&nbsp;

### *$docref*
This generates a CCDA for the given patient and attaches it to their patient history if no Summary of Care has been previously generated for the relevant encounters.
Otherwise, this returns the most recent CCDA Summary of Care document generated for each encounter.
If only patient is specified, then it will return one (1) Summary of Care document reference record for the latest encounter.
If patient and a date range is specified (start, end, start+end), then it will return one document reference for each encounter that falls within that range.

#### HTTP Request
`POST /DocumentReference/$docref`

#### Body Fields
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| resourceType | body | Must be `Parameters` | Yes | 16.9 |
| parameter | body |This is an array of [parameters](https://www.hl7.org/fhir/parameters.html) which must include one patient parameter | Yes | 16.9 |
| parameter.patient | body | The patient the document is for | Yes | 16.9 |
| parameter.start | body | The start date for EMN encounters | No | 16.9 |
| parameter.end | body | the end date for EMN encounters | No | 16.9 |

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
        },
        {
            "name": "start",
            "valueDateTime": "2022-02-23T08:00:00"
        },
        {
            "name": "end",
            "valueDateTime": "2022-02-24T08:00:00"
        }
      ]
    }
</pre>
Note: The `start` and `end` parameters can be either of type `valueDateTime` as above, or simply `valueDate` and passing only values such as `2022-02-23`
Note: the response body will be the same as the GET example below

#### HTTP Request 
`GET /DocumentReference/$docref?{patient}[&{start}][&{end}]`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| patient | query | Must be in the form `{patient GUID}` i.e: `patient=C21AB936-3A2A-4C5A-81B8-76B120194053` | Yes | 16.9 |
| start | query | Must be in the form of either  `2022-02-23T08:00:00` or `2022-02-23` | No | 16.9 |
| end | query | Must be in the form of either `2022-02-24T08:00:00` or `2022-02-24` | No | 16.9 |

#### *Note: Despite being a GET request, if an encounter that falls within the date range (if supplied) or the most recent encounter does not have a CCDA Summary of Care document previously generated, this request will cause one to be created and attached to the patient's document history*

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
                            "code": "18842-5",
                            "display": "Discharge Summary"
                        }
                    ],
                    "text": "Discharge Summary"
                },
                "category": [
                    {
                        "coding": [
                            {
                                "system": "https://select.nextech-api.com/api/structuredefinition/note-category",
                                "code": "Prescriptions",
                                "display": "Prescriptions"
                            }
                        ],
                        "text": "Prescriptions"
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
                            "reference": "Encounter/6",
                            "display": "Encounter Name"
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

