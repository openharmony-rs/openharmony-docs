# AVErrorCode

```TypeScript
enum AVErrorCode
```

Enumerates the types of [Media error codes](../../../reference/apis-media-kit/errorcode-media.md).

**Since:** 9

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_OK

```TypeScript
AVERR_OK = 0
```

The operation is successful.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_NO_PERMISSION

```TypeScript
AVERR_NO_PERMISSION = 201
```

No permission to perform the operation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_INVALID_PARAMETER

```TypeScript
AVERR_INVALID_PARAMETER = 401
```

Invalid input parameter.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_UNSUPPORT_CAPABILITY

```TypeScript
AVERR_UNSUPPORT_CAPABILITY = 801
```

Unsupported API.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_NO_MEMORY

```TypeScript
AVERR_NO_MEMORY = 5400101
```

The system memory is insufficient or the number of services reaches the upper limit.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_OPERATE_NOT_PERMIT

```TypeScript
AVERR_OPERATE_NOT_PERMIT = 5400102
```

The operation is not allowed in the current state or you do not have the permission to perform the operation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO

```TypeScript
AVERR_IO = 5400103
```

The data stream is abnormal.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_TIMEOUT

```TypeScript
AVERR_TIMEOUT = 5400104
```

The system or network response times out.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_SERVICE_DIED

```TypeScript
AVERR_SERVICE_DIED = 5400105
```

The service process is dead.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_UNSUPPORT_FORMAT

```TypeScript
AVERR_UNSUPPORT_FORMAT = 5400106
```

The format of the media asset is not supported.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_AUDIO_INTERRUPTED

```TypeScript
AVERR_AUDIO_INTERRUPTED = 5400107
```

The audio focus is interrupted.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_HOST_NOT_FOUND

```TypeScript
AVERR_IO_HOST_NOT_FOUND = 5411001
```

Failed to parse the server address or connect to the server.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_CONNECTION_TIMEOUT

```TypeScript
AVERR_IO_CONNECTION_TIMEOUT = 5411002
```

Network connection times out.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_NETWORK_ABNORMAL

```TypeScript
AVERR_IO_NETWORK_ABNORMAL = 5411003
```

Data or links are abnormal due to network exceptions.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_NETWORK_UNAVAILABLE

```TypeScript
AVERR_IO_NETWORK_UNAVAILABLE = 5411004
```

The network is disabled.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_NO_PERMISSION

```TypeScript
AVERR_IO_NO_PERMISSION = 5411005
```

No access permission.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_REQUEST_DENIED

```TypeScript
AVERR_IO_REQUEST_DENIED = 5411006
```

The client request parameter is incorrect or exceeds the processing capability.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_RESOURCE_NOT_FOUND

```TypeScript
AVERR_IO_RESOURCE_NOT_FOUND = 5411007
```

No network resource is available.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_SSL_CLIENT_CERT_NEEDED

```TypeScript
AVERR_IO_SSL_CLIENT_CERT_NEEDED = 5411008
```

The server fails to verify the client certificate.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_SSL_CONNECTION_FAILED

```TypeScript
AVERR_IO_SSL_CONNECTION_FAILED = 5411009
```

The SSL connection fails.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_SSL_SERVER_CERT_UNTRUSTED

```TypeScript
AVERR_IO_SSL_SERVER_CERT_UNTRUSTED = 5411010
```

The client fails to verify the server certificate.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_UNSUPPORTED_REQUEST

```TypeScript
AVERR_IO_UNSUPPORTED_REQUEST = 5411011
```

The request is not supported due to a network protocol error.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_SEEK_CONTINUOUS_UNSUPPORTED

```TypeScript
AVERR_SEEK_CONTINUOUS_UNSUPPORTED = 5410002
```

The seek operation in SEEK_CONTINUOUS mode is not supported.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_SUPER_RESOLUTION_UNSUPPORTED

```TypeScript
AVERR_SUPER_RESOLUTION_UNSUPPORTED = 5410003
```

Super resolution is not supported.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_SUPER_RESOLUTION_NOT_ENABLED

```TypeScript
AVERR_SUPER_RESOLUTION_NOT_ENABLED = 5410004
```

Super resolution is not enabled.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_IO_CLEARTEXT_NOT_PERMITTED

```TypeScript
AVERR_IO_CLEARTEXT_NOT_PERMITTED = 5411012
```

HTTP plaintext access is not allowed.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Multimedia.Media.Core

## AVERR_PARAMETER_OUT_OF_RANGE

```TypeScript
AVERR_PARAMETER_OUT_OF_RANGE = 5400108
```

The parameter value is out of range.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.Media.Core
