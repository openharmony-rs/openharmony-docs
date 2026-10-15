# WebDownloadErrorCode

```TypeScript
enum WebDownloadErrorCode
```

Enumerates the download task error codes.

**Since:** 11

<!--Device-webview-enum WebDownloadErrorCode--><!--Device-webview-enum WebDownloadErrorCode-End-->

**System capability:** SystemCapability.Web.Webview.Core

## CRASH

```TypeScript
CRASH = 50
```

The application crashes.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-CRASH = 50--><!--Device-WebDownloadErrorCode-CRASH = 50-End-->

**System capability:** SystemCapability.Web.Webview.Core

## ERROR_UNKNOWN

```TypeScript
ERROR_UNKNOWN = 0
```

Unknown error.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-ERROR_UNKNOWN = 0--><!--Device-WebDownloadErrorCode-ERROR_UNKNOWN = 0-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_ACCESS_DENIED

```TypeScript
FILE_ACCESS_DENIED = 2
```

No permission to access the file.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_ACCESS_DENIED = 2--><!--Device-WebDownloadErrorCode-FILE_ACCESS_DENIED = 2-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_BLOCKED

```TypeScript
FILE_BLOCKED = 11
```

Access to the file is blocked due to certain local policies.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_BLOCKED = 11--><!--Device-WebDownloadErrorCode-FILE_BLOCKED = 11-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_FAILED

```TypeScript
FILE_FAILED = 1
```

Failed to operate the file.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_FAILED = 1--><!--Device-WebDownloadErrorCode-FILE_FAILED = 1-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_HASH_MISMATCH

```TypeScript
FILE_HASH_MISMATCH = 14
```

Hash mismatch.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_HASH_MISMATCH = 14--><!--Device-WebDownloadErrorCode-FILE_HASH_MISMATCH = 14-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_NAME_TOO_LONG

```TypeScript
FILE_NAME_TOO_LONG = 5
```

The file name is too long.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_NAME_TOO_LONG = 5--><!--Device-WebDownloadErrorCode-FILE_NAME_TOO_LONG = 5-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_NO_SPACE

```TypeScript
FILE_NO_SPACE = 3
```

The disk space is insufficient.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_NO_SPACE = 3--><!--Device-WebDownloadErrorCode-FILE_NO_SPACE = 3-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_SAME_AS_SOURCE

```TypeScript
FILE_SAME_AS_SOURCE = 15
```

The file already exists.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_SAME_AS_SOURCE = 15--><!--Device-WebDownloadErrorCode-FILE_SAME_AS_SOURCE = 15-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_TOO_LARGE

```TypeScript
FILE_TOO_LARGE = 6
```

The file is too large.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_TOO_LARGE = 6--><!--Device-WebDownloadErrorCode-FILE_TOO_LARGE = 6-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_TOO_SHORT

```TypeScript
FILE_TOO_SHORT = 13
```

The file to resume downloading is not long enough. It may not exist.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_TOO_SHORT = 13--><!--Device-WebDownloadErrorCode-FILE_TOO_SHORT = 13-End-->

**System capability:** SystemCapability.Web.Webview.Core

## FILE_TRANSIENT_ERROR

```TypeScript
FILE_TRANSIENT_ERROR = 10
```

Some temporary issues occur, such as insufficient memory, files in use, and too many files open at the same time.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-FILE_TRANSIENT_ERROR = 10--><!--Device-WebDownloadErrorCode-FILE_TRANSIENT_ERROR = 10-End-->

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_DISCONNECTED

```TypeScript
NETWORK_DISCONNECTED = 22
```

Network disconnected.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-NETWORK_DISCONNECTED = 22--><!--Device-WebDownloadErrorCode-NETWORK_DISCONNECTED = 22-End-->

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_FAILED

```TypeScript
NETWORK_FAILED = 20
```

Common network error.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-NETWORK_FAILED = 20--><!--Device-WebDownloadErrorCode-NETWORK_FAILED = 20-End-->

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_INVALID_REQUEST

```TypeScript
NETWORK_INVALID_REQUEST = 24
```

