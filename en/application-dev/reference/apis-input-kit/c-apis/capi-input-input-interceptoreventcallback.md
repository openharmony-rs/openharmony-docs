# Input_InterceptorEventCallback

```c
typedef struct Input_InterceptorEventCallback {...} Input_InterceptorEventCallback
```

## Overview

Defines the interceptor callback event structure, which is used to define the callback types required for input event interception. Mouse interception events, touch input events, and axis events are supported.

<!--Device-struct Input_InterceptorEventCallback {...}--><!--Device-struct Input_InterceptorEventCallback {...}-End-->

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Related module**: [input](capi-input-kit-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Input_MouseEventCallback](capi-oh-input-manager-h.md#input_mouseeventcallback) mouseCallback | Callback for mouse events.<br>**Since**: 12 |
| [Input_TouchEventCallback](capi-oh-input-manager-h.md#input_toucheventcallback) touchCallback | Callback for touch input events.<br>**Since**: 12 |
| [Input_AxisEventCallback](capi-oh-input-manager-h.md#input_axiseventcallback) axisCallback | Callback for axis events.<br>**Since**: 12 |


