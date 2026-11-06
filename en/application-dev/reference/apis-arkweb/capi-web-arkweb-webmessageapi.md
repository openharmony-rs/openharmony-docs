# ArkWeb_WebMessageAPI

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-03T09:55:35.605Z pushedAt=2026-08-06T12:04:05.812Z -->

```c
typedef struct {...} ArkWeb_WebMessageAPI
```

## Overview

ArkWeb_WebMessageAPI is a native API struct for Web messages. This struct provides functions for creating and destroying messages, setting and obtaining message types, and managing message data buffers. This API is part of the postMessage bridge, supporting bidirectional communication between Native code and HTML pages.

Web message APIs must be called on the UI thread by calling the OH_ArkWeb_GetNativeAPI method. Before calling, you are advised to use [ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#macros) to check the availability of function pointers, preventing crashes caused by a mismatch between the SDK and device ROM.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t size | Size of the struct.|

### Member Functions

| Name                                                                                          | Description                                                                    |
|----------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| [ArkWeb_WebMessagePtr (\*createWebMessage)()](#createwebmessage)                             | Creates a message.                                                   |
| [void (\*destroyWebMessage)(ArkWeb_WebMessagePtr* webMessage)](#destroywebmessage)           | Destroys a message.                                       |
| [void (\*setType)(ArkWeb_WebMessagePtr webMessage, ArkWeb_WebMessageType type)](#settype)    | Sets the message type.                    |
| [ArkWeb_WebMessageType (\*getType)(ArkWeb_WebMessagePtr webMessage)](#gettype)               | Obtains the message type.                        |
| [void (\*setData)(ArkWeb_WebMessagePtr webMessage, void* data, size_t dataLength)](#setdata) | Sets data.|
| [void* (\*getData)(ArkWeb_WebMessagePtr webMessage, size_t* dataLength)](#getdata)           | Obtains data.                        |

## Member Function Description

### createWebMessage()

```c
ArkWeb_WebMessagePtr (*createWebMessage)()
```

**Description**

Creates a message. Used to create a message object to be sent before postMessage communication between Native code and HTML pages. After calling createWebMessage(), you must call destroyWebMessage() to release the message resources when they are no longer needed. Failure to call destroyWebMessage() will cause a message resource leak, affecting system memory management.

**Returns**

| Type                      | Description|
|--------------------------|----|
| [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) | Pointer to the message struct. |

### destroyWebMessage()

```c
void (*destroyWebMessage)(ArkWeb_WebMessagePtr* webMessage)
```

**Description**

Destroys a message and releases the memory occupied by the message object. Must be used in pair with createWebMessage(). Call this method to release resources after the message is no longer needed. After the call, the webMessage pointer becomes invalid and should no longer be used.

**Parameters**

| Name                                                                      | Description|
|---------------------------------------------------------------------------|----|
| [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md)* webMessage            | Pointer to the message to destroy.  |

### setType()

```c
void (*setType)(ArkWeb_WebMessagePtr webMessage, ArkWeb_WebMessageType type)
```

**Description**

Sets the message type. @param webMessage Pointer to the message struct. @param type Message type.

**Parameters**

| Name                                                                      | Description|
|---------------------------------------------------------------------------|----|
| [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) webMessage            | Pointer to the message struct.  |
| [ArkWeb_WebMessageType](capi-arkweb-type-h.md#arkweb_webmessagetype) type | Message type.  |

### getType()

```c
ArkWeb_WebMessageType (*getType)(ArkWeb_WebMessagePtr webMessage)
```

**Description**

Obtains the message type. Used to distinguish different types of communication messages, such as text messages, JSON messages, and binary messages.

**Parameters**

| Name                                | Description|
|-------------------------------------|----|
| [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) webMessage | Pointer to the message struct.  |

**Returns**

| Type | Description |
|----|-------|
| [ArkWeb_WebMessageType](capi-arkweb-type-h.md#arkweb_webmessagetype)   | Enumerated value of the message type returned, such as ARKWEB_WEB_MESSAGE_TYPE_STRING or ARKWEB_WEB_MESSAGE_TYPE_ARRAY_BUFFER.   |

### setData()

```c
void (*setData)(ArkWeb_WebMessagePtr webMessage, void* data, size_t dataLength)
```

**Description**

Sets data. Used to set the specific content of the message, supporting the transfer of text, JSON, or binary data from Native code to HTML pages.

**Parameters**

| Name                                                           | Description      |
|----------------------------------------------------------------|----------|
| [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) webMessage | Pointer to the message struct.|
|  void* data                                                              | Data pointer. The caller is responsible for memory management. The function does not release this memory internally, and data ownership is not transferred.         |
|  size_t dataLength                                                              | Data length.        |

### getData()

```c
void* (*getData)(ArkWeb_WebMessagePtr webMessage, size_t* dataLength)
```

**Description**

Obtains data. Used to obtain the specific content of the message, supporting the reception of text, JSON, or binary data from HTML pages and processing them in Native code. setData() must be called first to set the data before getData() can be called to obtain the data. If getData() is called without calling setData() first, NULL is returned and dataLength is 0.

**Parameters**

| Name                 | Description      |
|----------------------|----------|
| [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) webMessage | Pointer to the message struct.|
| size_t* dataLength   | Data length, which is an output parameter.        |

**Returns**

| Type| Description   |
|----|-------|
| void* | Pointer to the message data. The data length is returned via the dataLength output parameter. The lifecycle of the returned pointer is bound to the message object. The pointer becomes invalid after the message is destroyed, and the caller should not free this memory. |