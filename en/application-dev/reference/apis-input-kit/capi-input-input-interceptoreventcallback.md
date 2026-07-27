# Input_InterceptorEventCallback

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:20:31.742Z pushedAt=2026-06-12T02:47:37.894Z -->

```c
typedef struct Input_InterceptorEventCallback {...} Input_InterceptorEventCallback
```

## Overview

Defines the interceptor callback event structure, which is used to define the callback function types required for input event interception. Mouse interception events, touch input events, key events, and axis events are supported.

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Input_MouseEventCallback()](#input_mouseeventcallback) mouseCallback | Callback for mouse events.|
| [Input_TouchEventCallback()](#input_toucheventcallback) touchCallback | Callback used to return the touch event.|
| [Input_AxisEventCallback()](#input_axiseventcallback) axisCallback | Callback for axis events.|

### Member functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*Input_KeyEventCallback)(const Input_KeyEvent* keyEvent)](#input_keyeventcallback) | Input_KeyEventCallback() | Defines the lifecycle callback for **keyEvent**. If the callback is triggered, **keyEvent** will be destroyed.|
| [typedef void (\*Input_MouseEventCallback)(const Input_MouseEvent* mouseEvent)](#input_mouseeventcallback) | Input_MouseEventCallback() | Defines the lifecycle callback for **mouseEvent**. If the callback is triggered, **mouseEvent** will be destroyed.|
| [typedef void (\*Input_TouchEventCallback)(const Input_TouchEvent* touchEvent)](#input_toucheventcallback) | Input_TouchEventCallback() | Defines the lifecycle callback for **touchEvent**. If the callback is triggered, **touchEvent** will be destroyed.|
| [typedef void (\*Input_AxisEventCallback)(const Input_AxisEvent* axisEvent)](#input_axiseventcallback) | Input_AxisEventCallback() | Defines the lifecycle callback for **axisEvent**. If the callback is triggered, **axisEvent** will be destroyed.|

## Member Function Description

### Input_KeyEventCallback()

```c
typedef void (*Input_KeyEventCallback)(const Input_KeyEvent* keyEvent)
```

**Description**

Defines the lifecycle callback for **keyEvent**. If the callback is triggered, **keyEvent** will be destroyed.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [Input_KeyEvent](capi-input-input-keyevent.md)* keyEvent | Key event object.|

### Input_MouseEventCallback()

```c
typedef void (*Input_MouseEventCallback)(const Input_MouseEvent* mouseEvent)
```

**Description**

Defines the lifecycle callback for **mouseEvent**. If the callback is triggered, **mouseEvent** will be destroyed.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | Mouse event object.|

### Input_TouchEventCallback()

```c
typedef void (*Input_TouchEventCallback)(const Input_TouchEvent* touchEvent)
```

**Description**

Defines the lifecycle callback for **touchEvent**. If the callback is triggered, **touchEvent** will be destroyed.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | **touchEvent** object.|

### Input_AxisEventCallback()

```c
typedef void (*Input_AxisEventCallback)(const Input_AxisEvent* axisEvent)
```

**Description**

Defines the lifecycle callback for **axisEvent**. If the callback is triggered, **axisEvent** will be destroyed.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object.|