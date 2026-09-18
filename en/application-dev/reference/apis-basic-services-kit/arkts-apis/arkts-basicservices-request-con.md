# Constants

## ERROR_CANNOT_RESUME

```TypeScript
const ERROR_CANNOT_RESUME: number
```

(Download error codes) Failure to resume the download due to network errors.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_DEVICE_NOT_FOUND

```TypeScript
const ERROR_DEVICE_NOT_FOUND: number
```

(Download error codes) Failure to find a storage device such as a memory card.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_FILE_ALREADY_EXISTS

```TypeScript
const ERROR_FILE_ALREADY_EXISTS: number
```

(Download error codes) Failure to download the file because it already exists.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_FILE_ERROR

```TypeScript
const ERROR_FILE_ERROR: number
```

(Download error codes) File operation failed.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_HTTP_DATA_ERROR

```TypeScript
const ERROR_HTTP_DATA_ERROR: number
```

(Download error codes) HTTP transmission failed.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_INSUFFICIENT_SPACE

```TypeScript
const ERROR_INSUFFICIENT_SPACE: number
```

(Download error codes) Insufficient storage space.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_OFFLINE

```TypeScript
const ERROR_OFFLINE: number
```

(Download error codes) No network connection.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## ERROR_TOO_MANY_REDIRECTS

```TypeScript
const ERROR_TOO_MANY_REDIRECTS: number
```

(Download error codes) Error caused by too many network redirections.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_UNHANDLED_HTTP_CODE

```TypeScript
const ERROR_UNHANDLED_HTTP_CODE: number
```

(Download error codes) Unidentified HTTP code.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_UNKNOWN

```TypeScript
const ERROR_UNKNOWN: number
```

(Download error codes) Unknown error.

In API version 12 or earlier, only serial connection to the IP addresses associated with the specified domain name is supported, and the connection time for a single IP address is not controllable. If the first IP address returned by the DNS is blocked, a handshake timeout may occur, leading to an ERROR_UNKNOWN error.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## ERROR_UNSUPPORTED_NETWORK_TYPE

```TypeScript
const ERROR_UNSUPPORTED_NETWORK_TYPE: number
```

(Download error codes) Network type mismatch.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## EXCEPTION_FILEIO

```TypeScript
const EXCEPTION_FILEIO: number
```

(Specific error codes) Abnormal file operation.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## EXCEPTION_FILEPATH

```TypeScript
const EXCEPTION_FILEPATH: number
```

(Specific error codes) Abnormal file path.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## EXCEPTION_OTHERS

```TypeScript
const EXCEPTION_OTHERS: number
```

(Specific error codes) Other errors.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## EXCEPTION_PARAMCHECK

```TypeScript
const EXCEPTION_PARAMCHECK: number
```

(Universal error codes) Parameter check failed.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## EXCEPTION_PERMISSION

```TypeScript
const EXCEPTION_PERMISSION: number
```

(Universal error codes) Permission verification failed.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## EXCEPTION_SERVICE

```TypeScript
const EXCEPTION_SERVICE: number
```

(Specific error codes) Abnormal service.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## EXCEPTION_UNSUPPORTED

```TypeScript
const EXCEPTION_UNSUPPORTED: number
```

(Universal error codes) The device does not support this API.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## NETWORK_MOBILE

```TypeScript
const NETWORK_MOBILE: number
```

(Network type) Bit flag download allowed on a mobile network.

**Type:** number

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## NETWORK_WIFI

```TypeScript
const NETWORK_WIFI: number
```

(Network type) Bit flag download allowed on a WLAN.

**Type:** number

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## PAUSED_BY_USER

```TypeScript
const PAUSED_BY_USER: number
```

(Causes of download pause) The user paused the session.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## PAUSED_QUEUED_FOR_WIFI

```TypeScript
const PAUSED_QUEUED_FOR_WIFI: number
```

(Causes of download pause) Download paused and queuing for a WLAN connection because the file size exceeds the maximum value allowed for a mobile network session.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## PAUSED_UNKNOWN

```TypeScript
const PAUSED_UNKNOWN: number
```

(Causes of download pause) Download paused due to unknown reasons.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## PAUSED_WAITING_FOR_NETWORK

```TypeScript
const PAUSED_WAITING_FOR_NETWORK: number
```

(Causes of download pause) Download paused due to a network connection problem.

Example: network disconnection

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## PAUSED_WAITING_TO_RETRY

```TypeScript
const PAUSED_WAITING_TO_RETRY: number
```

(Causes of download pause) Download paused due to network error and then retried.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## SESSION_FAILED

```TypeScript
const SESSION_FAILED: number
```

(Download task status codes) Download failure without retry.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## SESSION_PAUSED

```TypeScript
const SESSION_PAUSED: number
```

(Download task status codes) Download paused.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## SESSION_PENDING

```TypeScript
const SESSION_PENDING: number
```

(Download task status codes) Download pending.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## SESSION_RUNNING

```TypeScript
const SESSION_RUNNING: number
```

(Download task status codes) Download in progress.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## SESSION_SUCCESSFUL

```TypeScript
const SESSION_SUCCESSFUL: number
```

(Download task status codes) Successful download.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download
