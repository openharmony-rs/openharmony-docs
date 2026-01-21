# qos.h
<!--Kit: Kernel Enhance Kit-->
<!--Subsystem: Kernel-->
<!--Owner: @gatieme-->
<!--Designer: @tanyihua-->
<!--Tester: @panny060-->
<!--Adviser: @fang-jinxu-->

## Overview

Declares the C APIs provided by QoS.

**Reference file**: <qos/qos.h>

**System capability**: SystemCapability.Resourceschedule.QoS.Core

**Library**: libqos.so

**Since**: 12

**Related module**: [QoS](capi-qos.md)

## Summary

### Structs

| Name| Description                                     |
| -- |-----------------------------------------|
| [OH_QoS_GewuCreateSessionResult](capi-qos-oh-qos-gewucreatesessionresult.md) | Defines the created session handle.                              |
| [OH_QoS_GewuSubmitRequestResult](capi-qos-oh-qos-gewusubmitrequestresult.md) | Defines error codes.<br>- If the session is created successfully, **OH_QOS_GEWU_OK** is returned.<br>- If the session fails to be created due to insufficient memory, **OH_QOS_GEWU_NOMEM** is returned.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [QoS_Level](#qos_level) | QoS_Level | Enumerates the QoS levels.|
| [OH_QoS_GewuErrorCode](#oh_qos_gewuerrorcode) | OH_QoS_GewuErrorCode | Enumerates the Gewu error codes.|

### Macros

| Name| Description|
| -- | -- |
| OH_QOS_GEWU_INVALID_SESSION_ID (static_cast\<OH_QoS_GewuSession\>(0xffffffffU)) | Indicates an invalid session handle, which is used for error return.<br>**Since**: 20|
| OH_QOS_GEWU_INVALID_REQUEST_ID (static_cast\<OH_QoS_GewuRequest\>(0xffffffffU)) | Indicates an invalid request handle, which is used for error return.<br>**Since**: 20|

### Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [int OH_QoS_SetThreadQoS(QoS_Level level)](#oh_qos_setthreadqos) | - | Sets the QoS level for the calling thread.|
| [int OH_QoS_ResetThreadQoS()](#oh_qos_resetthreadqos) | - | Cancels the QoS level of the calling thread.|
| [int OH_QoS_GetThreadQoS(QoS_Level *level)](#oh_qos_getthreadqos) | - | Obtains the QoS level of the calling thread.|
| [typedef void (\*OH_QoS_GewuOnResponse)(void* context, const char* response)](#oh_qos_gewuonresponse) | OH_QoS_GewuOnResponse | Called for receiving responses.|
| [OH_QoS_GewuCreateSessionResult OH_QoS_GewuCreateSession(const char* attributes)](#oh_qos_gewucreatesession) | - | Creates a GeWu session. The lifecycle of the session object starts from when the **CreateSession** function returns and ends when **DestroySession** is called. `const char* attributes`: JSON string of the session attributes. It supports the following fields: **- model: string**, which indicates the path of the model used by the session. Example of the JSON string of **attributes**:<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;"model": "/data/storage/el2/base/files/qwen2/"<br>&nbsp;}  |
| [OH_QoS_GewuErrorCode OH_QoS_GewuDestroySession(OH_QoS_GewuSession session)](#oh_qos_gewudestroysession) | - | Destroys a Gewu session. You are advised to wait until all requests are complete or aborted before calling this API. If there are ongoing requests when this API is called, the requests will be aborted, and you will not receive responses. Note that after this API is called, the session object cannot be used.|
| [OH_QoS_GewuErrorCode OH_QoS_GewuAbortRequest(OH_QoS_GewuSession session, OH_QoS_GewuRequest request)](#oh_qos_gewuabortrequest) | - | Stops a specified request. After this function is successfully called, the client will not receive any response to the request, and the request handle cannot be used.|
| [OH_QoS_GewuSubmitRequestResult OH_QoS_GewuSubmitRequest(OH_QoS_GewuSession session, const char* request, OH_QoS_GewuOnResponse callback, void* context)](#oh_qos_gewusubmitrequest) | - | Submits a request. `const char* request`: JSON string of the request. The following fields are supported: - **messages**: Array. An array of messages, where each element supports the following fields: - **role**: String. Role type of the message. - **"developer"**: Instructions provided by developers or the system. - **"user"**: User input. - **"assistant"**: Model generation result. - **content**: String. Message content. - **stream**: Boolean or null. This parameter is optional. Whether to enable streaming inference. By default, streaming inference is disabled. Example of a JSON string:<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;"messages": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"role": "developer",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"content": "Your are a helpful assistant."<br>&nbsp;&nbsp;&nbsp;&nbsp;},<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"role": "user",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"content": "What is OpenHarmony"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;&nbsp;&nbsp;],<br>&nbsp;&nbsp;&nbsp;&nbsp;"stream": true<br>}  |

### Variables

| Name                | Description  |
|--------------------|------|
| OH_QoS_GewuSession | Session handle.|
| OH_QoS_GewuRequest | Request handle.|

## Enum Description

### QoS_Level

```c
enum QoS_Level
```

**Description**

Enumerates the QoS levels.

**Since**: 12

| Value| Description|
| -- | -- |
| QOS_BACKGROUND = 0 | QoS level for user invisible tasks.|
| QOS_UTILITY | QoS level for background critical tasks.|
| QOS_DEFAULT | Default QoS level.|
| QOS_USER_INITIATED | QoS level for user triggered tasks.|
| QOS_DEADLINE_REQUEST | QoS level for time limited tasks.|
| QOS_USER_INTERACTIVE | QoS level for user interactive tasks.|

### OH_QoS_GewuErrorCode

```c
enum OH_QoS_GewuErrorCode
```

**Description**

Enumerates the Gewu error codes.

**Since**: 20

| Value| Description|
| -- | -- |
| OH_QOS_GEWU_OK = 0 | Operation successful.|
| OH_QOS_GEWU_NOPERM = 201 | Permission denied.|
| OH_QOS_GEWU_NOMEM = 203 | Memory error.|
| OH_QOS_GEWU_INVAL = 401 | Invalid parameter.|
| OH_QOS_GEWU_EXIST = 501 | Handle already exists.|
| OH_QOS_GEWU_NOENT = 502 | Handle not found.|
| OH_QOS_GEWU_NOSYS = 801 | Symbol not found.|
| OH_QOS_GEWU_FAULT = 901 | Other errors.|


## Function Description

### OH_QoS_SetThreadQoS()

```c
int OH_QoS_SetThreadQoS(QoS_Level level)
```

**Description**

Sets the QoS level for the calling thread.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [QoS_Level](capi-qos-h.md#qos_level) level | Sets the QoS level. For details, see [QoS_Level](capi-qos-h.md#qos_level).|

**Returns**

| Type| Description|
| -- | -- |
| int | **0** is returned if the operation is successful; a negative value is returned otherwise.|

**Reference**

[QoS_Level](capi-qos-h.md#qos_level)


### OH_QoS_ResetThreadQoS()

```c
int OH_QoS_ResetThreadQoS()
```

**Description**

Cancels the QoS level of the calling thread.

**Since**: 12

**Returns**

| Type| Description|
| -- | -- |
| int | **0** is returned if the operation is successful; a negative value is returned otherwise.|

**Reference**

[QoS_Level](capi-qos-h.md#qos_level)


### OH_QoS_GetThreadQoS()

```c
int OH_QoS_GetThreadQoS(QoS_Level *level)
```

**Description**

Obtains the QoS level of the calling thread.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [QoS_Level](capi-qos-h.md#qos_level) *level | QoS level of the calling thread. The parameter is an output parameter and is written to this variable in [QoS_Level](capi-qos-h.md#qos_level) format.|

**Returns**

| Type| Description|
| -- | -- |
| int | **0** is returned if the operation is successful; a negative value is returned otherwise.|

**Reference**

[QoS_Level](capi-qos-h.md#qos_level)


### OH_QoS_GewuOnResponse()

```c
typedef void (*OH_QoS_GewuOnResponse)(void* context, const char* response)
```

**Description**

Called for receiving responses.

**Since**: 20

**Parameters**

| Name| Description                                                                                                                                                                                                                                                                                                                                                                |
| -- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| void* context | User context handle specified when the request is submitted.                                                                                                                                                                                                                                                                                                                                                  |
| const char* response | JSON string of the response, which contains the following parameters:<br>- **message**: Message containing the following fields:<br>&nbsp;&nbsp;&nbsp;&nbsp;- **role**: String. Role type of the message, which should be **"assistant"**.<br>&nbsp;&nbsp;&nbsp;&nbsp;- **content**: String. Message content.<br>- **finish_reason**: String or null. Finish reason. The possible values are as follows:<br>&nbsp;&nbsp;&nbsp;&nbsp;- **null**: The request is not stopped. In streaming inference, there are multiple responses, and only the last response has a non-empty **finish_reason**. In non-streaming inference, there is only one response, and **finish_reason** is not empty.<br>&nbsp;&nbsp;&nbsp;&nbsp;- **"stop"**: The request is stopped normally.<br>&nbsp;&nbsp;&nbsp;&nbsp;- **"abort"**: The request is stopped by the user in advance.<br>&nbsp;&nbsp;&nbsp;&nbsp;- **"length"**: The number of tokens exceeds the upper limit.|

### OH_QoS_GewuCreateSession()

```c
OH_QoS_GewuCreateSessionResult OH_QoS_GewuCreateSession(const char* attributes)
```

**Description**

Creates a GeWu session. The lifecycle of the session object starts from when the **CreateSession** function returns and ends when **DestroySession** is called. `const char* attributes`: JSON string of the session attributes. It supports the following fields: - **model**: String, which indicates the path of the model used by the session. Example of the JSON string of **attributes**:<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;"model": "/data/storage/el2/base/files/qwen2/"<br>&nbsp;}

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const char* attributes | JSON string of session attributes.|

**Returns**

| Type| Description|
|--| -- |
| [OH_QoS_GewuCreateSessionResult](capi-qos-oh-qos-gewucreatesessionresult.md) | Result of creating a session.|

### OH_QoS_GewuDestroySession()

```c
OH_QoS_GewuErrorCode OH_QoS_GewuDestroySession(OH_QoS_GewuSession session)
```

**Description**

Destroys a Gewu session. You are advised to wait until all requests are complete or aborted before calling this API. If there are ongoing requests when this API is called, the requests will be aborted, and you will not receive responses. Note that after this API is called, the session object cannot be used.

**Since**: 20

**Parameters**

| Name  | Description|
|--| -- |
| [OH_QoS_GewuSession](#variables) session| Handle of the session to destroy.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_QoS_GewuErrorCode](capi-qos-h.md#oh_qos_gewuerrorcode) | Error code.<br>         - If the session is destroyed successfully, **OH_QOS_GEWU_OK** is returned.<br>         - If the session is not found, **OH_QOS_GEWU_NOENT** is returned.|

### OH_QoS_GewuAbortRequest()

```c
OH_QoS_GewuErrorCode OH_QoS_GewuAbortRequest(OH_QoS_GewuSession session, OH_QoS_GewuRequest request)
```

**Description**

Stops a specified request. After this function is successfully called, the client will not receive any response to the request, and the request handle cannot be used.

**Since**: 20

**Parameters**

| Name                              | Description|
|-----------------------------------| -- |
| [OH_QoS_GewuSession](#variables) session| Handle of the session to which the request is submitted.|
| [OH_QoS_GewuRequest](#variables) request| Handle of the request.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_QoS_GewuErrorCode](capi-qos-h.md#oh_qos_gewuerrorcode) | Error code.<br>         - If the request is successfully stopped, **OH_QOS_GEWU_OK** is returned.<br>         - If the request is not found, **OH_QOS_GEWU_NOENT** is returned.|

### OH_QoS_GewuSubmitRequest()

```c
OH_QoS_GewuSubmitRequestResult OH_QoS_GewuSubmitRequest(OH_QoS_GewuSession session, const char* request, OH_QoS_GewuOnResponse callback, void* context)
```

**Description**

Submits a request. `const char* request`: JSON string of the request. The following fields are supported: - **messages**: Array. An array of messages, where each element supports the following fields: - **role**: String. Role type of the message. - **"developer"**: Instructions provided by developers or the system. - **"user"**: User input. - **"assistant"**: Model generation result.- content: string. Message content. - **stream**: Boolean or null. This parameter is optional. Whether to enable streaming inference. By default, streaming inference is disabled. Example of a JSON string:<br>{<br>&nbsp;&nbsp;&nbsp;&nbsp;"messages": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"role": "developer",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"content": "Your are a helpful assistant."<br>&nbsp;&nbsp;&nbsp;&nbsp;},<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"role": "user",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"content": "What is OpenHarmony"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;&nbsp;&nbsp;],<br>&nbsp;&nbsp;&nbsp;&nbsp;"stream": true<br>}

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_QoS_GewuSession](#variables) session| Handle of the session to which the request is submitted.|
| const char* request | JSON string of the request.|
| [OH_QoS_GewuOnResponse](capi-qos-h.md#oh_qos_gewuonresponse) callback | Callback for receiving responses.|
| void* context | Pointer to the user context to be passed to the callback.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_QoS_GewuSubmitRequestResult](capi-qos-oh-qos-gewusubmitrequestresult.md) | Result of submitting a Gewu request.<br>         - If the request is submitted successfully, the value of **error** in **OH_QoS_GewuSubmitRequestResult** is **OH_QOS_GEWU_OK**, and the value of **request** is the request handle.<br>         - If the request fails to be submitted, the value of **error** in **OH_QoS_GewuSubmitRequestResult** is the cause of the error. **OH_QOS_GEWU_NOMEM** indicates that memory is insufficient for processing the request.|
