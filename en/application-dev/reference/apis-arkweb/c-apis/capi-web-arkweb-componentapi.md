# ArkWeb_ComponentAPI

```c
typedef struct ArkWeb_ComponentAPI {...} ArkWeb_ComponentAPI
```

## Overview

ArkWeb_ComponentAPI is an API struct provided by ArkWeb on the native side for listening to Web component lifecycle events. It inherits from the base native API type {@link ArkWeb_AnyNativeAPI}. Developers obtain this<br>struct by calling {@link OH_ArkWeb_GetNativeAPI} with the `ARKWEB_NATIVE_COMPONENT` type, and then register event<br>callbacks for Web component Controller attached, page load begin, page load end, and component destruction. This<br>struct is suitable for scenarios where you need to perceive key state changes of the Web component in native code (C/<br>C++), such as initializing native resources, synchronizing page load status, collecting analytics data, or releasing<br>associated resources upon component destruction. The related APIs must be called in the UI thread. Before calling a<br>specific member function, it is recommended to use the {@link ARKWEB_MEMBER_MISSING} macro to check whether the function pointer exists.

**Since**: 12

**Related module**: [Web](capi-web.md)

**Header file**: [arkweb_type.h](capi-arkweb-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t size | Size of the struct. |


### Member functions

| Name | Description |
| -- | -- |
| [void (\*onControllerAttached)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)](#oncontrollerattached) | Registers a callback listener for the Controller attached event. Note: This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists. |
| [void (\*onPageBegin)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)](#onpagebegin) | This callback is triggered when the web page starts loading. It is triggered only for the main frame, not for iframe or frameset content loading. This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists. |
| [void (\*onPageEnd)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)](#onpageend) | This callback is triggered when the web page finishes loading. It is triggered only for the main frame, not for iframe or frameset content loading. This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists. |
| [void (\*onDestroy)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)](#ondestroy) | Triggered when this **Web** component is destroyed. |

## Member function description

### onControllerAttached()

```c
void (*onControllerAttached)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)
```

**Description**

Registers a callback listener for the Controller attached event. Note: This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists.

### onPageBegin()

```c
void (*onPageBegin)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)
```

**Description**

This callback is triggered when the web page starts loading. It is triggered only for the main frame, not for iframe or frameset content loading. This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists.

### onPageEnd()

```c
void (*onPageEnd)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)
```

**Description**

This callback is triggered when the web page finishes loading. It is triggered only for the main frame, not for iframe or frameset content loading. This callback must be called in the UI thread. Before calling, it is recommended to use the ARKWEB_MEMBER_MISSING macro to check whether the function pointer exists.

### onDestroy()

```c
void (*onDestroy)(const char* webTag, ArkWeb_OnComponentCallback callback, void* userData)
```

**Description**

Triggered when this **Web** component is destroyed.


