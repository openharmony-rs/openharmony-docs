# OH_NativeXComponent_TouchPoint
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-08-27T08:48:55.529Z pushedAt=2026-08-28T02:55:37.498Z -->

```c
typedef struct {...} OH_NativeXComponent_TouchPoint
```

## Overview

Defines the information about a touch point in a touch event. This struct is filled by the system in the touch event callback. Through the callback, you can obtain the status data of each touch point, including the coordinates relative to the application window and the component, touch type, contact area, pressure, timestamp, and pressed state. It applies to scenarios where multi-touch information needs to be accurately obtained and processed.

**Since**: 8

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t id | Unique identifier of the finger.|
| float screenX | X-coordinate of the touch point relative to the upper left corner of the application window where the **XComponent** is located, in px. |
| float screenY | Y-coordinate of the touch point relative to the upper left corner of the application window where the **XComponent** is located, in px. |
| float x | X-coordinate of the touch point relative to the left edge of the **XComponent**, in px. |
| float y | Y-coordinate of the touch point relative to the upper edge of the **XComponent**, in px. |
| [OH_NativeXComponent_TouchEventType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_toucheventtype) type | Type of the touch event, used to distinguish different touch actions such as press, lift, and movement. For details about the values, see **OH_NativeXComponent_TouchEventType**. |
| double size | Contact area between the finger pad and the screen. The value range is [0.0, 1.0], and a larger value indicates a larger contact area (normalized value). |
| float force | Pressure of the current touch event. The value range is [0, 1], where **0** indicates no pressure and **1** indicates the maximum pressure recognizable by the device (the actual value range depends on the device capability). |
| int64_t timeStamp | Timestamp of the touch event. It is the interval between the time when the event is triggered and the time when the system starts, in nanoseconds.|
| bool isPressed | Whether the current point is pressed. **true** when the point is pressed, **false** when it is released.|


