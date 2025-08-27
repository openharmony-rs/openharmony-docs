# oh_axis_type.h

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->

## 概述

输入设备的轴事件结构和枚举。

**引用文件：** <multimodalinput/oh_axis_type.h>

**库：** libohinput.so

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

```
enum InputEvent_AxisType
```

**描述**

输入设备的轴类型。

**起始版本：** 12

| 枚举项 | 描述             |
| -- |----------------|
| AXIS_TYPE_UNKNOWN | 未知轴类型，通常作为初始值。 |
| AXIS_TYPE_SCROLL_VERTICAL | 垂直滚动轴，当您滚动鼠标滚轮或在触摸板上进行单指或双指滑动时，垂直滚动轴的状态改变。               |
| AXIS_TYPE_SCROLL_HORIZONTAL | 水平滚动轴，当您滚动鼠标滚轮或在触摸板上进行双指滑动时，水平滚动轴的状态发生变化。               |
| AXIS_TYPE_PINCH | 捏合轴，用于描述触摸板上的双指捏合手势。               |
| AXIS_TYPE_ROTATE | 旋转轴，用于描述触摸板上的双指旋转手势。               |

### InputEvent_AxisEventType

```
enum InputEvent_AxisEventType
```

**描述**

输入设备的轴事件类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AXIS_EVENT_TYPE_PINCH = 1 | 双指捏合事件，包含AXIS_TYPE_PINCH和AXIS_TYPE_ROTATE两种轴类型。		<br>**起始版本：** 12。 |
| AXIS_EVENT_TYPE_SCROLL = 2 | 滚轴事件，包含AXIS_TYPE_SCROLL_VERTICAL和AXIS_TYPE_SCROLL_HORIZONTAL两种轴类型，其中鼠标滚轮事件仅包含AXIS_TYPE_SCROLL_VERTICAL一种轴类型。		<br>**起始版本：** 12。 |

### InputEvent_AxisAction

```
enum InputEvent_AxisAction
```

**描述**

轴事件动作。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| AXIS_ACTION_CANCEL = 0 | 取消轴输入事件。 |
| AXIS_ACTION_BEGIN | 开始轴输入事件。 |
| AXIS_ACTION_UPDATE | 轴输入事件中。 |
| AXIS_ACTION_END | 结束轴输入事件。 |


