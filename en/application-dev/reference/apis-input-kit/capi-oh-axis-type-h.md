# oh_axis_type.h

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:20:55.825Z pushedAt=2026-06-12T03:30:41.755Z -->

## Overview

Defines the device axis event struct and enumerates device axis events. The axis type defines the physical behavior characteristics of an input device in different interaction scenarios. The system uses the axis type to distinguish and transmit different gesture interaction information.

**File to include**: <multimodalinput/oh_axis_type.h>

**Library**: libohinput.so

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Related module**: [input](capi-input.md)

## Summary

### Enums

| **Name**| typedef Keyword| Description|
| -- | -- | -- |
| [InputEvent_AxisType](#inputevent_axistype) | InputEvent_AxisType | Provides axis types of the input device.|
| [InputEvent_AxisEventType](#inputevent_axiseventtype) | InputEvent_AxisEventType | Provides event types of the input device.|
| [InputEvent_AxisAction](#inputevent_axisaction) | InputEvent_AxisAction | Provides actions of the input device.|

## Enum Description

### InputEvent_AxisType

```c
enum InputEvent_AxisType
```

**Description**

Defines the axis type of an input device.

**Since**: 12

| Enum| Description            |
| -- |----------------|
| AXIS_TYPE_UNKNOWN = 0 | Unknown axis type, which is usually used as the initial value.|
| AXIS_TYPE_SCROLL_VERTICAL = 1 | Vertical scroll axis. When you scroll the mouse wheel or slide with one or two fingers on the touchpad, the status of the vertical scroll axis changes.              |
| AXIS_TYPE_SCROLL_HORIZONTAL = 2 | Horizontal scroll axis. When you scroll the mouse wheel or slide with two fingers on the touchpad, the status of the horizontal scroll axis changes.              |
| AXIS_TYPE_PINCH = 3 | Pinch axis, which is used to describe a two-finger pinch gesture on the touchpad.              |
| AXIS_TYPE_ROTATE = 4 | Rotation axis, which is used to describe a two-finger rotation gesture on the touchpad.              |

### InputEvent_AxisEventType

```c
enum InputEvent_AxisEventType
```

**Description**

Event type of the input device.

**Since**: 12

| Enum| Description|
| -- | -- |
| AXIS_EVENT_TYPE_PINCH = 1 | Two-finger pinch event. The value can be **AXIS_TYPE_PINCH** or **AXIS_TYPE_ROTATE**, both of which are of the [InputEvent_AxisType](#inputevent_axistype) type.|
| AXIS_EVENT_TYPE_SCROLL = 2 | Scroll event. The value can be **AXIS_TYPE_SCROLL_VERTICAL** or **AXIS_TYPE_SCROLL_HORIZONTAL**, both of which are of the [InputEvent_AxisType](#inputevent_axistype) type. For a mouse wheel event, only **AXIS_TYPE_SCROLL_VERTICAL** is supported.|

### InputEvent_AxisAction

```c
enum InputEvent_AxisAction
```

**Description**

Action of the input device.

**Since**: 12

| Enum| Description|
| -- | -- |
| AXIS_ACTION_CANCEL = 0 | The axis event is canceled.|
| AXIS_ACTION_BEGIN = 1 | The axis event begins.|
| AXIS_ACTION_UPDATE = 2 | The axis event is updated.|
| AXIS_ACTION_END = 3 | The axis event ends.|