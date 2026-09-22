# oh_axis_type.h

## Overview

**Include**: <multimodalinput/oh_axis_type.h>

**Library**: libohinput.so

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

**Related module**: [input](capi-input.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [InputEvent_AxisType](#inputevent_axistype) | InputEvent_AxisType | Defines the axis type of an input device. |
| [InputEvent_AxisEventType](#inputevent_axiseventtype) | InputEvent_AxisEventType | Event type of the input device. |
| [InputEvent_AxisAction](#inputevent_axisaction) | InputEvent_AxisAction | Action of the input device. |

## Enum type description

### InputEvent_AxisType

```c
enum InputEvent_AxisType
```

**Description**

Defines the axis type of an input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AXIS_TYPE_UNKNOWN = 0 | Unknown axis type, which is usually used as the initial value.<br>**Since**: 12 |
| AXIS_TYPE_SCROLL_VERTICAL = 1 | Vertical scroll axis. When you scroll the mouse wheel or slide with one or two fingers on the touchpad, the status of the vertical scroll axis changes.<br>**Since**: 12 |
| AXIS_TYPE_SCROLL_HORIZONTAL = 2 | Horizontal scroll axis. When you scroll the mouse wheel or slide with two fingers on the touchpad, the status of the horizontal scroll axis changes.<br>**Since**: 12 |
| AXIS_TYPE_PINCH = 3 | Pinch axis, which is used to describe a two-finger pinch gesture on the touchpad.<br>**Since**: 12 |
| AXIS_TYPE_ROTATE = 4 | Rotation axis, which is used to describe a two-finger rotation gesture on the touchpad.<br>**Since**: 12 |

### InputEvent_AxisEventType

```c
enum InputEvent_AxisEventType
```

**Description**

Event type of the input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AXIS_EVENT_TYPE_PINCH = 1 | Two-finger pinch event. The value can be **AXIS_TYPE_PINCH** or **AXIS_TYPE_ROTATE**, both of which are of the [InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype) type.<br>**Since**: 12 |
| AXIS_EVENT_TYPE_SCROLL = 2 | Scroll event. The value can be **AXIS_TYPE_SCROLL_VERTICAL** or **AXIS_TYPE_SCROLL_HORIZONTAL**, both of which are of the [InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype) type. For a mouse wheel event, only **AXIS_TYPE_SCROLL_VERTICAL**<br>is supported.<br>**Since**: 12 |

### InputEvent_AxisAction

```c
enum InputEvent_AxisAction
```

**Description**

Action of the input device.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 12

| Enum item | Description |
| -- | -- |
| AXIS_ACTION_CANCEL = 0 | The axis event is canceled.<br>**Since**: 12 |
| AXIS_ACTION_BEGIN = 1 | The axis event begins.<br>**Since**: 12 |
| AXIS_ACTION_UPDATE = 2 | The axis event is updated.<br>**Since**: 12 |
| AXIS_ACTION_END = 3 | The axis event ends.<br>**Since**: 12 |