Invalid network request. The request may be redirected to an unsupported scheme or an invalid URL.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-NETWORK_INVALID_REQUEST = 24--><!--Device-WebDownloadErrorCode-NETWORK_INVALID_REQUEST = 24-End-->

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_SERVER_DOWN

```TypeScript
NETWORK_SERVER_DOWN = 23
```

The server is shut down.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-NETWORK_SERVER_DOWN = 23--><!--Device-WebDownloadErrorCode-NETWORK_SERVER_DOWN = 23-End-->

**System capability:** SystemCapability.Web.Webview.Core

## NETWORK_TIMEOUT

```TypeScript
NETWORK_TIMEOUT = 21
```

Network connection timeout.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-NETWORK_TIMEOUT = 21--><!--Device-WebDownloadErrorCode-NETWORK_TIMEOUT = 21-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_BAD_CONTENT

```TypeScript
SERVER_BAD_CONTENT = 33
```

The server does not have the requested data.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_BAD_CONTENT = 33--><!--Device-WebDownloadErrorCode-SERVER_BAD_CONTENT = 33-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_CERT_PROBLEM

```TypeScript
SERVER_CERT_PROBLEM = 35
```

The server certificate is incorrect.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_CERT_PROBLEM = 35--><!--Device-WebDownloadErrorCode-SERVER_CERT_PROBLEM = 35-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_CONTENT_LENGTH_MISMATCH

```TypeScript
SERVER_CONTENT_LENGTH_MISMATCH = 38
```

The received data does not match the content length.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_CONTENT_LENGTH_MISMATCH = 38--><!--Device-WebDownloadErrorCode-SERVER_CONTENT_LENGTH_MISMATCH = 38-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_CROSS_ORIGIN_REDIRECT

```TypeScript
SERVER_CROSS_ORIGIN_REDIRECT = 39
```

An unexpected cross-site redirection occurs.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_CROSS_ORIGIN_REDIRECT = 39--><!--Device-WebDownloadErrorCode-SERVER_CROSS_ORIGIN_REDIRECT = 39-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_FAILED

```TypeScript
SERVER_FAILED = 30
```

The server returns a general error.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_FAILED = 30--><!--Device-WebDownloadErrorCode-SERVER_FAILED = 30-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_FORBIDDEN

```TypeScript
SERVER_FORBIDDEN = 36
```

The access to the server is forbidden.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_FORBIDDEN = 36--><!--Device-WebDownloadErrorCode-SERVER_FORBIDDEN = 36-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_NO_RANGE

```TypeScript
SERVER_NO_RANGE = 31
```

The server does not support the range request.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_NO_RANGE = 31--><!--Device-WebDownloadErrorCode-SERVER_NO_RANGE = 31-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_UNAUTHORIZED

```TypeScript
SERVER_UNAUTHORIZED = 34
```

The file cannot be downloaded from the server.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_UNAUTHORIZED = 34--><!--Device-WebDownloadErrorCode-SERVER_UNAUTHORIZED = 34-End-->

**System capability:** SystemCapability.Web.Webview.Core

## SERVER_UNREACHABLE

```TypeScript
SERVER_UNREACHABLE = 37
```

The server cannot be accessed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-SERVER_UNREACHABLE = 37--><!--Device-WebDownloadErrorCode-SERVER_UNREACHABLE = 37-End-->

**System capability:** SystemCapability.Web.Webview.Core

## USER_CANCELED

```TypeScript
USER_CANCELED = 40
```

The user cancels the download.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-USER_CANCELED = 40--><!--Device-WebDownloadErrorCode-USER_CANCELED = 40-End-->

**System capability:** SystemCapability.Web.Webview.Core

## USER_SHUTDOWN

```TypeScript
USER_SHUTDOWN = 41
```

The user closes the application.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WebDownloadErrorCode-USER_SHUTDOWN = 41--><!--Device-WebDownloadErrorCode-USER_SHUTDOWN = 41-End-->

**System capability:** SystemCapability.Web.Webview.Core
