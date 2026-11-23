# OH_NativeXComponent_HistoricalPoint
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-11-18T09:13:42.866Z pushedAt=2026-11-20T02:11:51.476Z nl=1 -->

```c
typedef struct {...} OH_NativeXComponent_HistoricalPoint
```

## Overview

Defines a historical touch point. During touch event processing, the system records the historical touch point information in the touch trajectory to restore the complete touch trajectory in scenarios such as high-speed swiping. Each historical touch point contains information such as coordinates, type, pressure, timestamp, and tilt angle. It is applicable to scenarios such as touch trajectory analysis and gesture recognition.

**Since**: 10

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
| [OH_NativeXComponent_TouchEventType](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_toucheventtype) type | Touch type of the touch event.|
| double size | Contact area between the touch tool and the screen. This value is the normalized contact area, with a value range of 0.0 to 1.0. |
| float force | Pressure of the current touch event. Value range: 0.0 to 1.0, where **0.0** indicates no pressure and **1.0** indicates the maximum pressure. |
| int64_t timeStamp | Timestamp of the current touch event. It is the interval between the time when the event is triggered and the time when the system starts, in nanoseconds. |
| float titlX | Angle between the projection on the x-y plane and the z axis of the current touch event, in radians. |
| float titlY | Angle between the projection on the y-z plane and the z axis of the current touch event, in radians. |
| [OH_NativeXComponent_TouchEvent_SourceTool](capi-native-interface-xcomponent-h.md#oh_nativexcomponent_touchevent_sourcetool) sourceTool | Source tool of the touch event.|


