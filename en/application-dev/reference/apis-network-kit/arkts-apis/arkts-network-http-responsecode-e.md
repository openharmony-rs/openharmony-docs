# ResponseCode

Enumerates the response codes for an HTTP request.

**Since:** 6

**System capability:** SystemCapability.Communication.NetStack

## OK

```TypeScript
OK = 200
```

The request is successful. This return code is generally used for GET and POST requests.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## CREATED

```TypeScript
CREATED = 201
```

"Created." The request has been successfully sent and a new resource is created.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## ACCEPTED

```TypeScript
ACCEPTED = 202
```

"Accepted." The request has been accepted for processing, but the processing has not been completed.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## NOT_AUTHORITATIVE

```TypeScript
NOT_AUTHORITATIVE = 203
```

"Non-Authoritative Information." The request is successful.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## NO_CONTENT

```TypeScript
NO_CONTENT = 204
```

"No Content." The server has successfully fulfilled the request but there is no additional content to send in the response payload body.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## RESET

```TypeScript
RESET = 205
```

"Reset Content." The server has successfully fulfilled the request and desires that the user agent reset the content.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## PARTIAL

```TypeScript
PARTIAL = 206
```

"Partial Content." The server has successfully fulfilled the partial GET request for a given resource.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## MULT_CHOICE

```TypeScript
MULT_CHOICE = 300
```

"Multiple Choices." The requested resource corresponds to any one of a set of representations.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## MOVED_PERM

```TypeScript
MOVED_PERM = 301
```

"Moved Permanently." The requested resource has been assigned a new permanent URI and any future references to this resource will be redirected to this URI.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## MOVED_TEMP

```TypeScript
MOVED_TEMP = 302
```

"Moved Temporarily." The requested resource is moved temporarily to a different URI.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## SEE_OTHER

```TypeScript
SEE_OTHER = 303
```

"See Other." The response to the request can be found under a different URI.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## NOT_MODIFIED

```TypeScript
NOT_MODIFIED = 304
```

"Not Modified." The client has performed a conditional GET request and access is allowed, but the content has not been modified.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## USE_PROXY

```TypeScript
USE_PROXY = 305
```

"Use Proxy." The requested resource can only be accessed through the proxy.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## BAD_REQUEST

```TypeScript
BAD_REQUEST = 400
```

"Bad Request." The request could not be understood by the server due to incorrect syntax.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## UNAUTHORIZED

```TypeScript
UNAUTHORIZED = 401
```

"Unauthorized." The request requires user authentication.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## PAYMENT_REQUIRED

```TypeScript
PAYMENT_REQUIRED = 402
```

"Payment Required." This code is reserved for future use.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## FORBIDDEN

```TypeScript
FORBIDDEN = 403
```

"Forbidden." The server understands the request but refuses to process it.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## NOT_FOUND

```TypeScript
NOT_FOUND = 404
```

"Not Found." The server does not find anything matching the Request-URI.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## BAD_METHOD

```TypeScript
BAD_METHOD = 405
```

"Method Not Allowed." The method specified in the request is not allowed for the resource identified by the Request-URI.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## NOT_ACCEPTABLE

```TypeScript
NOT_ACCEPTABLE = 406
```

"Not Acceptable." The server cannot fulfill the request according to the content characteristics of the request.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## PROXY_AUTH

```TypeScript
PROXY_AUTH = 407
```

"Proxy Authentication Required." The request requires user authentication with the proxy.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## CLIENT_TIMEOUT

```TypeScript
CLIENT_TIMEOUT = 408
```

"Request Timeout." The client fails to generate a request within the timeout period.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## CONFLICT

```TypeScript
CONFLICT = 409
```

"Conflict." The request cannot be fulfilled due to a conflict with the current state of the resource. Conflicts are most likely to occur in response to a PUT request.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## GONE

```TypeScript
GONE = 410
```

"Gone." The requested resource has been deleted permanently and is no longer available.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## LENGTH_REQUIRED

```TypeScript
LENGTH_REQUIRED = 411
```

"Length Required." The server refuses to process the request without a defined Content-Length.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## PRECON_FAILED

```TypeScript
PRECON_FAILED = 412
```

"Precondition Failed." The precondition in the request is incorrect.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## ENTITY_TOO_LARGE

```TypeScript
ENTITY_TOO_LARGE = 413
```

"Request Entity Too Large." The server refuses to process a request because the request entity is larger than the server is able to process.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## REQ_TOO_LONG

```TypeScript
REQ_TOO_LONG = 414
```

"Request-URI Too Long." The Request-URI is too long for the server to process.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## UNSUPPORTED_TYPE

```TypeScript
UNSUPPORTED_TYPE = 415
```

"Unsupported Media Type." The server is unable to process the media format in the request.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## RANGE_NOT_SATISFIABLE

```TypeScript
RANGE_NOT_SATISFIABLE = 416
```

"Range Not Satisfiable." The server cannot serve the requested ranges.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NetStack

## INTERNAL_ERROR

```TypeScript
INTERNAL_ERROR = 500
```

"Internal Server Error." The server encounters an unexpected error that prevents it from fulfilling the request.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## NOT_IMPLEMENTED

```TypeScript
NOT_IMPLEMENTED = 501
```

"Not Implemented." The server does not support the function required to fulfill the request.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## BAD_GATEWAY

```TypeScript
BAD_GATEWAY = 502
```

"Bad Gateway." The server acting as a gateway or proxy receives an invalid response from the upstream server.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## UNAVAILABLE

```TypeScript
UNAVAILABLE = 503
```

"Service Unavailable." The server is currently unable to process the request due to a temporary overload or system maintenance.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## GATEWAY_TIMEOUT

```TypeScript
GATEWAY_TIMEOUT = 504
```

"Gateway Timeout." The server acting as a gateway or proxy does not receive requests from the remote server within the timeout period.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## VERSION

```TypeScript
VERSION = 505
```

The server does not support the HTTP protocol version used in the client request.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack
