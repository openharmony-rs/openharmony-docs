# ArkWeb_ComponentAPI

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zourongchun-->
<!--Designer: @kurli1-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=d1b85ec7ea193eefc4ef0fcb99c42629d3e17584 translatedAt=2026-08-03T09:48:28.212Z pushedAt=2026-08-06T07:46:02.837Z -->

```c
typedef struct {...} ArkWeb_ComponentAPI
```

## Overview

ArkWeb_ComponentAPI is an API struct provided by ArkWeb on the native side for listening to Web component lifecycle events. It inherits from the base native API type [ArkWeb_AnyNativeAPI](capi-web-arkweb-anynativeapi.md). Developers obtain this struct by calling [OH_ArkWeb_GetNativeAPI](capi-arkweb-interface-h.md#oh_arkweb_getnativeapi) with the `ARKWEB_NATIVE_COMPONENT` type, and then register event callbacks for Web component Controller attached, page load begin, page load end, and component destruction. This struct is suitable for scenarios where you need to perceive key state changes of the Web component in native code (C/C++), such as initializing native resources, synchronizing page load status, collecting analytics data, or releasing associated resources upon component destruction. The related APIs must be called in the UI thread. Before calling a specific member function, it is recommended to use the [ARKWEB_MEMBER_MISSING](capi-arkweb-type-h.md#macros) macro to check whether the function pointer exists.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| size_t size | Size of the struct.|

### Member Functions

| Name                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [void (\*onControllerAttached)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)](#oncontrollerattached) | Registers a callback for the Controller Attached event.                          |
| [void (\*onPageBegin)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)](#onpagebegin) | Registers a callback for the Web component page load begin event. This callback is triggered only on the main frame and will not be triggered when content in an iframe or frameset is loaded. |
| [void (\*onPageEnd)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)](#onpageend) | Registers a callback for the Web component page load end event. This callback is triggered only on the main frame and will not be triggered when content in an iframe or frameset is loaded. |
| [void (\*onDestroy)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)](#ondestroy) | Registers a callback for the Web component destruction event.                                |

## Member Function Description

### onControllerAttached()

```c
void (*onControllerAttached)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)
```

**Description**

Registers a callback listener for the Controller attached event. Note: This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists.

**Parameters**

| Name| Description|
| -- | -- |
| const char* webTag | Name of the **Web** component.|
| ArkWeb_OnComponentCallback callback | Callback of **onControllerAttached**.|
|  void* userData | User-defined data.|

### onPageBegin()

```c
void (*onPageBegin)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)
```

**Description**

This callback is triggered when the web page starts loading. It is triggered only for the main frame, not for iframe or frameset content loading. This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists.

**Parameters**

| Name| Description|
| -- | -- |
| const char* webTag | Name of the **Web** component.|
| ArkWeb_OnComponentCallback callback | Callback invoked when the web page starts loading, used to handle the business logic at the beginning of the page load. |
| void* userData | Pointer to the user-defined data. This data is passed to the callback when the callback is triggered, and can be used to save context information or state data. |

### onPageEnd()

```c
void (*onPageEnd)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)
```

**Description**

This callback is triggered when the web page finishes loading. It is triggered only for the main frame, not for iframe or frameset content loading. This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists.

**Parameters**

| Name| Description|
| -- | -- |
| const char* webTag | Name of the **Web** component.|
| [ArkWeb_OnComponentCallback](./capi-arkweb-type-h.md#arkweb_oncomponentcallback) callback | Callback triggered when page load completes, used to handle business logic after page load completes. |
| void* userData | User-defined data pointer. This data is passed to the callback function when the callback is triggered, and can be used to save context information or state data. |

### onDestroy()

```c
void (*onDestroy)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)
```

**Description**

Triggered when this **Web** component is destroyed.

**Parameters**

| Name| Description|
| -- | -- |
| const char* webTag | Name of the **Web** component.|
| ArkWeb_OnComponentCallback callback | Callback of **onDestroy**.|
| void* userData | Pointer to the user-defined data. |