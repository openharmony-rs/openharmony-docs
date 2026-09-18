# arkweb_interface.h

## Overview

`arkweb_interface.h` is the core entry header file of ArkWeb on the native side (C/C++): it defines the basic Native API type [ArkWeb_AnyNativeAPI](capi-web-arkweb-anynativeapi.md) and the API type enum [ArkWeb_NativeAPIVariantKind](capi-arkweb-interface-h.md#arkweb_nativeapivariantkind), provides the [OH_ArkWeb_GetNativeAPI](capi-arkweb-interface-h.md#oh_arkweb_getnativeapi) interface for obtaining specific Native API structs such as Controller, Component, and CookieManager on demand, and also provides [OH_ArkWeb_RegisterScrollCallback](capi-arkweb-interface-h.md#oh_arkweb_registerscrollcallback) for registering scroll event callbacks of the Web component. When developers need to control Web component behavior in native code (such as executing JavaScript, managing cookies, monitoring component lifecycle or scroll events), they should first obtain the corresponding Native API through this header file, while capabilities such as page rendering and display still need to be provided by the Web component on the ArkTS side.

**Library**: libohweb.so

**System capability**: SystemCapability.Web.Webview.Core

**Since**: 11

**Related module**: [Web](capi-web.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkWeb_AnyNativeAPI](capi-web-arkweb-anynativeapi.md) | ArkWeb_AnyNativeAPI | ArkWeb_AnyNativeAPI is the basic struct type of ArkWeb Native API, used to uniformly represent pointers to various Native API structs obtained through the [OH_ArkWeb_GetNativeAPI](capi-arkweb-interface-h.md#oh_arkweb_getnativeapi) API. This struct contains a size member of the size_t type, which records the size of the current struct. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkWeb_NativeAPIVariantKind](#arkweb_nativeapivariantkind) | ArkWeb_NativeAPIVariantKind | Enumerates the native API types. |

### Function

| Name | Description |
| -- | -- |
| [ArkWeb_AnyNativeAPI* OH_ArkWeb_GetNativeAPI(ArkWeb_NativeAPIVariantKind type)](#oh_arkweb_getnativeapi) | Obtains the corresponding Native API struct based on the API type passed in. It is used in scenarios such as obtaining a Controller in native code to control Web component behavior, obtaining a CookieManager to manage cookies, obtaining a WebMessagePort for message communication, and obtaining a JavaScriptValue to operate JavaScript objects. |
| [bool OH_ArkWeb_RegisterScrollCallback(const char* webTag, ArkWeb_OnScrollCallback callback, void* userData)](#oh_arkweb_registerscrollcallback) | Registers a callback for the component scroll event. It is used in scenarios such as monitoring user scroll behavior for lazy loading, detecting scroll position for back-to-top functionality, recording user browsing behavior for data analysis, and implementing visual effects during scrolling. |

## Enum type description

### ArkWeb_NativeAPIVariantKind

```c
enum ArkWeb_NativeAPIVariantKind
```

**Description**

Enumerates the native API types.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKWEB_NATIVE_COMPONENT | API type related to Component. |
| ARKWEB_NATIVE_CONTROLLER | API type related to Controller. |
| ARKWEB_NATIVE_WEB_MESSAGE_PORT | API type related to WebMessagePort. |
| ARKWEB_NATIVE_WEB_MESSAGE | API type related to WebMessage. |
| ARKWEB_NATIVE_COOKIE_MANAGER | API type related to CookieManager. |
| ARKWEB_NATIVE_JAVASCRIPT_VALUE | API type related to ArkWeb JavaScript value.<br>**Since**: 18 |


## Function description

### OH_ArkWeb_GetNativeAPI()

```c
ArkWeb_AnyNativeAPI* OH_ArkWeb_GetNativeAPI(ArkWeb_NativeAPIVariantKind type)
```

**Description**

Obtains the corresponding Native API struct based on the API type passed in. It is used in scenarios such as obtaining a Controller in native code to control Web component behavior, obtaining a CookieManager to manage cookies, obtaining a WebMessagePort for message communication, and obtaining a JavaScriptValue to operate JavaScript objects.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkWeb_NativeAPIVariantKind](capi-arkweb-interface-h.md#arkweb_nativeapivariantkind) type | Type of Native API supported by ArkWeb. Different API types may require different system versions. For details, see the enum type description. <br>Note: The returned pointer is managed by the system and does not need to be manually released by the developer. Multiple calls with the same parameters may return the same pointer. The returned Native API struct is valid within the lifecycle of the Web component. Ensure thread safety when using it. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkWeb_AnyNativeAPI*](capi-web-arkweb-anynativeapi.md) | Returns the pointer to the corresponding Native API struct based on the passed-in API type. The first member      of the struct is the size of the current struct. It can be used to access specific Native API functions such as      Controller, Component, and CookieManager. <br> If the passed-in API type is not supported in the current system      version (for example, ARKWEB_NATIVE_JAVASCRIPT_VALUE is unavailable in versions earlier than 18), NULL is      returned. |

### OH_ArkWeb_RegisterScrollCallback()

```c
bool OH_ArkWeb_RegisterScrollCallback(const char* webTag, ArkWeb_OnScrollCallback callback, void* userData)
```

**Description**

Registers a callback for the component scroll event. It is used in scenarios such as monitoring user scroll behavior for lazy loading, detecting scroll position for back-to-top functionality, recording user browsing behavior for data analysis, and implementing visual effects during scrolling.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* webTag | Name of the **Web** component. |
| ArkWeb_OnScrollCallback callback | Callback used when a page is scrolled. |
| void* userData | Pointer to user-defined data. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | true is returned if the operation is successful; otherwise, false is returned. |


