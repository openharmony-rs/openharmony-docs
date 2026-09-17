# OH_NativeXComponent_MouseEvent_Callback

```c
typedef struct OH_NativeXComponent_MouseEvent_Callback {...} OH_NativeXComponent_MouseEvent_Callback
```

## Overview

Registers the mouse event callbacks.

**Since**: 9

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member functions

| Name | Description |
| -- | -- |
| [void (\*DispatchMouseEvent)(OH_NativeXComponent* component, void* window)](#dispatchmouseevent) | Called when a mouse event is triggered. |
| [void (\*DispatchHoverEvent)(OH_NativeXComponent* component, bool isHover)](#dispatchhoverevent) | Called when a hover event is triggered. |

## Member function description

### DispatchMouseEvent()

```c
void (*DispatchMouseEvent)(OH_NativeXComponent* component, void* window)
```

**Description**

Called when a mouse event is triggered.

### DispatchHoverEvent()

```c
void (*DispatchHoverEvent)(OH_NativeXComponent* component, bool isHover)
```

**Description**

Called when a hover event is triggered.


