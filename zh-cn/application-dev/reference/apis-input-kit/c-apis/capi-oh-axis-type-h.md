# oh_axis_type.h

## 概述

Defines the device axis event struct and enumerates device axis events. The axis type defines the physicalbehavior characteristics of an input device in different interaction scenarios. The system uses the axis type todistinguish and transmit different gesture interaction information.

**库：** liboh_input.so

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**起始版本：** 12

**相关模块：** [input](capi-input.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [InputEvent_AxisType](#inputevent_axistype) | InputEvent_AxisType | 输入设备的轴类型。 |
| [InputEvent_AxisEventType](#inputevent_axiseventtype) | InputEvent_AxisEventType | 输入设备的轴事件类型。 |
| [InputEvent_AxisAction](#inputevent_axisaction) | InputEvent_AxisAction | 轴事件动作。 |

## 枚举类型说明

### InputEvent_AxisType

```c
enum InputEvent_AxisType
```

**描述**

输入设备的轴类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AXIS_TYPE_UNKNOWN |  |
| AXIS_TYPE_SCROLL_VERTICAL |  |
| AXIS_TYPE_SCROLL_HORIZONTAL |  |
| AXIS_TYPE_PINCH |  |
| AXIS_TYPE_ROTATE |  |

### InputEvent_AxisEventType

```c
enum InputEvent_AxisEventType
```

**描述**

输入设备的轴事件类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AXIS_EVENT_TYPE_PINCH = 1 | 双指捏合事件，包含AXIS_TYPE_PINCH和AXIS_TYPE_ROTATE两种[InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype)。<br>**起始版本：** 12 |
| AXIS_EVENT_TYPE_SCROLL = 2 | 滚轴事件，包含AXIS_TYPE_SCROLL_VERTICAL和AXIS_TYPE_SCROLL_HORIZONTAL两种[InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype)，其中鼠标滚轮事件仅包含AXIS_TYPE_SCROLL_VERTICAL一种[InputEvent_AxisType](capi-oh-axis-type-h.md#inputevent_axistype)。<br>**起始版本：** 12 |

### InputEvent_AxisAction

```c
enum InputEvent_AxisAction
```

**描述**

轴事件动作。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AXIS_ACTION_CANCEL = 0 |  |
| AXIS_ACTION_BEGIN |  |
| AXIS_ACTION_UPDATE |  |
| AXIS_ACTION_END |  |


