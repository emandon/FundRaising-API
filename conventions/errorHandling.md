# Error handling

iBanFirst fundraising API uses conventional HTTP response codes to indicate success or failure of an API request. 
The body of the response contains more detailed information on the cause of the problem.

In general, the HTTP status code is indicative of where the problem occurred:

* Codes in the 200-299 range indicate success.
     * Unless otherwise specified, methods are expected to return 200 OK on success.
* Codes in the 400-499 range indicate that the request was invalid or incorrect somehow (e.g. a required parameter was missing, a trade failed, etc.). For example:
     * `400 Bad Request` occurs if the JSON body is malformed. This includes syntax errors as well as when invalid or mutually-exclusive options are selected.
     * `403 Forbidden` occurs if there is a problem with your authentication on the server.
     * `404 Not Found` occurs if the path specified does not exist, or does not support that method (for example, trying to POST to a URL that only serves GET requests)
* Codes in the 500-599 range indicate that the server experienced a problem. This could be due to a network outage or a bug in the software somewhere. For example:
     * `500 Internal Server Error` occurs when the server does not catch an error. This is always a bug. If you can reproduce the error, file it at our bug tracker in your FX4Biz platform.
     * `502 Bad Gateway` occurs if FX4Biz-REST could not contact its FX4Biz server at all.
     * `504 Gateway Timeout` occurs if the FX4Biz server took too long to respond to the FX4Biz-REST server.

When possible, the server provides a JSON response body with more information about the error. 

These responses contain the following fields:

| Parameter | Type	| Description |
|---------------|-------|-------------|
| Error	| Error Object | An object describing the error. |

