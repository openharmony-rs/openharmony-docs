# OH_NativeXComponent_MouseEvent_Callback

```c
typedef struct OH_NativeXComponent_MouseEvent_Callback {...} OH_NativeXComponent_MouseEvent_Callback
```

## Overview

Registers the mouse event callbacks.

<!--Device-struct OH_NativeXComponent_MouseEvent_Callback {...}--><!--Device-struct OH_NativeXComponent_MouseEvent_Callback {...}-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

**Related module**: [OH_NativeXComponent Native XComponent](capi-arkui-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [void (\*DispatchMouseEvent)(OH_NativeXComponent* component, void* window)](#dispatchmouseevent) | - | Called when a mouse event is triggered. |
| [void (\*DispatchHoverEvent)(OH_NativeXComponent* component, bool isHover)](#dispatchhoverevent) | - | Called when a hover event is triggered. |

## Member function description

### DispatchMouseEvent()

```c
void (*DispatchMouseEvent)(OH_NativeXComponent* component, void* window)
```

**Description**

Called when a mouse event is triggered.

<!--Device-void (*DispatchMouseEvent)(OH_NativeXComponent* component, void* window)--><!--Device-void (*DispatchMouseEvent)(OH_NativeXComponent* component, void* window)-End-->

### DispatchHoverEvent()

```c
void (*DispatchHoverEvent)(OH_NativeXComponent* component, bool isHover)
```

**Description**

Called when a hover event is triggered.

<!--Device-void (*DispatchHoverEvent)(OH_NativeXComponent* component, bool isHover)--><!--Device-void (*DispatchHoverEvent)(OH_NativeXComponent* component, bool isHover)-End-->


