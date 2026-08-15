# ArkWeb_WebMessagePortAPI

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-03T09:56:04.927Z pushedAt=2026-08-06T12:25:56.646Z -->

```c
typedef struct {...} ArkWeb_WebMessagePortAPI
```

## Overview

ArkWeb_WebMessagePortAPI is a native API struct for web message ports. This struct provides functions such as message port creation, closing, message sending, and message receiving callback registration. This API is a core component of the postMessage bridge, supporting the establishment of persistent bidirectional communication channels between native code and web pages. It is suitable for scenarios where data interaction between native apps and web pages is required, solving cross-language communication challenges and improving app extensibility and development efficiency.

Web message port related APIs must be called on the UI thread by using the OH_ArkWeb_GetNativeAPI method. Before calling, you are advised to use [ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#macros) to check the availability of function pointers, preventing crashes caused by mismatches between the SDK and the device ROM.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t size | Size of the struct, in bytes. |

### Member Functions

| Name                                                                                                                                                                                             | Description        |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| [ArkWeb_ErrorCode (\*postMessage)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag, const ArkWeb_WebMessagePtr webMessage)](#postmessage)                                      | Sends a message to the HTML page.|
| [void (\*close)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag)](#close)                                                                                                     | Closes a message port.   |
| [void (\*setMessageEventHandler)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag, ArkWeb_OnMessageEventHandler messageEventHandler, void* userData)](#setmessageeventhandler) | Sets a callback for receiving HTML messages.          |

## Member Function Description

### postMessage()

```c
ArkWeb_ErrorCode (*postMessage)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag, const ArkWeb_WebMessagePtr webMessage)
```

**Description**

Sends a message to the HTML page. It is used when native code needs to pass data, instructions, or configuration information to a web page, for example, form data synchronization and control command delivery.

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort | Pointer to the message port.|
| const char* webTag | Name of the Web component, used to identify the Web component to operate. It must be a unique identifier bound to the Web component. If no Web component bound to webTag is found, an initialization failure error is returned. |
|  const [ArkWeb_WebMessagePtr](capi-web-arkweb-webmessage8h.md) webMessage | Message to send.|

**Returns**

| Type | Description |
| -- | -- |
| [ArkWeb_ErrorCode](capi-arkweb-error-code-h.md#arkweb_errorcode) | Result code.<br>[ARKWEB_SUCCESS](capi-arkweb-error-code-h.md#arkweb_errorcode): execution successful.<br>[ARKWEB_INVALID_PARAM](capi-arkweb-error-code-h.md#arkweb_errorcode): invalid parameter.<br><br>**Possible causes:**<br>- webMessagePort or webMessage is null.<br>- The parameter type is incorrect.<br><br>**Solutions:**<br>- Check whether the parameter is a null pointer.<br>- Verify that the parameter type meets the API requirements.<br><br>[ARKWEB_INIT_ERROR](capi-arkweb-error-code-h.md#arkweb_errorcode): initialization failed. No Web component bound to webTag is found.<br><br>**Possible causes:**<br>- The Web component is not properly initialized.<br>- The webTag parameter does not match the actual Web component name.<br><br>**Solutions:**<br>- Ensure that the Web component has been initialized.<br>- Check whether the webTag parameter matches the Web component name. |

### close()

```c
void (*close)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag)
```

**Description**

Closes a message port.

**Parameters**

| Name| Description|
| -- | -- |
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort | Pointer to the message port.|
| const char* webTag                                                                   |  Name of the **Web** component.             |

### setMessageEventHandler()

```c
void (*setMessageEventHandler)(const ArkWeb_WebMessagePortPtr webMessagePort, const char* webTag,
        ArkWeb_OnMessageEventHandler messageEventHandler, void* userData)
```

**Description**

Sets a callback for receiving HTML messages. It is used when messages, requests, or event notifications from a web page need to be received and processed, for example, receiving user input and status update notifications.

**Parameters**

| Name                                                                                                   | Description                  |
|--------------------------------------------------------------------------------------------------------|----------------------|
| const [ArkWeb_WebMessagePortPtr](capi-web-arkweb-webmessageport8h.md) webMessagePort                       | Pointer to the message port.|
| const char* webTag                                                                                     |  Name of the **Web** component.                    |
| [ArkWeb_OnMessageEventHandler](capi-arkweb-type-h.md#arkweb_onmessageeventhandler) messageEventHandler | Callback used to handle messages.                    |
| void* userData                                                                                         | User-defined data that is passed to the messageEventHandler callback when triggered. It can be used to carry context information or additional service data, and its lifecycle is managed by the app.                     |