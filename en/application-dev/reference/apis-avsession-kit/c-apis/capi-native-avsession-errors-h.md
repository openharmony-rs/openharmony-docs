# native_avsession_errors.h

## Overview

Declare avsession related error.

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-avsession-kit-ohavsession.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AVSession_ErrCode](#avsession_errcode) | AVSession_ErrCode | AVSession error code |
| [AVSessionCallback_Result](#avsessioncallback_result) | AVSessionCallback_Result | Defines enumeration of avsession callback result. |
| [AVMetadata_Result](#avmetadata_result) | AVMetadata_Result | AVMetadata error code |
| [AVQueueItem_Result](#avqueueitem_result) | AVQueueItem_Result | AVQUEUEITEM error code |

## Enum type description

### AVSession_ErrCode

```c
enum AVSession_ErrCode
```

**Description**

AVSession error code

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| AV_SESSION_ERR_SUCCESS = 0 | &nbsp;The operation completed successfully. |
| AV_SESSION_ERR_INVALID_PARAMETER = 401 | &nbsp;Invalid parameter. |
| AV_SESSION_ERR_SERVICE_EXCEPTION = 6600101 | &nbsp;Service exception. |
| AV_SESSION_ERR_CODE_SESSION_NOT_EXIST = 6600102 | &nbsp;The session does not exist. |
| AV_SESSION_ERR_CODE_COMMAND_INVALID = 6600105 | &nbsp;Invalid session command. |
| AV_SESSION_ERR_CODE_SESSION_INACTIVE = 6600106 | &nbsp;The session is not activated. |
| AV_SESSION_ERR_CODE_MESSAGE_OVERLOAD = 6600107 | &nbsp;Too many commands or events. |
| AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST = 6600109 | &nbsp;The remote connection is not established.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_UNSPECIFIED = 6611000 | The error code for cast control is unspecified.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_REMOTE_ERROR = 6611001 | An unspecified error occurs in the remote player.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_BEHIND_LIVE_WINDOW = 6611002 | The playback position falls behind the live window.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_TIMEOUT = 6611003 | The process of cast control times out.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_RUNTIME_CHECK_FAILED = 6611004 | The runtime check failed.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_PLAYER_NOT_WORKING = 6611100 | Cross-device data transmission is locked.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_SEEK_MODE_UNSUPPORTED = 6611101 | The specified seek mode is not supported.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_ILLEGAL_SEEK_TARGET = 6611102 | The position to seek to is out of the range of the media asset or the specified seek mode is not supported.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_PLAY_MODE_UNSUPPORTED = 6611103 | The specified playback mode is not supported.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_PLAY_SPEED_UNSUPPORTED = 6611104 | The specified playback speed is not supported.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_DEVICE_MISSING = 6611105 | The action failed because either the media source device or the media sink device has been revoked.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_INVALID_PARAM = 6611106 | The parameter is invalid, for example, the url is illegal to play.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_NO_MEMORY = 6611107 | Allocation of memory failed.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_OPERATION_NOT_ALLOWED = 6611108 | Operation is not allowed.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_UNSPECIFIED = 6612000 | An unspecified input/output error occurs.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NETWORK_CONNECTION_FAILED = 6612001 | Network connection failure.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NETWORK_CONNECTION_TIMEOUT = 6612002 | Network timeout.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_INVALID_HTTP_CONTENT_TYPE = 6612003 | Invalid "Content-Type" HTTP header.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_BAD_HTTP_STATUS = 6612004 | The HTTP server returns an unexpected HTTP response status code.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_FILE_NOT_FOUND = 6612005 | The file does not exist.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NO_PERMISSION = 6612006 | No permission is granted to perform the IO operation.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_CLEARTEXT_NOT_PERMITTED = 6612007 | Access to cleartext HTTP traffic is not allowed by the app's network security configuration.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_READ_POSITION_OUT_OF_RANGE = 6612008 | Reading data out of the data bound.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NO_CONTENTS = 6612100 | The media does not contain any contents that can be played.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_READ_ERROR = 6612101 | The media cannot be read, for example, because of dust or scratches.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_CONTENT_BUSY = 6612102 | This resource is already in use.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_CONTENT_EXPIRED = 6612103 | The content using the validity interval has expired.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_USE_FORBIDDEN = 6612104 | Using the requested content to play is not allowed.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NOT_VERIFIED = 6612105 | The use of the allowed content cannot be verified.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_EXHAUSTED_ALLOWED_USES = 6612106 | The number of times this content has been used as requested has reached the maximum allowed number of uses.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NETWORK_PACKET_SENDING_FAILED = 6612107 | An error occurs when sending packet from source device to sink device.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_UNSPECIFIED = 6613000 | Unspecified error related to content parsing.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_CONTAINER_MALFORMED = 6613001 | Parsing error associated with media container format bit streams.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_MANIFEST_MALFORMED = 6613002 | Parsing error associated with the media manifest.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_CONTAINER_UNSUPPORTED = 6613003 | An error occurs when attempting to extract a file with an unsupported media container format or an unsupported media container feature.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_MANIFEST_UNSUPPORTED = 6613004 | Unsupported feature in the media manifest.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_UNSPECIFIED = 6614000 | Unspecified decoding error.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_INIT_FAILED = 6614001 | Decoder initialization failed.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_QUERY_FAILED = 6614002 | Decoder query failed.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_FAILED = 6614003 | Decoding the media samples failed.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_FORMAT_EXCEEDS_CAPABILITIES = 6614004 | The format of the content to decode exceeds the capabilities of the device.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_FORMAT_UNSUPPORTED = 6614005 | The format of the content to decode is not supported.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_UNSPECIFIED = 6615000 | Unspecified errors related to the audio renderer.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_INIT_FAILED = 6615001 | Initializing the audio renderer failed.<br>**Since**: 23 |
| AV_SESSION_ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_WRITE_FAILED = 6615002 | The audio renderer fails to write data.<br>**Since**: 23 |

### AVSessionCallback_Result

```c
enum AVSessionCallback_Result
```

**Description**

Defines enumeration of avsession callback result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| AVSESSION_CALLBACK_RESULT_SUCCESS = 0 | Result of avsession callback is success. |
| AVSESSION_CALLBACK_RESULT_FAILURE = -1 | Result of avsession callback failed. |

### AVMetadata_Result

```c
enum AVMetadata_Result
```

**Description**

AVMetadata error code

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| AVMETADATA_SUCCESS = 0 | &nbsp;The call was successful. |
| AVMETADATA_ERROR_INVALID_PARAM = 1 | &nbsp;This means that the function was executed with an invalid input parameter. |
| AVMETADATA_ERROR_NO_MEMORY = 2 | &nbsp;This means there is no memory left. |

### AVQueueItem_Result

```c
enum AVQueueItem_Result
```

**Description**

AVQUEUEITEM error code

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 23

| Enum item | Description |
| -- | -- |
| AVQUEUEITEM_SUCCESS = 0 | &nbsp;The call was successful.<br>**Since**: 23 |
| AVQUEUEITEM_ERROR_INVALID_PARAM = 1 | &nbsp;This means that the function was executed with an invalid input parameter.<br>**Since**: 23 |
| AVQUEUEITEM_ERROR_NO_MEMORY = 2 | &nbsp;This means there is no memory left.<br>**Since**: 23 |


