# Input_InterceptorEventCallback

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=98b59aab53480716b722fc4051586a4a2638d2bf translatedAt=2026-09-11T00:08:58.559Z pushedAt=2026-09-11T02:54:37.583Z -->

```c
typedef struct Input_InterceptorEventCallback {...} Input_InterceptorEventCallback
```

## Overview

Defines the interceptor callback event structure, which is used to define the callback types required for input event interception. Mouse interception events, touch input events, and axis events are supported.

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Input_MouseEventCallback](capi-oh-input-manager-h.md#input_mouseeventcallback) mouseCallback | Callback for mouse events. |
| [Input_TouchEventCallback](capi-oh-input-manager-h.md#input_toucheventcallback) touchCallback | Callback for touch input events. |
| [Input_AxisEventCallback](capi-oh-input-manager-h.md#input_axiseventcallback) axisCallback | Callback for axis events. |
