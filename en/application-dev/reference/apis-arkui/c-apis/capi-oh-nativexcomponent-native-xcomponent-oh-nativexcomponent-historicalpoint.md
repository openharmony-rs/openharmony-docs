# OH_NativeXComponent_HistoricalPoint

```c
typedef struct OH_NativeXComponent_HistoricalPoint {...} OH_NativeXComponent_HistoricalPoint
```

## Overview

Represents the historical point.

**Since**: 10

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
| int64_t timeStamp | Timestamp of the current touch event. |
| float titlX | The angle between projection on plane-X-Y and axis-Z of the current touch event. |
| float titlY | The angle between projection on plane-Y-Z and axis-Z of the current touch event. |
| [OH_NativeXComponent_TouchEvent_SourceTool](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_touchevent_sourcetool) sourceTool | The sourceTool of the current touch event. |


