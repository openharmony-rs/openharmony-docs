# Input_InterceptorEventCallback

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct Input_InterceptorEventCallback {...} Input_InterceptorEventCallback
```

## 概述

拦截回调事件结构体，用于定义输入事件拦截所需的回调函数类型，支持拦截鼠标事件、触屏输入事件、按键事件和轴事件。

**起始版本：** 12

**相关模块：** [input](capi-input.md)

**所在头文件：** [oh_input_manager.h](capi-oh-input-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Input_MouseEventCallback](#input_mouseeventcallback) mouseCallback | 鼠标事件的回调函数。 |
| [Input_TouchEventCallback](#input_toucheventcallback) touchCallback | 触屏输入事件的回调函数。 |
| [Input_AxisEventCallback](#input_axiseventcallback) axisCallback | 轴事件的回调函数。 |


### 成员函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*Input_MouseEventCallback)(const Input_MouseEvent* mouseEvent)](#input_mouseeventcallback) | Input_MouseEventCallback() | 鼠标事件的回调函数，mouseEvent的生命周期为回调函数内。 |
| [typedef void (\*Input_TouchEventCallback)(const Input_TouchEvent* touchEvent)](#input_toucheventcallback) | Input_TouchEventCallback() | 触屏输入事件的回调函数，touchEvent的生命周期为回调函数内。 |
| [typedef void (\*Input_AxisEventCallback)(const Input_AxisEvent* axisEvent)](#input_axiseventcallback) | Input_AxisEventCallback() | 轴事件的回调函数，axisEvent的生命周期为回调函数内。 |

## 成员函数说明

### Input_MouseEventCallback()

```c
typedef void (*Input_MouseEventCallback)(const Input_MouseEvent* mouseEvent)
```

**描述**

鼠标事件的回调函数，mouseEvent的生命周期为回调函数内。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Input_MouseEvent](capi-input-input-mouseevent.md)* mouseEvent | 鼠标事件对象。 |

### Input_TouchEventCallback()

```c
typedef void (*Input_TouchEventCallback)(const Input_TouchEvent* touchEvent)
```

**描述**

触屏输入事件的回调函数，touchEvent的生命周期为回调函数内。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Input_TouchEvent](capi-input-input-touchevent.md)* touchEvent | 触屏输入事件对象。 |

### Input_AxisEventCallback()

```c
typedef void (*Input_AxisEventCallback)(const Input_AxisEvent* axisEvent)
```

**描述**

轴事件的回调函数，axisEvent的生命周期为回调函数内。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [Input_AxisEvent](capi-input-input-axisevent.md)* axisEvent | 轴事件对象。 |
