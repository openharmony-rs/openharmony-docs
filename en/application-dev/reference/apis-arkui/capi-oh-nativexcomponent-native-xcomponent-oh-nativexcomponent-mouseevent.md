# OH_NativeXComponent_MouseEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=93671d7b3a52ef991619a64de0a6519e9c56b14b translatedAt=2026-10-10T10:42:25.678Z pushedAt=2026-10-15T03:19:24.909Z -->

```c
typedef struct {...} OH_NativeXComponent_MouseEvent
```

## Overview

Defines a mouse event. It is used to pass mouse event information in the mouse event callback of **XComponent**, including the coordinates of the touch point relative to the component and the screen, the event timestamp, the mouse action, and the button information.

**Since**: 9

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | X-coordinate of the mouse point relative to the upper left corner of the current component. Unit: px. |
| float y | Y-coordinate of the mouse point relative to the upper left corner of the current component. Unit: px. |
| float screenX | X-coordinate of the mouse point relative to the upper left corner of the application screen where the **XComponent** is located. Unit: px. |
| float screenY | Y-coordinate of the mouse point relative to the upper left corner of the application screen where the **XComponent** is located. Unit: px. |
| int64_t timestamp | Timestamp of the current mouse event. It is the interval between the time when the event is triggered and the time when the system starts, in ns. |
| [OH_NativeXComponent_MouseEventAction](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_mouseeventaction) action | Action of the current mouse event. For details about the values, see **OH_NativeXComponent_MouseEventAction**, which includes actions such as press, release, and movement. |
| [OH_NativeXComponent_MouseEventButton](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_mouseeventbutton) button | Button that triggers the current mouse event. For details about the values, see **OH_NativeXComponent_MouseEventButton**, which includes buttons such as the left button, right button, middle button, back button, and forward button. |


