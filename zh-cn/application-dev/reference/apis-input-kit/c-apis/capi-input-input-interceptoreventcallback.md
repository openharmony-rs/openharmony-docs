# Input_InterceptorEventCallback

```c
typedef struct Input_InterceptorEventCallback {...} Input_InterceptorEventCallback
```

## 概述

Defines the structure for the interceptor of event callbacks,including mouseCallback, touchCallback, and axisCallback.

**起始版本：** 12

**相关模块：** [input](capi-input.md)

**所在头文件：** [oh_input_manager.h](capi-oh-input-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Input_MouseEventCallback](capi-oh-input-manager-h.md#input_mouseeventcallback) mouseCallback | Defines a lifecycle callback for **mouseEvent**. |
| [Input_TouchEventCallback](capi-oh-input-manager-h.md#input_toucheventcallback) touchCallback | Defines a lifecycle callback for **touchEvent**. |
| [Input_AxisEventCallback](capi-oh-input-manager-h.md#input_axiseventcallback) axisCallback | Defines a lifecycle callback for **axisEvent**. |


