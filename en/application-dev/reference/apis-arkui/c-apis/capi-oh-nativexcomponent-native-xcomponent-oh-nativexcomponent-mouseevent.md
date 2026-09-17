# OH_NativeXComponent_MouseEvent

```c
typedef struct OH_NativeXComponent_MouseEvent {...} OH_NativeXComponent_MouseEvent
```

## Overview

Represents the mouse event information.

**Since**: 9

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float x | X coordinate of the mouse point relative to the left edge of the element to mouse. |
| float y | Y coordinate of the mouse point relative to the upper edge of the element to mouse. |
| float screenX | X coordinate of the mouse point relative to the left edge of the screen. |
| float screenY | Y coordinate of the mouse point relative to the upper edge of the screen. |
| int64_t timestamp | Timestamp of the current mouse event. |
| [OH_NativeXComponent_MouseEventAction](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_mouseeventaction) action | Mouse event action. |
| [OH_NativeXComponent_MouseEventButton](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_mouseeventbutton) button | Mouse event button. |


