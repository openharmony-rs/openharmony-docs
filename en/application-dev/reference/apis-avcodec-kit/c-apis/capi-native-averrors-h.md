# native_averrors.h

## Overview

The file declares the error codes used by the media framework.

**Library**: libnative_media_core.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 9

**Related module**: [Core](capi-core.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVErrCode](#oh_averrcode) | OH_AVErrCode | Enumerates the error codes used by the media framework. |

## Enum type description

### OH_AVErrCode

```c
enum OH_AVErrCode
```

**Description**

Enumerates the error codes used by the media framework.

**Since**: 9

| Enum item | Description |
| -- | -- |
| AV_ERR_OK = 0 | the operation completed successfully.<br>**Since**: 9 |
| AV_ERR_NO_MEMORY = 1 | no memory.<br>**Since**: 9 |
| AV_ERR_OPERATE_NOT_PERMIT = 2 | operation not permitted.<br>**Since**: 9 |
| AV_ERR_INVALID_VAL = 3 | invalid argument.<br>**Since**: 9 |
| AV_ERR_IO = 4 | IO error.<br>**Since**: 9 |
| AV_ERR_TIMEOUT = 5 | network timeout.<br>**Since**: 9 |
| AV_ERR_UNKNOWN = 6 | unknown error.<br>**Since**: 9 |
| AV_ERR_SERVICE_DIED = 7 | media service died.<br>**Since**: 9 |
| AV_ERR_INVALID_STATE = 8 | the state is not support this operation.<br>**Since**: 9 |
| AV_ERR_UNSUPPORT = 9 | unsupport interface.<br>**Since**: 9 |
| AV_ERR_INPUT_DATA_ERROR = 10 | input data error.<br>**Since**: 12 |
| AV_ERR_UNSUPPORTED_FORMAT = 11 | unsupported format.<br>**Since**: 18 |
| AV_ERR_EXTEND_START = 100 | extend err start.<br>**Since**: 9 |
| AV_ERR_DRM_BASE = 200 | drm error base.<br>**Since**: 12 |
| AV_ERR_DRM_DECRYPT_FAILED = 201 | drm decrypt failed.<br>**Since**: 12 |
| AV_ERR_VIDEO_BASE = 300 | video error base.<br>**Since**: 12 |
| AV_ERR_VIDEO_UNSUPPORTED_COLOR_SPACE_CONVERSION = 301 | video unsupported color space conversion.<br>**Since**: 12 |
| AV_ERR_IO_CANNOT_FIND_HOST = 5411001 | can not find host, maybe the address of server is incorrect.<br>**Since**: 14 |
| AV_ERR_IO_CONNECTION_TIMEOUT = 5411002 | network connection timeout.<br>**Since**: 14 |
| AV_ERR_IO_NETWORK_ABNORMAL = 5411003 | failed link due to abnormal network.<br>**Since**: 14 |
| AV_ERR_IO_NETWORK_UNAVAILABLE = 5411004 | failed link due to unavailable network.<br>**Since**: 14 |
| AV_ERR_IO_NO_PERMISSION = 5411005 | network permission dennied.<br>**Since**: 14 |
| AV_ERR_IO_NETWORK_ACCESS_DENIED = 5411006 | the client request parameters are incorrect or exceed the processing capacity.<br>**Since**: 14 |
| AV_ERR_IO_RESOURCE_NOT_FOUND = 5411007 | cannot find available network resources.<br>**Since**: 14 |
| AV_ERR_IO_SSL_CLIENT_CERT_NEEDED = 5411008 | the server failed to verify the client certificate because the certificate is not carried, the certificate is invalid, or the certificate is expired.<br>**Since**: 14 |
| AV_ERR_IO_SSL_CONNECT_FAIL = 5411009 | the client failed to verify the server certificate because the certificate is not carried, the certificate is invalid, or the certificate is expired.<br>**Since**: 14 |
| AV_ERR_IO_SSL_SERVER_CERT_UNTRUSTED = 5411010 | SSL server cert untrusted.<br>**Since**: 14 |
| AV_ERR_IO_UNSUPPORTED_REQUEST = 5411011 | unsupported request due to network protocols.<br>**Since**: 14 |
| AV_ERR_IO_CLEARTEXT_NOT_PERMITTED = 5411012 | Http clear text not permitted.<br>**Since**: 23 |
| AV_ERR_STREAM_CHANGED = 5410005 | Signals a stream format change in synchronous mode. Required follow-up actions: - For video encoders: Call {@link OH_VideoEncoder_GetOutputDescription}<br> - For video decoders: Call {@link OH_VideoDecoder_GetOutputDescription}<br> - For audio decoders : Call {@link OH_AudioCodec_GetOutputDescription} to retrieve updated stream configuration.<br>**Since**: 20 |
| AV_ERR_TRY_AGAIN_LATER = 5410006 | Indicates temporary buffer query failure in synchronous mode, it's recommended to wait and retry the operation after a short interval.<br>**Since**: 20 |
| AV_ERR_SUPER_RESOLUTION_UNSUPPORTED = 5410003 | Super-resolution unsupported.<br>**Since**: 23 |
| AV_ERR_SUPER_RESOLUTION_NOT_ENABLED = 5410004 | No PlaybackStrategy set to enable super-resolution feature.<br>**Since**: 23 |


