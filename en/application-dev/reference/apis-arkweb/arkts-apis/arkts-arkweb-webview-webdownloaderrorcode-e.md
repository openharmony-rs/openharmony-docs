# WebDownloadErrorCode

Enumerates the download task error codes.

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## ERROR_UNKNOWN

```TypeScript
ERROR_UNKNOWN = 0
```

Unknown error.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_FAILED

```TypeScript
FILE_FAILED = 1
```

Failed to operate the file.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_ACCESS_DENIED

```TypeScript
FILE_ACCESS_DENIED = 2
```

No permission to access the file.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_NO_SPACE

```TypeScript
FILE_NO_SPACE = 3
```

The disk space is insufficient.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_NAME_TOO_LONG

```TypeScript
FILE_NAME_TOO_LONG = 5
```

The file name is too long.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_TOO_LARGE

```TypeScript
FILE_TOO_LARGE = 6
```

The file is too large.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_TRANSIENT_ERROR

```TypeScript
FILE_TRANSIENT_ERROR = 10
```

Some temporary issues occur, such as insufficient memory, files in use, and too many files open at the same time.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_BLOCKED

```TypeScript
FILE_BLOCKED = 11
```

Access to the file is blocked due to certain local policies.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_TOO_SHORT

```TypeScript
FILE_TOO_SHORT = 13
```

The file to resume downloading is not long enough. It may not exist.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_HASH_MISMATCH

```TypeScript
FILE_HASH_MISMATCH = 14
```

Hash mismatch.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## FILE_SAME_AS_SOURCE

```TypeScript
FILE_SAME_AS_SOURCE = 15
```

The file already exists.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_FAILED

```TypeScript
NETWORK_FAILED = 20
```

Common network error.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_TIMEOUT

```TypeScript
NETWORK_TIMEOUT = 21
```

Network connection timeout.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_DISCONNECTED

```TypeScript
NETWORK_DISCONNECTED = 22
```

Network disconnected.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_SERVER_DOWN

```TypeScript
NETWORK_SERVER_DOWN = 23
```

The server is shut down.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_INVALID_REQUEST

```TypeScript
NETWORK_INVALID_REQUEST = 24
```

Invalid network request. The request may be redirected to an unsupported scheme or an invalid URL.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_FAILED

```TypeScript
SERVER_FAILED = 30
```

The server returns a general error.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_NO_RANGE

```TypeScript
SERVER_NO_RANGE = 31
```

The server does not support the range request.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_BAD_CONTENT

```TypeScript
SERVER_BAD_CONTENT = 33
```

The server does not have the requested data.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_UNAUTHORIZED

```TypeScript
SERVER_UNAUTHORIZED = 34
```

The file cannot be downloaded from the server.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_CERT_PROBLEM

```TypeScript
SERVER_CERT_PROBLEM = 35
```

The server certificate is incorrect.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_FORBIDDEN

```TypeScript
SERVER_FORBIDDEN = 36
```

The access to the server is forbidden.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_UNREACHABLE

```TypeScript
SERVER_UNREACHABLE = 37
```

The server cannot be accessed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_CONTENT_LENGTH_MISMATCH

```TypeScript
SERVER_CONTENT_LENGTH_MISMATCH = 38
```

The received data does not match the content length.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_CROSS_ORIGIN_REDIRECT

```TypeScript
SERVER_CROSS_ORIGIN_REDIRECT = 39
```

An unexpected cross-site redirection occurs.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## USER_CANCELED

```TypeScript
USER_CANCELED = 40
```

The user cancels the download.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## USER_SHUTDOWN

```TypeScript
USER_SHUTDOWN = 41
```

The user closes the application.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## CRASH

```TypeScript
CRASH = 50
```

The application crashes.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
