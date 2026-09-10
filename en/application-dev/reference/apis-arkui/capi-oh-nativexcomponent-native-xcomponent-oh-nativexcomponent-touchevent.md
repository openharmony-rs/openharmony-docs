# OH_NativeXComponent_TouchEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e2e8608c64e606248f00eb66f3b2d4805fae44da translatedAt=2026-08-27T08:49:11.514Z pushedAt=2026-08-28T02:50:48.229Z -->

```c
typedef struct {...} OH_NativeXComponent_TouchEvent
```

## Overview

Defines a touch event. When a user performs a touch operation on **XComponent**, this struct provides information such as the coordinates, type, contact area, pressure, and timestamp of the touch point. It applies to scenarios where **XComponent** touch interactions need to be handled at the native layer.

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
| float y | Y-coordinate of the touch point relative to the top edge of the **XComponent**, in px. |
| [OH_NativeXComponent_TouchEventType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_toucheventtype) type | Type of the touch event. |
| double size | Normalized size of the touch area, indicating the relative ratio of the contact area between the finger pad and the screen. The value range is 0.0 to 1.0. A larger value indicates a larger contact area. |
| float force | Pressure of the current touch event, as a normalized value. The value range is 0.0 to 1.0, where **0.0** indicates no pressure and **1.0** indicates the maximum pressure recognizable by the device. |
| int64_t deviceId | ID of the device where the current touch event is triggered.|
| int64_t timeStamp | Timestamp of the touch point. It is the interval between the time when the event is triggered and the time when the system starts, in nanoseconds.|
| [OH_NativeXComponent_TouchPoint](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-touchpoint.md) touchPoints[OH_NATIVE_XCOMPONENT_MAX_TOUCH_POINTS_NUMBER] | Array of the current touch points. The number of valid elements in the array is specified by **numPoints**. For details about **OH_NATIVE_XCOMPONENT_MAX_TOUCH_POINTS_NUMBER**, see [Macros](capi-native-interface-xcomponent-h.md#macros). |
| uint32_t numPoints | Number of the current touch points. The value range is [1, **OH_NATIVE_XCOMPONENT_MAX_TOUCH_POINTS_NUMBER**]. The value **1** indicates single-finger touch, and a value greater than 1 indicates multi-finger touch. |
