# Errors

Polis API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Business error that caused the request to fail like a validation error.
401 | Unauthorized -- API key is wrong.
403 | Forbidden -- API key does not have access to requested resource.
404 | Not Found -- The specified item could not be found.
405 | Method Not Allowed -- Method not supported for requested resource.
429 | Too Many Requests -- You're sending too many requests! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
