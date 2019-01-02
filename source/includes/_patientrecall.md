# Patient-Recall

## Patient-Recall

### Overview

The patient recall resource contains information about patient recalls.

### Fields

| Name | Description | Type | Initial Version |
| ---- | ----------- | ---- | --------------- |
| resourcetype | The declaration of the type of resource this is. | [string](https://www.hl7.org/fhir/datatypes.html#string) | _14.1_ |
| id | The unique value assigned to each patient recall which discerns it from all others | [string](https://www.hl7.org/fhir/datatypes.html#string) | _14.1_ |
| extension - createddate| The created date as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |
| extension - recalldate| The (optional) recall date as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |
| extension - appointmentdate| The (optional) appointment date as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |
| extension - recallstatusid| The status id of the recall as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |
| extension - templatename| The template name as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |
| extension - stepname| The recall step name as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |
| extension - patient| The patient as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |
| extension - location| The (optional) location as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |
| extension - resources| The (optional) resources as a packaged extension. Contains definition url and value | [extension](https://www.hl7.org/fhir/extensibility.html) | _14.1_ |


### Sample
<pre class="center-column">
{
    "resourceType": "Bundle",
    "type": "searchset",
    "total": 41,
    "link": [
        {
            "relation": "self",
            "url": "http://localhost:57298/api/patient-recall"
        },
        {
            "relation": "next",
            "url": "http://localhost:57298/api/patient-recall?_getpagesoffset=10&_count=10"
        },
        {
            "relation": "first",
            "url": "http://localhost:57298/api/patient-recall?_getpagesoffset=0&_count=10"
        },
        {
            "relation": "last",
            "url": "http://localhost:57298/api/patient-recall?_getpagesoffset=31&_count=10"
        }
    ],
    "entry": [
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "55",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2013-05-16T11:25:54.43-04:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2013-08-16T00:00:00-04:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "3 Month Recall"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "3 Month"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/5008a671-c8e9-47b2-a031-33b5b155f710"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "56",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2013-11-05T12:51:46.307-05:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2014-11-05T00:00:00-05:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Annual Visit"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "12 month annual visit"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/e040b4a9-a855-4942-85bb-c11d5e5fbeee"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "57",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2013-11-05T12:54:16.48-05:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2014-11-05T00:00:00-05:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Annual Visit"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "12 month annual visit"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/e040b4a9-a855-4942-85bb-c11d5e5fbeee"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "58",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2013-11-05T12:54:34.97-05:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2014-11-05T00:00:00-05:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Annual Visit"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "12 month annual visit"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/e040b4a9-a855-4942-85bb-c11d5e5fbeee"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "59",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2013-11-19T16:46:21.937-05:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2013-12-03T00:00:00-05:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Skin Cancer"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "2 Week Followup"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/2f014922-6984-4cdf-80c0-ed1f0f5c18f0"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "60",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2013-12-11T17:34:10.427-05:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2013-12-25T00:00:00-05:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Skin Cancer"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "2 Week Followup"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/87cfc242-c7de-4d0a-90bd-0f9783c0b487"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "61",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2014-03-14T10:42:17.153-04:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2014-03-28T00:00:00-04:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Skin Cancer"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "2 Week Followup"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/1452de00-88d1-4f5e-abdb-d1c25f8eeb4a"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "62",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2014-07-30T09:32:56.867-04:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2014-08-13T00:00:00-04:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Skin Cancer"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "2 Week Followup"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/e409e81e-ae9c-48e2-858a-d97321344244"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "63",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2014-09-30T14:23:27.203-04:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2014-10-14T00:00:00-04:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Melissa Test"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "2 week follow up"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/1452de00-88d1-4f5e-abdb-d1c25f8eeb4a"
                            }
                        }
                    }
                ]
            }
        },
        {
            "resource": {
                "resourceType": "patient-recall",
                "id": "64",
                "extension": [
                    {
                        "id": "CreatedDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
                        "valueDateTime": "2014-10-20T13:32:55.237-04:00"
                    },
                    {
                        "id": "RecallDate",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
                        "valueDateTime": "2014-11-03T00:00:00-05:00"
                    },
                    {
                        "id": "RecallStatusID",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
                    },
                    {
                        "id": "TemplateName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
                        "valueString": "Skin Cancer"
                    },
                    {
                        "id": "StepName",
                        "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
                        "valueString": "2 Week Followup"
                    },
                    {
                        "id": "Patient",
                        "valueParticipantComponent": {
                            "actor": {
                                "reference": "Patient/53068d51-eae8-451a-8fd5-d06f33f6d208"
                            }
                        }
                    }
                ]
            }
        }
    ]
}</pre>
&nbsp;

### *Search*
Searches for all patient recalls matching the given search criteria. See [https://www.hl7.org/fhir/search.html](https://www.hl7.org/fhir/search.html) for instructions on formatting search criteria.

#### HTTP Request 
`GET /patient-recall?{parameters}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| identifier | query | The unique identifier for a single patient recall | N | _14.1_ |

#### Example: Get all patient recalls

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall
</pre>
&nbsp;

#### Example: Get a specific patient recall based on identifier

<pre class="center-column">
GET https://select.nextech-api.com/api/patient-recall/55
</pre>
#### Response
<pre class="center-column">
{
    "resourceType": "patient-recall",
    "id": "55",
    "extension": [
        {
            "id": "CreatedDate",
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#created-date",
            "valueDateTime": "2013-05-16T11:25:54.43-04:00"
        },
        {
            "id": "RecallDate",
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-date",
            "valueDateTime": "2013-08-16T00:00:00-04:00"
        },
        {
            "id": "RecallStatusID",
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#recall-status-id"
        },
        {
            "id": "TemplateName",
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#template-name",
            "valueString": "3 Month Recall"
        },
        {
            "id": "StepName",
            "url": "https://select.nextech-api.com/api/structuredefinition/patient-recall#step-name",
            "valueString": "3 Month"
        },
        {
            "id": "Patient",
            "valueParticipantComponent": {
                "actor": {
                    "reference": "Patient/5008a671-c8e9-47b2-a031-33b5b155f710"
                }
            }
        }
    ]
}
</pre>
&nbsp;
