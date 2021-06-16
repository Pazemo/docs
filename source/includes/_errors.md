# Errors

## HTTP Status Codes

We use common HTTP status codes included in the response header to indicate success or failure.

Error Code | Meaning
---------- | -------
200 | OK -- Everything worked as expected..
400 | Bad Request -- The request was unacceptable, often due to missing a required parameter.
401 | Unauthorized -- Your API key is wrong.
402 | Request Failed -- The parameters were valid but the request failed.
403 | Forbidden -- The data requested is hidden for administrators only.
404 | Not Found -- The specified data could not be found.
409 | Conflict -- The request conflicts with another request (perhaps due to using the same idempotent key).
410 | Gone -- The data requested has been removed from our servers.
429 | Too Many Requests -- Too many requests hit the API too quickly. We recommend an exponential backoff of your requests.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

## Validation Errors

>Example Validation Error:

```json
{
    "errors": [
        {
            "code": "error.route.not.supported",
            "message": "This route is not supported",
            "arguments": [
                "CNY-EUR"
            ]
        }
    ]
}
```

Data validation or violation of business rules related errors. Response could contain multiple errors.

## Authentication Errors

>Example Authentication Error:

```json
{
    "error": "unauthorized",
    "error_description": "Full authentication is required to access this resource"
}
```

Security related errors.

## System Errors

>Example System Error:

```json
{
  "timestamp": "2017-02-02T13:07:39.644+0000",
  "status": 500,
  "error": "Internal Server Error",
  "exception": "java.lang.NullPointerException",
  "message": "No message available",
  "path": "/v1/quotes/0b63b0cb-2041-4bc4-b3fc-1e51a1454a1b/account-requirements"
}
```

Something went wrong in our side.