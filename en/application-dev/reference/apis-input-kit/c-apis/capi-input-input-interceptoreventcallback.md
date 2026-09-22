# Input_InterceptorEventCallback

```c
typedef struct Input_InterceptorEventCallback {...} Input_InterceptorEventCallback
```

## Overview

Defines the interceptor callback event structure, which is used to define the callback function types required for input event interception. Mouse interception events, touch input events, key events, and axis events are supported.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Input_MouseEventCallback](capi-oh-input-manager-h.md#input_mouseeventcallback) mouseCallback | Callback for mouse events. |
| [Input_TouchEventCallback](capi-oh-input-manager-h.md#input_toucheventcallback) touchCallback | Callback used to return the touch event. |
| [Input_AxisEventCallback](capi-oh-input-manager-h.md#input_axiseventcallback) axisCallback | Callback for axis events. |


