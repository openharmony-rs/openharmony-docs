# OH_NativeXComponent_Callback

```c
typedef struct OH_NativeXComponent_Callback {...} OH_NativeXComponent_Callback
```

## Overview

Registers the surface lifecycle and touch event callbacks.

<!--Device-struct OH_NativeXComponent_Callback {...}--><!--Device-struct OH_NativeXComponent_Callback {...}-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 8

**Related module**: [OH_NativeXComponent Native XComponent](capi-arkui-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [void (\*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)](#onsurfacecreated) | - | Called when the surface is created. |
| [void (\*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)](#onsurfacechanged) | - | Called when the surface is changed. |
| [void (\*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)](#onsurfacedestroyed) | - | Called when the surface is destroyed. |
| [void (\*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)](#dispatchtouchevent) | - | Called when a touch event is triggered. |

## Member function description

### OnSurfaceCreated()

```c
void (*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)
```

**Description**

Called when the surface is created.

<!--Device-void (*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)--><!--Device-void (*OnSurfaceCreated)(OH_NativeXComponent* component, void* window)-End-->

### OnSurfaceChanged()

```c
void (*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)
```

**Description**

Called when the surface is changed.

<!--Device-void (*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)--><!--Device-void (*OnSurfaceChanged)(OH_NativeXComponent* component, void* window)-End-->

### OnSurfaceDestroyed()

```c
void (*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)
```

**Description**

Called when the surface is destroyed.

<!--Device-void (*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)--><!--Device-void (*OnSurfaceDestroyed)(OH_NativeXComponent* component, void* window)-End-->

### DispatchTouchEvent()

```c
void (*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)
```

**Description**

Called when a touch event is triggered.

<!--Device-void (*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)--><!--Device-void (*DispatchTouchEvent)(OH_NativeXComponent* component, void* window)-End-->


