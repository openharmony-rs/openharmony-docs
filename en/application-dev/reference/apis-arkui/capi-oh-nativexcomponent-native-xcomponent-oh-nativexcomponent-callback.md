# OH_NativeXComponent_Callback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_NativeXComponent_Callback {...} OH_NativeXComponent_Callback
```

## Overview

Registers callbacks for the surface lifecycle and touch event.

**Since**: 8

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [void (\*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)](#onsurfacecreated) | Invoked when a surface is created.|
| [void (\*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)](#onsurfacechanged) | Invoked when the surface changes.|
| [void (\*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)](#onsurfacedestroyed) | Invoked when the surface is destroyed.|
| [void (\*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)](#dispatchtouchevent) | Invoked when a touch event is triggered.|

## Member Function Description

### OnSurfaceCreated()

```c
void (*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)
```

**Description**


Invoked when a surface is created.

**Since**: 8

**Parameters**

| Name                               | Description|
|------------------------------------| -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to an [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md) instance.|
| void* window                       | Handle to the **NativeWindow** instance.<br>The **NativeWindow** instance obtained through the **XComponent** lifecycle callback is held by the system side with a reference count. After the **OnSurfaceDestroyed** callback is triggered, the reference count is decreased by one. After the reference count reaches zero, the **NativeWindow** instance will be released.|

### OnSurfaceChanged()

```c
void (*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)
```

**Description**


Invoked when the surface changes.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to an [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md) instance.|
|  void* window | Handle to the **NativeWindow** instance.|

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
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to an [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md) instance.|
|  void* window | Handle to the **NativeWindow** instance.|

### DispatchTouchEvent()

```c
void (*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)
```

**Description**


Invoked when a touch event is triggered.

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to an [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md) instance.|
|  void* window | Handle to the **NativeWindow** instance.|
