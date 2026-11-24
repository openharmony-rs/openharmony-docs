# OH_NativeXComponent_HistoricalPoint

```c
typedef struct OH_NativeXComponent_HistoricalPoint {...} OH_NativeXComponent_HistoricalPoint
```

## Overview

Represents the historical point.

<!--Device-typedef struct OH_NativeXComponent_HistoricalPoint {...} OH_NativeXComponent_HistoricalPoint--><!--Device-typedef struct OH_NativeXComponent_HistoricalPoint {...} OH_NativeXComponent_HistoricalPoint-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 10

**Related module**: [OH_NativeXComponent Native XComponent](capi-arkui-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t id | Unique identifier of a finger.<br><!--Device-int32_t id--><!--Device-int32_t id-End--> |
| float screenX | X coordinate of the touch point relative to the left edge of the screen.<br><!--Device-float screenX--><!--Device-float screenX-End--> |
| float screenY | Y coordinate of the touch point relative to the upper edge of the screen.<br><!--Device-float screenY--><!--Device-float screenY-End--> |
| float x | X coordinate of the touch point relative to the left edge of the element to touch.<br><!--Device-float x--><!--Device-float x-End--> |
| float y | Y coordinate of the touch point relative to the upper edge of the element to touch.<br><!--Device-float y--><!--Device-float y-End--> |
| [OH_NativeXComponent_TouchEventType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_toucheventtype) type | Touch type of the touch event.<br><!--Device-OH_NativeXComponent_TouchEventType type--><!--Device-OH_NativeXComponent_TouchEventType type-End--> |
| double size | Contact area between the finger pad and the screen.<br><!--Device-double size--><!--Device-double size-End--> |
| float force | Pressure of the current touch event.<br><!--Device-float force--><!--Device-float force-End--> |
| int64_t timeStamp | Timestamp of the current touch event.<br><!--Device-int64_t timeStamp--><!--Device-int64_t timeStamp-End--> |
| float titlX | The angle between projection on plane-X-Y and axis-Z of the current touch event.<br><!--Device-float titlX--><!--Device-float titlX-End--> |
| float titlY | The angle between projection on plane-Y-Z and axis-Z of the current touch event.<br><!--Device-float titlY--><!--Device-float titlY-End--> |
| [OH_NativeXComponent_TouchEvent_SourceTool](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_touchevent_sourcetool) sourceTool | The sourceTool of the current touch event.<br><!--Device-OH_NativeXComponent_TouchEvent_SourceTool sourceTool--><!--Device-OH_NativeXComponent_TouchEvent_SourceTool sourceTool-End--> |


