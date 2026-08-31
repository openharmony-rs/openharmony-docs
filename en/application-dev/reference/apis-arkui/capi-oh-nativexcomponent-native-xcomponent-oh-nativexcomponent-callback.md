# OH_NativeXComponent_Callback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=26981b54dcb92d5646f17bc8dcf56ce1bdfdfcf7 translatedAt=2026-08-27T08:45:58.907Z pushedAt=2026-08-28T01:44:08.588Z -->

```c
typedef struct OH_NativeXComponent_Callback {...} OH_NativeXComponent_Callback
```

## Overview

Defines **OH_NativeXComponent_Callback**, which is used to register the Surface lifecycle (creation, change, and destruction) and touch event callbacks of the **XComponent** component. It applies to scenarios where the surface state changes need to be detected on the native side and user touch interactions need to be handled.

**Since**: 8

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [void (\*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)](#onsurfacecreated) | Invoked when the surface is created. |
| [void (\*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)](#onsurfacechanged) | Invoked when the size of the surface changes. |
| [void (\*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)](#onsurfacedestroyed) | Invoked when the surface is destroyed.|
| [void (\*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)](#dispatchtouchevent) | Invoked when a touch event is dispatched. |

## Member Function Description

### OnSurfaceCreated()

```c
void (*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)
```

**Description**


Invoked when the surface is created.

**Since**: 8

**Parameters**

| Name                               | Description|
|------------------------------------| -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to the **OH_NativeXComponent** instance. |
| void* window                       | **NativeWindow** handle.<br>The **NativeWindow** obtained through the **XComponent** lifecycle is held by the system with a reference count. After the **OnSurfaceDestroyed** callback is triggered, the reference count is decremented by one. After it reaches zero, the **NativeWindow** will be released. |

### OnSurfaceChanged()

```c
void (*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)
```

**Description**


Invoked when the size of the surface changes.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to the **OH_NativeXComponent** instance. |
| void* window | **NativeWindow** handle. This handle is passed in when the surface size or format changes, allowing you to perceive the latest surface state and update the rendering configuration. |

### OnSurfaceDestroyed()

```c
void (*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)
```

**Description**


Invoked when the surface is destroyed.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to the **OH_NativeXComponent** instance. |
|  void* window | **NativeWindow** handle. After this callback is triggered, the reference count of the **NativeWindow** held by the system is decremented by one. The **NativeWindow** will be released after it reaches zero. Do not continue to use this window handle after this callback. |

### DispatchTouchEvent()

```c
void (*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)
```

**Description**


Invoked when a touch event is dispatched. You can obtain touch event data in this callback to implement custom interaction logic, such as gesture recognition and custom drawing.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to the **OH_NativeXComponent** instance. |
|  void* window | **NativeWindow** handle.<br/>The **NativeWindow** obtained through the **XComponent** lifecycle is held by the system with a reference count. After the **OnSurfaceDestroyed** callback is triggered, the reference count is decremented by one. The **NativeWindow** will be released after the reference count reaches zero. |


