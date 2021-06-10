# Errors

## HTTP Status Codes

We use common HTTP status codes included in the response header to indicate success or failure.

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The data requested is hidden for administrators only.
404 | Not Found -- The specified data could not be found.
405 | Method Not Allowed -- You tried to access a data with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The data requested has been removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many datas! Slow down!
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