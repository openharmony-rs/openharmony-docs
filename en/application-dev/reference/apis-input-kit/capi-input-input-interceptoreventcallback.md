# Input_InterceptorEventCallback

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=20afaef788761bf2910ca233e927684c4314041b translatedAt=2026-11-04T01:00:07.015Z pushedAt=2026-11-04T03:24:28.423Z nl=1 -->

```c
typedef struct Input_InterceptorEventCallback {...} Input_InterceptorEventCallback
```

## Overview

The Input_InterceptorEventCallback struct defines the callback function types required for input event interception, supporting the interception of mouse events, touchscreen input events, and axis events.

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Input_MouseEventCallback](capi-oh-input-manager-h.md#input_mouseeventcallback) mouseCallback | Callback for the mouse event. |
| [Input_TouchEventCallback](capi-oh-input-manager-h.md#input_toucheventcallback) touchCallback | Callback for the touchscreen input event. |
| [Input_AxisEventCallback](capi-oh-input-manager-h.md#input_axiseventcallback) axisCallback | Callback for the axis event. |
