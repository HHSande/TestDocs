# API design

## Asynchronous operations

The High Level API is a mix of synchronous and asynchronous operations.
Synchronous operations are operations that completes / finishes directly. When the client gets a response, processing has finished.
An example is the operation "Set home name".

Synchronous operations typically result in an `HTTP 200 OK`, `HTTP 201 Created` or `HTTP 204 No Content` response, depending on the contents of the response.

Asynchronous operations are operations that might take longer to process, so the client should not wait (block) for a result.
All operations involving the gateway are implemented as asynchronous requests, since the gateway might be offline or on an unstable network.
For asynchronous operations, the response code is `HTTP 202 Accepted`.

All HTTP operations are validated immediately, so if an asynchronous HTTP operation fails validation, then a HTTP 400 response is returned synchronously with error details.

For requests that pass validation and are sent for further processing, the default timeout (unless otherwise noted) for all asynchronous operations is 30 seconds, so the client should get either a success event or a timeout event in the event stream within that time frame.

## HTTP verbs

| Verb   | Usage                                                          |
| ------ | -------------------------------------------------------------- |
| GET    | Used to retrieve a resource                                    |
| POST   | Used to create a new resource or submit an operation           |
| PATCH  | Used to update an existing resource, including partial updates |
| PUT    | Used to update an existing resource                            |
| DELETE | Used to delete an existing resource                            |

## HTTP response codes

| <nobr>HTTP response code</nobr> | Description                                                                                                                                                                      |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200 OK                          | The request completed successfully.                                                                                                                                              |
| 201 Created                     | A new resource has been created successfully. The HTTP response will provide an identifier to the created resource (API operation dependant).                                    |
| 202 Accepted                    | Used for asynchronous operations. The request has been accepted for processing, but the processing has not been completed.                                                       |
| 204 No Content                  | An update to an existing resource has been applied successfully.                                                                                                                 |
| 400 Bad Request                 | The request was malformed or had content that did not pass validation. The response body will include an error providing further information.                                    |
| 401 Unauthorized                | Missing or invalid user HTTP Authentication credentials, or the user's email address has not been validated.                                                                     |
| 403 Forbidden                   | Valid user HTTP Authentication credentials, but user did not have access to resource (including not sufficient privileges to perform the operation on the resource in question). |
| 404 Not Found                   | The requested resource did not exist                                                                                                                                             |
| 409 Conflict                    | Another resource with conflicting parameters exists (i.e. uniqueness constraint violated).                                                                                       |

## Date format

All dates accepted and returned by the API are in <b>ISO 8601</b> format (example "2020-06-24T12:53:28.000+0000"). (???)
