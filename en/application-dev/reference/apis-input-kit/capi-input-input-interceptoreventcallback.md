# Input_InterceptorEventCallback

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the structure of interceptor callback events, including mouse events, touch events, and axis events.

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| Input_MouseEventCallback mouseCallback | Callback for mouse events.<br>**Since**: 12|
| Input_TouchEventCallback touchCallback | Callback used to return the touch event.<br>**Since**: 12|
| Input_AxisEventCallback axisCallback | Callback for axis events.<br>**Since**: 12|


### Member functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*Input_KeyEventCallback)(const Input_KeyEvent* keyEvent)](#input_keyeventcallback) | Input_KeyEventCallback() | Defines the lifecycle callback for **keyEvent**. If the callback is triggered, **keyEvent** will be destroyed.<br>**Since**: 12|
| [typedef void (\*Input_MouseEventCallback)(const Input_MouseEvent* mouseEvent)](#input_mouseeventcallback) | Input_MouseEventCallback() | Defines the lifecycle callback for **mouseEvent**. If the callback is triggered, **mouseEvent** will be destroyed.<br>**Since**: 12|
| [typedef void (\*Input_TouchEventCallback)(const Input_TouchEvent* touchEvent)](#input_toucheventcallback) | Input_TouchEventCallback() | Defines the lifecycle callback for **touchEvent**. If the callback is triggered, **touchEvent** will be destroyed.<br>**Since**: 12|
| [typedef void (\*Input_AxisEventCallback)(const Input_AxisEvent* axisEvent)](#input_axiseventcallback) | Input_AxisEventCallback() | Defines the lifecycle callback for **axisEvent**. If the callback is triggered, **axisEvent** will be destroyed.<br>**Since**: 12|
| [typedef void (\*Input_DeviceAddedCallback)(int32_t deviceId)](#input_deviceaddedcallback) | Input_DeviceAddedCallback() | Defines the callback used to receive device insertion events.<br>**Since**: 13|
| [typedef void (\*Input_DeviceRemovedCallback)(int32_t deviceId)](#input_deviceremovedcallback) | Input_DeviceRemovedCallback() | Defines the callback used to receive device removal events.<br>**Since**: 13|

## Member Function Description

### Input_KeyEventCallback()

```
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

```
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

```
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

```
typedef void (*Input_AxisEventCallback)(const Input_AxisEvent* axisEvent)
```

**Description**

Defines the lifecycle callback for **axisEvent**. If the callback is triggered, **axisEvent** will be destroyed.

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | Axis event object.|

### Input_DeviceAddedCallback()

```
typedef void (*Input_DeviceAddedCallback)(int32_t deviceId)
```

**Description**

Defines the callback used to receive device insertion events.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| int32_t deviceId | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.|

### Input_DeviceRemovedCallback()

```
typedef void (*Input_DeviceRemovedCallback)(int32_t deviceId)
```

**Description**

Defines the callback used to receive device removal events.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| int32_t deviceId | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.|
