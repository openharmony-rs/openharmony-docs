# native_avsession_errors.h
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

## Overview

The file declares the playback control error codes.

**File to include**: <multimedia/av_session/native_avsession_errors.h>

**Library**: libohavsession.so

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Since**: 13

**Related module**: [OHAVSession](capi-ohavsession.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AVSession_ErrCode](#avsession_errcode) | AVSession_ErrCode | Enumerates the playback control error codes.|
| [AVSessionCallback_Result](#avsessioncallback_result) | AVSessionCallback_Result | Enumerates the audio and video session callback results.|
| [AVMetadata_Result](#avmetadata_result) | AVMetadata_Result | Enumerates the playback control metadata error codes.|
| [AVQueueItem_Result](#avqueueitem_result) | AVQueueItem_Result | Enumerates the error codes of an item in the queue.|

## Enums

### AVSession_ErrCode

```c
enum AVSession_ErrCode
```

**Description**

Enumerates the playback control error codes.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| AV_SESSION_ERR_SUCCESS = 0 | The operation is successful.|
| AV_SESSION_ERR_INVALID_PARAMETER = 401 | Parameter check fails.|
| AV_SESSION_ERR_SERVICE_EXCEPTION = 6600101 | The session server is abnormal.|
| AV_SESSION_ERR_CODE_SESSION_NOT_EXIST = 6600102 | The session does not exist.|
| AV_SESSION_ERR_CODE_COMMAND_INVALID = 6600105 | The session command is invalid.|
| AV_SESSION_ERR_CODE_SESSION_INACTIVE = 6600106 | The session is not activated.|
| AV_SESSION_ERR_CODE_MESSAGE_OVERLOAD = 6600107 | Too many commands or messages.|
| AV_SESSION_ERR_CODE_REMOTE_CONNECTION_NOT_EXIST = 6600109 |  The remote session does not exist.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_UNSPECIFIED = 6611000 |  An unknown error occurs in the casting controller.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_REMOTE_ERROR = 6611001 |  An unknown error occurs in the remote device.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_BEHIND_LIVE_WINDOW = 6611002 |  The loaded progress exceeds the total progress of the cast video.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_TIMEOUT = 6611003 |  The loading of the casting controller times out.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_RUNTIME_CHECK_FAILED = 6611004 |  The runtime check fails.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_PLAYER_NOT_WORKING = 6611100 |  Cross-device data transmission is locked.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_SEEK_MODE_UNSUPPORTED = 6611101 |  The specified seek mode is not supported.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_ILLEGAL_SEEK_TARGET = 6611102 |  The seek position is out of bounds or the seek mode is abnormal.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_PLAY_MODE_UNSUPPORTED = 6611103 |  The specified playback mode is not supported.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_PLAY_SPEED_UNSUPPORTED = 6611104 |  The specified playback speed is not supported.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_DEVICE_MISSING = 6611105 |  Operation failed because the media receiver is offline.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_INVALID_PARAM = 6611106 |  The parameter is invalid. For example, the playback URL is invalid.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_NO_MEMORY = 6611107 |  Memory allocation failed.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_OPERATION_NOT_ALLOWED = 6611108 |  The operation is not allowed.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_UNSPECIFIED = 6612000 |  Unknown input/output error.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NETWORK_CONNECTION_FAILED = 6612001 |  Network connection failed.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NETWORK_CONNECTION_TIMEOUT = 6612002 |  Network connection timeout.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_INVALID_HTTP_CONTENT_TYPE = 6612003 |  The **Content-Type** field in the HTTP request header is invalid.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_BAD_HTTP_STATUS = 6612004 |  The HTTP server returns an abnormal HTTP response status code.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_FILE_NOT_FOUND = 6612005 |  The file does not exist.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NO_PERMISSION = 6612006 |  The permission to perform I/O operations is missing.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_CLEARTEXT_NOT_PERMITTED = 6612007 |  This operation is not allowed by the network security configuration.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_READ_POSITION_OUT_OF_RANGE = 6612008 |  The data to read exceeds the data range.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NO_CONTENTS = 6612100 |  No media resources are available for playback.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_READ_ERROR = 6612101 |  The media cannot be read. For example, the storage medium is dusty or scratched.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_CONTENT_BUSY = 6612102 |  The resource is being used.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_CONTENT_EXPIRED = 6612103 |  The content has expired.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_USE_FORBIDDEN = 6612104 |  Using the requested content is not allowed.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NOT_VERIFIED = 6612105 |  The permission to use the authorized content cannot be verified.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_EXHAUSTED_ALLOWED_USES = 6612106 |  The number of on-demand requests for using the media content has reached the maximum allowed by the system.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_IO_NETWORK_PACKET_SENDING_FAILED = 6612107 |  The local device fails to send resource packages to the remote device.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_UNSPECIFIED = 6613000 |  An undefined error occurs during media content parsing.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_CONTAINER_MALFORMED = 6613001 |  An error occurs when the media container format stream is parsed.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_MANIFEST_MALFORMED = 6613002 |  An error occurs when the media list is parsed.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_CONTAINER_UNSUPPORTED = 6613003 |  Failed to extract the file because the media container format is not supported.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_PARSING_MANIFEST_UNSUPPORTED = 6613004 |  The media cannot be read. For example, the media is dusty or scratched.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_UNSPECIFIED = 6614000 |  An unknown decoding error occurs.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_INIT_FAILED = 6614001 |  Initializing the decoder fails.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_QUERY_FAILED = 6614002 |  Querying the decoder fails.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_FAILED = 6614003 |  Decoding the media sample fails.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_FORMAT_EXCEEDS_CAPABILITIES = 6614004 |  The number of content requests reaches the maximum.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_DECODING_FORMAT_UNSUPPORTED = 6614005 |  The content format is not supported for decoding.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_UNSPECIFIED = 6615000 |  An unknown error occurs in the audio renderer.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_INIT_FAILED = 6615001 |  An exception occurs during audio renderer initialization.<br>**Since**: 23|
| AV_SESSION_ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_WRITE_FAILED = 6615002 |  An exception occurs when the audio renderer writes data.<br>**Since**: 23|

### AVSessionCallback_Result

```c
enum AVSessionCallback_Result
```

**Description**

Enumerates the audio and video session callback results.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| AVSESSION_CALLBACK_RESULT_SUCCESS = 0 | The session callback returns a success result.|
| AVSESSION_CALLBACK_RESULT_FAILURE = -1 | The session callback returns a failure result.|

### AVMetadata_Result

```c
enum AVMetadata_Result
```

**Description**

Enumerates the playback control metadata error codes.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| AVMETADATA_SUCCESS = 0 | The API execution is successful.|
| AVMETADATA_ERROR_INVALID_PARAM = 1 | The function is executed with invalid input parameters.|
| AVMETADATA_ERROR_NO_MEMORY = 2 | Failed to allocate memory.|

### AVQueueItem_Result

```c
enum AVQueueItem_Result
```

**Description**

Enumerates the error codes of an item in the queue.

**Since:** 23

| Enum Item| Description|
| -- | -- |
| AVQUEUEITEM_SUCCESS = 0 |  The API execution is successful.|
| AVQUEUEITEM_ERROR_INVALID_PARAM = 1 |  The function is executed with invalid input parameters.|
| AVQUEUEITEM_ERROR_NO_MEMORY = 2 |  Failed to allocate memory.|
