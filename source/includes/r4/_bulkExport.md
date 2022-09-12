# Bulk Export

## Bulk FHIR Export [(Documentation)](http://hl7.org/fhir/uv/bulkdata/STU1.0.1/export/index.html)

### Overview
This functionality provides the ability for asynchronous generation of potentially large amounts of bulk data - whether that be all patients, a subset (defined group) of patients, or all available data contained in the FHIR server.

### *Bulk Data Kick-off request*
Allows for the generation of bulk data in one of three different formats: all patients, a subset of patients within a defined group, or all available data contained in the FHIR server.

## All Patients

#### HTTP Request 
`GET /r4/Patient/$export?{parameters}` 

#### HTTP Headers 
| Name | Value | Description | Required |
| ---- | ----- | ----------- | -------- |
| Accept | `application/fhir+json` | Specifies the format of the optional OperationOutcome resource response to the kick-off request | Yes |
| Prefer | `respond-async` | Specifies whether the response is immediate or asynchronous | Yes |

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _outputFormat | query | The format for the requested bulk data files to be generated as per the [FHIR Asynchronous Request Pattern](http://hl7.org/fhir/async.html). Defaults to `application/fhir+ndjson`, but also supports `application/ndjson` and `ndjson` abbreviated representations| No | _16.9_ |
| _since | query | Resources will be included in the response if their state has changed after the supplied time (e.g. if `Resource.meta.lastUpdated` is later than the supplied `_since` time) | No | _16.9_ |
| _type | query | String of comma-delimited FHIR R4 resource types (example: `Patient,MedicationRequest`). All supported resources are returned if this parameter is not provided | No | _16.9_ |

#### HTTP Response
A successful kick-off request will return a response with a `202 Accepted` HTTP status code, along with a `Content-Location` reponse header containing the absolute URL of the endpoint that must be used for subsequent status requests (polling location), which will be located at `https://select.nextech-api.com/api/r4/Export/{ExportJobID}`. See below for the usage of this polling endpoint.
A failed kick-off request will return a response with either a `4XX` or `5XX` range status code, along with a JSON response body containing a FHIR `OperationOutCome` resource describing the error that occurred.

#### Example: Start an export of all patients

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Patient/$export
</pre>
&nbsp;

## All Patients within a group

#### HTTP Request 
`GET /r4/Group/{GroupID}/$export?{parameters}` 

#### HTTP Headers 
| Name | Value | Description | Required |
| ---- | ----- | ----------- | -------- |
| Accept | `application/fhir+json` | Specifies the format of the optional OperationOutcome resource response to the kick-off request | Yes |
| Prefer | `respond-async` | Specifies whether the response is immediate or asynchronous | Yes |

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| GroupID | path | ID of the group of patients to export | Yes | _16.9_ |
| _outputFormat | query | The format for the requested bulk data files to be generated as per the [FHIR Asynchronous Request Pattern](http://hl7.org/fhir/async.html). Defaults to `application/fhir+ndjson`, but also supports `application/ndjson` and `ndjson` abbreviated representations| No | _16.9_ |
| _since | query | Resources will be included in the response if their state has changed after the supplied time (e.g. if `Resource.meta.lastUpdated` is later than the supplied `_since` time) | No | _16.9_ |
| _type | query | String of comma-delimited FHIR R4 resource types (example: `Patient,MedicationRequest`). All supported resources are returned if this parameter is not provided | No | _16.9_ |

#### HTTP Response
A successful kick-off request will return a response with a `202 Accepted` HTTP status code, along with a `Content-Location` reponse header containing the absolute URL of the endpoint that must be used for subsequent status requests (polling location), which will be located at `https://select.nextech-api.com/api/r4/Export/{ExportJobID}`. See below for the usage of this polling endpoint.
A failed kick-off request will return a response with either a `4XX` or `5XX` range status code, along with a JSON response body containing a FHIR `OperationOutCome` resource describing the error that occurred.

#### Example: Start an export of all patients within the group with an ID of "1"

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Group/1/$export
</pre>
&nbsp;

## System level export

#### HTTP Request 
`GET /r4/$export?{parameters}` 

#### HTTP Headers 
| Name | Value | Description | Required |
| ---- | ----- | ----------- | -------- |
| Accept | `application/fhir+json` | Specifies the format of the optional OperationOutcome resource response to the kick-off request | Yes |
| Prefer | `respond-async` | Specifies whether the response is immediate or asynchronous | Yes |

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| _outputFormat | query | The format for the requested bulk data files to be generated as per the [FHIR Asynchronous Request Pattern](http://hl7.org/fhir/async.html). Defaults to `application/fhir+ndjson`, but also supports `application/ndjson` and `ndjson` abbreviated representations| No | _16.9_ |
| _since | query | Resources will be included in the response if their state has changed after the supplied time (e.g. if `Resource.meta.lastUpdated` is later than the supplied `_since` time) | No | _16.9_ |
| _type | query | String of comma-delimited FHIR R4 resource types (example: `Patient,MedicationRequest`). All supported resources are returned if this parameter is not provided | No | _16.9_ |

#### HTTP Response
A successful kick-off request will return a response with a `202 Accepted` HTTP status code, along with a `Content-Location` reponse header containing the absolute URL of the endpoint that must be used for subsequent status requests (polling location), which will be located at `https://select.nextech-api.com/api/r4/Export/{ExportJobID}`. See below for the usage of this polling endpoint.
A failed kick-off request will return a response with either a `4XX` or `5XX` range status code, along with a JSON response body containing a FHIR `OperationOutCome` resource describing the error that occurred.

#### Example: Start an export of all allowed FHIR resources

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/$export
</pre>
&nbsp;

## Poll export content location

#### HTTP Request 
`GET /r4/Export/{ExportJobID}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| ExportJobID | path | ID of the export job to poll the status of. Returned in the `Content-Location` HTTP header in the HTTP response to the kick-off request | Yes | _16.9_ |

#### HTTP Response
An export job can be in one of three states: `In-Progress`, `Error`, and `Complete`, and has the following types of responses for those states:
##### In-Progress
Returned by the server while it is processing the $export request. 
The `X-Progress` HTTP response header gives an indication of how far along the export is, as a percentage. 
The `Retry-After` HTTP response header gives a delay time in seconds indicating the amount of time to wait before making another polling request to this endpoint.
&nbsp;
<pre class="center-column">
Status: 202 Accepted
X-Progress: “50% complete”
Retry-After: 120
</pre>
&nbsp;

##### Error
Returned by the server if the export operation fails. 
A description of the error is in the `OperationOutcome.Text` member of the FHIR JSON response. The below is an example of a timeout error.
&nbsp;
<pre class="center-column">
Status: 500 Internal Server Error
Content-Type: application/json

{
 "resourceType": "OperationOutcome",
 "id": "1",
 "issue": [
  {
   "severity": "error",
   "code": "processing",
   "details": {
    "text": "An internal timeout has occurred"
   }
  }
 ]
}
</pre>
&nbsp;

##### Complete
Returned by the server when the export operation has completed. Below is an example response for when this endpoint is polled and the requested export job (filtered to the `Patient` and `Observation` FHIR resources, in this example) has completed. 
The `Expires` HTTP response header indicates when the files in the response will no longer be available for access.
The `transactionTime` member in the JSON response body indicates the server's time when the query is run.
The `request` member in the JSON response body is the full URL of the original bulk data kick-off request.
The `requiresAccessToken` member in the JSON response body indicates whether an OAuth 2.0 bearer token is required to access the indicated export files.
The `output` array member in the JSON response body indicates both each exported FHIR resource `type` and the `url` containing the exported `.ndjson` file for that resource.
The `error` array member in the JSON response body indicates each error file detailing error(s) that were encountered during the export.
&nbsp;
<pre class="center-column">
Status: 200 OK
Expires: Mon, 22 Jul 2019 23:59:59 GMT
Content-Type: application/json

{
 "transactionTime": "2021-01-01T00:00:00Z",
 "request" : "https://select.nextech-api.com/api/r4/Patient/$export?_type=Patient,Observation",
 "requiresAccessToken" : false,
 "output" : [{
  "type" : "Patient",
  "url" : "https://storagesample.blob.core.windows.net/sampleoutput/patient_file_1.ndjson"
 },{
  "type" : "Patient",
  "url" : "https://storagesample.blob.core.windows.net/sampleoutput/patient_file_2.ndjson"
 },{
  "type" : "Observation",
  "url" : "https://storagesample.blob.core.windows.net/sampleoutput/observation_file_1.ndjson"
 }],
 "error" : [{
  "type" : "OperationOutcome",
  "url" : "https://storagesample.blob.core.windows.net/sampleoutput/err_file_1.ndjson"
 }]
 }
</pre>
&nbsp;

#### Example: Poll the status of an export job with an ID of "61b05fbe-6b5f-4b68-aec4-c03d09f51e82"

<pre class="center-column">
GET https://select.nextech-api.com/api/r4/Export/61b05fbe-6b5f-4b68-aec4-c03d09f51e82
</pre>
&nbsp;

## Cancel export job

#### HTTP Request 
`DELETE /r4/Export/{ExportJobID}`

#### Parameters
| Name | Located in | Description | Required | Initial Version |
| ---- | ---------- | ----------- | -------- | --------------- |
| ExportJobID | path | ID of the export job to cancel. Returned in the `Content-Location` HTTP header in the HTTP response to the kick-off request | Yes | _16.9_ |

#### Example: Cancel an export job with an ID of "61b05fbe-6b5f-4b68-aec4-c03d09f51e82"

<pre class="center-column">
DELETE https://select.nextech-api.com/api/r4/Export/61b05fbe-6b5f-4b68-aec4-c03d09f51e82
</pre>
&nbsp;