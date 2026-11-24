# OH_NativeXComponent_MouseEvent

```c
typedef struct OH_NativeXComponent_MouseEvent {...} OH_NativeXComponent_MouseEvent
```

## Overview

Represents the mouse event information.

<!--Device-typedef struct OH_NativeXComponent_MouseEvent {...} OH_NativeXComponent_MouseEvent--><!--Device-typedef struct OH_NativeXComponent_MouseEvent {...} OH_NativeXComponent_MouseEvent-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 9

**Related module**: [OH_NativeXComponent Native XComponent](capi-arkui-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float x | X coordinate of the mouse point relative to the left edge of the element to mouse.<br><!--Device-float x--><!--Device-float x-End--> |
| float y | Y coordinate of the mouse point relative to the upper edge of the element to mouse.<br><!--Device-float y--><!--Device-float y-End--> |
| float screenX | X coordinate of the mouse point relative to the left edge of the screen.<br><!--Device-float screenX--><!--Device-float screenX-End--> |
| float screenY | Y coordinate of the mouse point relative to the upper edge of the screen.<br><!--Device-float screenY--><!--Device-float screenY-End--> |
| int64_t timestamp | Timestamp of the current mouse event.<br><!--Device-int64_t timestamp--><!--Device-int64_t timestamp-End--> |
| [OH_NativeXComponent_MouseEventAction](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_mouseeventaction) action | Mouse event action.<br><!--Device-OH_NativeXComponent_MouseEventAction action--><!--Device-OH_NativeXComponent_MouseEventAction action-End--> |
| [OH_NativeXComponent_MouseEventButton](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_mouseeventbutton) button | Mouse event button.<br><!--Device-OH_NativeXComponent_MouseEventButton button--><!--Device-OH_NativeXComponent_MouseEventButton button-End--> |


