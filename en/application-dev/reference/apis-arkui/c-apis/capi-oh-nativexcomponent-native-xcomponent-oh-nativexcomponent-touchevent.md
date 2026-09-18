# OH_NativeXComponent_TouchEvent

```c
typedef struct OH_NativeXComponent_TouchEvent {...} OH_NativeXComponent_TouchEvent
```

## Overview

Represents the touch event.

**Since**: 8

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t id | Unique identifier of a finger. |
| float screenX | X coordinate of the touch point relative to the left edge of the screen. |
| float screenY | Y coordinate of the touch point relative to the upper edge of the screen. |
| float x | X coordinate of the touch point relative to the left edge of the element to touch. |
| float y | Y coordinate of the touch point relative to the upper edge of the element to touch. |
| [OH_NativeXComponent_TouchEventType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_toucheventtype) type | Touch type of the touch event. |
| double size | Contact area between the finger pad and the screen. |
| float force | Pressure of the current touch event. |
| int64_t deviceId | ID of the device where the current touch event is generated. |
| int64_t timeStamp | Timestamp of the current touch event. |
| [OH_NativeXComponent_TouchPoint](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent-touchpoint.md) touchPoints[OH_NATIVE_XCOMPONENT_MAX_TOUCH_POINTS_NUMBER] | Array of the current touch points. |
| uint32_t numPoints | Number of current touch points. |


